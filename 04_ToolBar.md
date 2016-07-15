##1. Remove the default ActionBar

Replace ActionBar with Toolbar, as ActionBar may cause inconsistency in different versions, by changing style (there are two style files!)
```
 <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
 
 //Alternatives that didn't work in my case:
 //Add
 <item name="android:windowActionBar">false</item>
 
```

##2. Prerequisites

1. Add the v7 appcompat support library
2. Make sure the activity extends AppCompatActivity

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
