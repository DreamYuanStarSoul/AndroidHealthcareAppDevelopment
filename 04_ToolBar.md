##1. Remove the default ActionBar

Replace ActionBar with ToolBar, as ActionBar may cause inconsistency in different versions, by changing style (there are two style files!)
```
 <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
 
 //Alternatives that didn't work in my case:
 //Add
 <item name="android:windowActionBar">false</item>
 
```

##2. Prerequisites

1. Add the v7 appcompat support library
2. Make sure the activity extends AppCompatActivity
3. 
