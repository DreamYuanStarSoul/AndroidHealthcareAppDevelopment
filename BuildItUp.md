#First - Simple UI

##Add a new text field
```
<EditText android:id="@+id/edit_message"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:hint="@string/edit_message" /> //Error, as it is not yet defined
```
id indicates the reference/name of this element, need "+" when we create it. Hint is the default message that will actually be displayed.

"warp_content" means the element will only occupy the space that it needs
"match_parent" occupies the entire interface


##Define strings in res/values/stings
```
<resources>
    <string name="app_name">MainApp</string>
    <string name="action_settings">Settings</string>
    <string name="edit_message">Enter a Message</string>
    <string name="button_send">Send</string>
</resources>
```
Externalize all the string is definitely a brilliant idea! In case of localization, we only need this single file to do the translation. I should apply this tactic in other complicated programs, too.

##Call method by clicking button

```
<Button android:onClick="sendMessage"/>

...

public void sendMessage(View view) {
    Intent intent = new Intent(this, DisplayMessageActivity.class);  //Explain in the next section
    EditText editText = (EditText) findViewById(R.id.edit_message);
    String message = editText.getText().toString();
    intent.putExtra(EXTRA_MESSAGE, message);
    startActivity(intent);
}
```
Method requirements:

1. Be public;
2. Have a void return value;
3. Have a View as the only parameter (this will be the View that was clicked);

##Create an Intent

```
Intent intent = new Intent(this, DisplayMessageActivity.class);
```
1. A Context, Activity class is a subclass of Context;
2. The *Class* of the activity which receives the Intent (which the Intent intends to send to).

Find and reach a view:
```
EditText editText = (EditText) findViewById(R.id.edit_message);
String message = editText.getText().toString();
```

An Intent can carry data types as key-value pairs called extras (Key:EXTRA_MESSAGE, Value:message):
```
public final static String EXTRA_MESSAGE = "com.mycompany.myfirstapp.MESSAGE";
...
intent.putExtra(EXTRA_MESSAGE, message);
startActivity(intent);
```
The system receives this call and starts an instance of the Activity specified by the Intent


##Create a secondary activity

Each activity has "onCreate() method", where the activity receives and renders intent. And "setContentView()" is where it performs initial setup of components. 

```
Intent intent = getIntent();
String message = intent.getStringExtra(MyActivity.EXTRA_MESSAGE);
TextView textView = new TextView(this);
textView.setTextSize(40);
textView.setText(message);
RelativeLayout layout = (RelativeLayout) findViewById(R.id.content);
layout.addView(textView);
```
We extract the message and put it into a textView, which we put into the layout. 
