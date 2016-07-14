#Activity
##Launcher Activity
Add these to one of the activity and make it the launcher activity.
```
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
```

##onCreate()
```
public void onCreate(Bundle savedInstanceState) {
    // Always call the super, same for other onXX() methods
    super.onCreate(savedInstanceState);

    // Set the user interface layout for this Activity
    // The layout file is defined in the project res/layout/main_activity.xml file
    setContentView(R.layout.main_activity);
    
    // Initialize member TextView so we can manipulate it later
    mTextView = (TextView) findViewById(R.id.text_message);
    
    // Make sure we're running on Honeycomb or higher to use ActionBar APIs
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.HONEYCOMB) {
        // For the main activity, make sure the app icon in the action bar
        // does not behave as a button
        ActionBar actionBar = getActionBar();
        actionBar.setHomeButtonEnabled(false);
    }
}
```


##onResume()


##onPause()


##onStop()
```
@Override
protected void onStop() {
    super.onStop();  // Always call the superclass method first

    // Save the note's current draft, because the activity is stopping
    // and we want to be sure the current note progress isn't lost.
    ContentValues values = new ContentValues();
    values.put(NotePad.Notes.COLUMN_NAME_NOTE, getCurrentNoteText());
    values.put(NotePad.Notes.COLUMN_NAME_TITLE, getCurrentNoteTitle());

    getContentResolver().update(
            mUri,    // The URI for the note to update.
            values,  // The map of column names and new values to apply to them.
            null,    // No SELECT criteria are used.
            null     // No WHERE columns are used.
            );
}
```
##onStart() / onRestart()
onCreate() and onStart() are ephemeral, the activity will stay in onResume() (running) status afterwars.

```
@Override
protected void onStart() {
    super.onStart();  // Always call the superclass method first
    
    // The activity is either being restarted or started for the first time
    // so this is where we should make sure that GPS is enabled
    LocationManager locationManager = 
            (LocationManager) getSystemService(Context.LOCATION_SERVICE);
    boolean gpsEnabled = locationManager.isProviderEnabled(LocationManager.GPS_PROVIDER);
    
    if (!gpsEnabled) {
        // Create a dialog here that requests the user to enable GPS, and use an intent
        // with the android.provider.Settings.ACTION_LOCATION_SOURCE_SETTINGS action
        // to take the user to the Settings screen to enable GPS when they click "OK"
    }
}

@Override
protected void onRestart() {
    super.onRestart();  // Always call the superclass method first
    
    // Activity being restarted from stopped state    
}
```

##onDestroy()
Usually not needed, as activity will perform cleanup during onPause() and onStop(). But for long-running resources and threads, we destroty the activity. 

#####finish() - transfer page
The system calls onDestroy() after it has already called onPause() and onStop() in all situations except one: when you call finish() from within the onCreate() method. In some cases, such as when your activity operates as a temporary decision maker to launch another activity, you might call finish() from within onCreate() to destroy the activity. In this case, the system immediately calls onDestroy() without calling any of the other lifecycle methods.

```
@Override
public void onDestroy() {
    super.onDestroy();  // Always call the superclass
    
    // Stop method tracing that the activity started during onCreate()
    android.os.Debug.stopMethodTracing();
}
```
##Recreating an activity

If activity was destroyed due to "back" function or suicide "finish()", it's gone permanently. However, if it has been destroyed by system due to not enough resources, its state will be preserved by system through "onSaveInstanceState()". The states includes all the views which have an unique ID. Override the method to preserve additional information.
```
static final String STATE_SCORE = "playerScore";
static final String STATE_LEVEL = "playerLevel";
...

@Override
public void onSaveInstanceState(Bundle savedInstanceState) {
    // Save the user's current game state
    savedInstanceState.putInt(STATE_SCORE, mCurrentScore);
    savedInstanceState.putInt(STATE_LEVEL, mCurrentLevel);
    
    // Always call the superclass so it can save the view hierarchy state
    super.onSaveInstanceState(savedInstanceState);
}
```

