##View Basic

We can generally assume that each view is a unit on our interface, such as a button, a text window. I personally suggest we initialize and modify views through Java code, especially those views that will constantly change in response to user behaviors.


When you wanna modify a view in Java, you have to get it from res file
```
// In activity
TextView prediction = (TextView) findViewById(R.id.prediction_text);
         prediction.setText("");
         
// If not in activity, get activity first
TextView prediction = (TextView) getActivity().findViewById(R.id.prediction_text);
```

To intialize an image button, we could:
```
private ImageButton buttonPrediction;
buttonPrediction = (ImageButton) findViewById(R.id.procare_button_prediction);
buttonPrediction.setOnClickListener(this);
((ImageButton) buttonPrediction).setImageResource(R.drawable.monitor);
buttonPrediction.setScaleType(ImageView.ScaleType.FIT_CENTER);
```


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
Add this line to leave a moderate margin between all modules.
```
android:useDefaultMargins="true"
```

