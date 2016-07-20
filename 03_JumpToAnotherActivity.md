#Simple UI manipulation

##Create a view
```
//Add a new text field in .xml
<EditText android:id="@+id/button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:hint="@string/button" /> 
    
//Define strings in res/values/stings in .xml
<resources>
    <string name="button_send">Send</string>
</resources>
```
id indicates the reference/name of this element, hint is the default message that will actually be displayed.

"warp_content": only occupy the space needed
"match_parent": extends to the entire page

Externalize all the string is definitely a brilliant idea! In case of localization, we only need this single file to do the translation. I should apply this tactic in other complicated programs, too.


##Send the message to another activity when button clicked

We create a Java method to do this, the requirements are:

1. Be public;
2. Have a void return value;
3. Have a View as the only parameter (this will be the View that was clicked);
```
//In main activity xml, invoke "sendMessage" method when button clicked:
<Button android:onClick="sendMessage"/>

//In its Java, create the method:
public void sendMessage(View view) {
    Intent intent = new Intent(this, DisplayMessageActivity.class);  //Explain in the next section
    EditText editText = (EditText) findViewById(R.id.edit_message);
    String message = editText.getText().toString();
    intent.putExtra(EXTRA_MESSAGE, message);
    startActivity(intent);
}
```

#####Explanantion
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
Step 4: Create a secondary activity (activity_display_message) to display the message
Each activity has "onCreate() method", where the activity receives and renders intent. And "setContentView()" is where it performs initial setup of components. 
```
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_display_message);

        // Get the intent of this activity and extract the message from it
        Intent intent = getIntent();
        String message = intent.getStringExtra(HomeActivity.EXTRA_MESSAGE);
        TextView textView = new TextView(this);
        textView.setTextSize(40);
        textView.setText(message);
        RelativeLayout layout = (RelativeLayout) findViewById(R.id.content);
        layout.addView(textView);
    }
```
Now, we can extract the message from the intent and put it into a textView, which we put into the layout. 

##Simply jump to another activity?

This one we will also use a lot:
```
if (success) { 
    finish(); // End current activity
    Intent intent = new Intent(LoginActivity.this, MyActivity.class); // Create an intent
    startActivity(intent); // Launch it
```

#Done :D
