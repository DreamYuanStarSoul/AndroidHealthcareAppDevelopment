
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
