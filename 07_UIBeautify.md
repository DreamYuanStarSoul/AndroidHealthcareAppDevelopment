## Gradient background
Create a drawable file contains:
```
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <gradient android:startColor="@color/transparent100"
        android:centerColor="@color/primaryLight"
        android:endColor="@color/transparent100"></gradient>
</shape>
```

We can also change the shape, cornor angles, and border in "shape". Go back to xml, change the background to drawable:
```
android:background="@drawable/background_clock"
```
