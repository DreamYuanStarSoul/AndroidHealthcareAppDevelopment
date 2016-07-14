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
##onStart()
onCreate() and onStart() are ephemeral, the activity will stay in onResume() (running) status afterwars.

##onDestroy()
Usually not needed, as activity will perform cleanup during onPause() and onStop(). But for long-running resources and threads, we destroty the activity.
```
@Override
public void onDestroy() {
    super.onDestroy();  // Always call the superclass
    
    // Stop method tracing that the activity started during onCreate()
    android.os.Debug.stopMethodTracing();
}
```

##onResume()


##onPause()



##onStop()
