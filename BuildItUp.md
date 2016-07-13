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

/** Called when the user clicks the Send button */
    public void sendMessage(View view) {
        // Do something in response to button
    }
```
Method requirements:

1. Be public;
2. Have a void return value;
3. Have a View as the only parameter (this will be the View that was clicked);
