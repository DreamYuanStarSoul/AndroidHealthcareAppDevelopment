##Remove the default ActionBar

Replace ActionBar with ToolBar, as ActionBar may cause inconsistency in different versions, by changing style
```
 <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
 
 //Or add
 
 <item name="android:windowActionBar">false</item>
```

