##Put activities into Menifest as you create them!

##Print log?
Use println() instead of print()

##Best approach for clicking buttons

Create an individual listener for each button
```
private ImageButton buttonHeartbeat;
private ImageButton buttonStepCount;

buttonHeartbeat = (ImageButton) findViewById(R.id.general_button_heartbeat);
buttonStepCount = (ImageButton) findViewById(R.id.general_button_step_count);

buttonHeartbeat.setOnClickListener(this);
buttonStepCount.setOnClickListener(this);

public void onClick(View v) {
    if (v.getId() == R.id.general_button_step_count) {
        selectTab(0);
    }
    else if (v.getId() == R.id.general_button_heartbeat) {
        selectTab(1);
    }
}
```


##UserLoginTask
```
public class UserLoginTask extends AsyncTask<Void, Void, Boolean> {}

private UserLoginTask mAuthTask = null;
mAuthTask = new UserLoginTask(email, password); // The verification process
mAuthTask.execute((Void) null); // What happen next: jump to another page, hint an error, or close the program
```
execute() include four stages of methods, onPreExecute(),doInBackground(Params...), onProgressUpdate(Progress...), and onPostExecute(Result). Usually, we need to override at least doInBackground(), and in most cases onPostExecute()
(https://developer.android.com/reference/android/os/AsyncTask.html)


##Insert image to drawable

1. Right click on res, new Image Asset
2. On Asset type choose Action Bar and Tab Icons
3. Choose the image path
4. Give your image a name in Resource name
5. Next->Finish

The image will be saved in the /res/drawable folder!
(http://stackoverflow.com/questions/29047902/how-to-add-an-image-to-the-drawable-folder-in-android-studio)

##Depreciated usage and update:
fill_parent --> march_parent



##Insert special characters in string.xml
\u0020    space

\n        new line

\t        tab

##EditText

Use 
```
android:maxLines="1"
```
instead of 
```
singleLine="true"
```
which has been depreciated

##TextView
To clear: view.setText("");


##Phone call function

Use "ACTION_DIAL" to call for the dial panel, use "ACTION_CALL" to call directly, which needs additional permission. 

This problem is complicated and there are many different ways to resolve it. Here we have three different approaches. If you are lucky, try to run your program on a real device, and the problem may fix by itself.  

*You have to use a string starts with "tel:" and followed by only digits.
```
emergentCallButton =  (Button) findViewById(R.id.homepage_button_emergent_call);
emergentCallButton.setOnClickListener(new View.OnClickListener() {
```
Approach 1:
```
String emergentNumber = "119";
@Override
public void onClick(View view) {
    Intent callIntent = new Intent(Intent.ACTION_CALL);
    callIntent.setData(Uri.parse("tel:" + emergentNumber));
    if (callIntent.resolveActivity(getPackageManager()) != null) {
        startActivity(callIntent);
    }
}
```
Approach 2:
```
public void onClick(View view) {
    Intent callIntent = new Intent(Intent.ACTION_CALL);
    callIntent.setData(Uri.parse("tel:" + emergentNumber));
    try {
        startActivity(callIntent);
    catch (SecurityException e) {
    //...
    }
}
```
Approach 3:
```
public void onClick(View view) {
    Intent callIntent = new Intent(Intent.ACTION_CALL);
    callIntent.setData(Uri.parse("tel:" + emergentNumber));
    callIntent.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK);   // add this line
    try {
        startActivity(callIntent);
    catch (SecurityException e) {
    //...
    }
}
```

Add permission in Menifast
```
<uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
```
