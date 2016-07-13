Simple UI - Click a Button

##Add a new text field in .xml
```
<EditText android:id="@+id/edit_message"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:hint="@string/edit_message" /> //Error, as it is not yet defined
```
id indicates the reference/name of this element, need "+" when we create it. Hint is the default message that will actually be displayed.

"warp_content" means the element will only occupy the space that it needs
"match_parent" occupies the entire interface


##Define strings in res/values/stings in .xml
```
<resources>
    <string name="app_name">MainApp</string>
    <string name="action_settings">Settings</string>
    <string name="edit_message">Enter a Message</string>
    <string name="button_send">Send</string>
</resources>
```
Externalize all the string is definitely a brilliant idea! In case of localization, we only need this single file to do the translation. I should apply this tactic in other complicated programs, too.

##Send input message to a new interface by clicking a button
#####Call method
Method requirements:

1. Be public;
2. Have a void return value;
3. Have a View as the only parameter (this will be the View that was clicked);
```
//In xml, invoke "sendMessage" method when button clicked:
<Button android:onClick="sendMessage"/>

//In java, create the method:
public void sendMessage(View view) {
    Intent intent = new Intent(this, DisplayMessageActivity.class);  //Explain in the next section
    EditText editText = (EditText) findViewById(R.id.edit_message);
    String message = editText.getText().toString();
    intent.putExtra(EXTRA_MESSAGE, message);
    startActivity(intent);
}
```

#####Create an Intent
Step 1: Create an intent with its source activity (left) and target activity (right)
```
Intent intent = new Intent(this, DisplayMessageActivity.class);
```
Step 2: Find the view and reach its content
```
EditText editText = (EditText) findViewById(R.id.edit_message);
String message = editText.getText().toString();
```
Setp 3: Pass message to the Intent
Create a unique, public constant EXTRA_MESSAGE as key, pair it with input message as value, and then assign the key-value pair to putExtra(). The intent will thsu carry the input message. When the system receives the call, it starts an instance of the Activity specified by the Intent
```
public final static String EXTRA_MESSAGE = "com.mycompany.myfirstapp.MESSAGE"; // This could be anything, just a string

intent.putExtra(EXTRA_MESSAGE, message);
startActivity(intent);
```
Step 4: Create a secondary activity to display the message
Each activity has "onCreate() method", where the activity receives and renders intent. And "setContentView()" is where it performs initial setup of components. 
```
//In java - onCreate():
Intent intent = getIntent();
String message = intent.getStringExtra(MyActivity.EXTRA_MESSAGE);
TextView textView = new TextView(this);
textView.setTextSize(40);
textView.setText(message);
RelativeLayout layout = (RelativeLayout) findViewById(R.id.content);
layout.addView(textView);
```
We extract the message from the intent and put it into a textView, which we put into the layout. 

#Done :D
