##Print log?
Use println() instead of print()

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

##GridLayout

1. GridLayout is in use only after Android 4.0, API Level = 14. Lower versions will need additional support packages
2. Column and row start from 0 and end at n-1
3. Use "android:layout_width="0dp" to make elements have no-zero heights
4. Excessive length of string may cause unevenness in alignment

My evenly distributed example with span and weight
```
<GridLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_below="@+id/homepage_status"
    android:rowCount="2"
    android:columnCount="3">

    <Button
        android:id="@+id/homepage_emergency_button"
        android:text="@string/homepage_emergent_call"
        android:onClick="goGeneral"
        android:layout_row="0"
        android:layout_rowSpan="2"
        android:layout_column="2"
        android:layout_gravity="fill"
        android:layout_columnWeight="1"/>

    <Button
        android:id="@+id/homepage_button_general_fit"
        android:layout_width="wrap_content"
        android:text="@string/homepage_general_fit"
        android:layout_row="0"
        android:layout_column="0"
        android:layout_gravity="fill"
        android:layout_rowWeight="1"
        android:layout_columnWeight="1" />

    <Button
        android:id="@+id/homepage_button_professional_care"
        android:text="@string/homepage_professional_care"
        android:layout_row="1"
        android:layout_column="0"
        android:layout_gravity="fill"
        android:layout_rowWeight="1" />

    <Button
        android:text="1"
        android:layout_row="0"
        android:layout_column="1"
        android:layout_gravity="fill"
        android:layout_columnWeight="1"/>

    <Button
        android:id="@+id/homepage_button_system"
        android:text="@string/homepage_system"
        android:layout_row="1"
        android:layout_column="1"
        android:layout_gravity="fill"
        />

</GridLayout>
```

##Insert special characters in string.xml
&#160    space 
\n       new line
\t       tab

