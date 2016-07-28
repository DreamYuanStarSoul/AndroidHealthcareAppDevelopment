## Gradient background
We can change the color, shape, cornor angles, and border for button, textview, and more. Create a drawable file contains:
```
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <gradient android:startColor="@color/transparent100"
        android:centerColor="@color/primaryLight"
        android:endColor="@color/transparent100"></gradient>
</shape>
```
Go back to xml, change the background to drawable:
```
android:background="@drawable/background_clock"
```


## Basic image button
```
buttonSleep = (ImageButton) findViewById(R.id.general_button_sleep);
buttonSleep.setOnClickListener(this);

((ImageButton) buttonSleep).setImageResource(R.drawable.sleep);   // Add a symbol
buttonSleep.setScaleType(ImageView.ScaleType.FIT_CENTER);
buttonStepCount.setBackgroundColor(normal);  // Change the background
```

## On click effect

Change and restore button UI when clicked.

Color:
```
if (chosen)
    button.setBackgroundColor(clicked);

private void restoreColor() {
for (ImageButton ib : buttonList) 
    ib.setBackgroundColor(normal);
}
```
Drawable:
```
Drawable mDrawable = getResources().getDrawable(R.drawable.background);
textView.setBackground(mDrawable);
```

## Large Image
Simply copy and paste them into drawable folder, then invoke them.
