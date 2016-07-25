##1. Prerequisites

1. Add the v7 appcompat support library
2. Make sure ALL activities using toolbar extends AppCompatActivity

##2. Remove the default ActionBar

Replace ActionBar with Toolbar, as ActionBar may cause inconsistency in different versions, by changing style (there are two style files!)
```
 <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
 
 //Alternatives that didn't work in my case:
 //Add
 <item name="android:windowActionBar">false</item>
 
```

##3. Add Toolbar
In xml
```
<android.support.v7.widget.Toolbar
   android:id="@+id/my_toolbar"
   android:layout_width="match_parent"
   android:layout_height="?attr/actionBarSize"
   android:background="?attr/colorPrimary"
   android:elevation="4dp"
   android:theme="@style/ThemeOverlay.AppCompat.ActionBar"
   app:popupTheme="@style/ThemeOverlay.AppCompat.Light"/>
   ```
In Java
```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_my);
    Toolbar myToolbar = (Toolbar) findViewById(R.id.my_toolbar);
    setSupportActionBar(myToolbar);
    }
```

##4. To manipulate

To use the ActionBar utility methods, call the activity's getSupportActionBar() method. This method returns a reference to an appcompat ActionBar object. Once you have that reference, you can call any of the ActionBar methods to adjust the app bar. For example, to hide the app bar, call ActionBar.hide().

##5. Add action buttons
Create a new XML file under res/menu/
```
<menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <!-- "Mark Favorite", should appear as action button if possible -->
    <item
        android:id="@+id/action_favorite"
        android:icon="@drawable/ic_favorite_black_48dp"
        android:title="@string/action_favorite"
        app:showAsAction="ifRoom"/>

    <!-- Settings, should always be in the overflow -->
    <item android:id="@+id/action_settings"
          android:title="@string/action_settings"
          app:showAsAction="never"/>

</menu>
```

6. Response to actions

When the user selects one of the app bar items, the system calls your activity's onOptionsItemSelected() callback method, and passes a MenuItem object to indicate which item was clicked. In your implementation of onOptionsItemSelected(), call the MenuItem.getItemId() method to determine which item was pressed. 
```
@Override
public boolean onOptionsItemSelected(MenuItem item) {
    switch (item.getItemId()) {
        case R.id.action_settings:
            // User chose the "Settings" item, show the app settings UI...
            return true;

        case R.id.action_favorite:
            // User chose the "Favorite" action, mark the current item
            // as a favorite...
            return true;

        default:
            // If we got here, the user's action was not recognized.
            // Invoke the superclass to handle it.
            return super.onOptionsItemSelected(item);

    }
}
```
