#Caution!
Be very aware about the consistency of packages. For example, Fragment and FragmentManager are included in both android.app package and android.support package. You wanna make sure that you are using the same package for these two classes, otherwise you will get an error for you don't know why, such as in the following code.
```
transaction.add(R.id.id_content, fragmentStepCount);
transaction.show(fragmentStepCount);
```


##Create a XML file named "fragment_step_count" 
```
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="layout.FragmentStepCount">

    <!-- TODO: Update blank fragment layout -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="@string/hello_blank_fragment" />

    <ImageButton
        android:id="@+id/imageButton"
        android:layout_width="73dp"
        android:layout_height="61dp"
        android:layout_gravity="center_horizontal|bottom" />

</FrameLayout>
```

##Create a Java controller
```
public class FragmentStepCount extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_step_count, container, false);
    }
}
```

##Embed the fragment xml into the main activity xml
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/general"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <fragment android:name="layout.FragmentStepCount"
        android:id="@+id/fragment_step_count"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</RelativeLayout>
```

##Put the fragment into your activity
```
public class GeneralActivity extends AppCompatActivity  {
//implements View.OnClickListener
    private FragmentStepCount fragmentStepCount;
    private LinearLayout layoutStepCount;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.fragment_step_count);

        layoutStepCount = (LinearLayout) findViewById(R.id.fragment_step_count);
    }

    private void setTabSelection(int index) {
        // Manager and Transaction are needed
        FragmentManager fm = getFragmentManager();
        FragmentTransaction transaction = fm.beginTransaction();
       
        if (fragmentStepCount == null) {
            fragmentStepCount = new FragmentStepCount();
            transaction.add(R.id.id_content, fragmentStepCount);
        }
        else {
            transaction.show(fragmentStepCount); // Hidden before
        }
        
        transaction.commit();
    }
}
```

(https://guides.codepath.com/android/Creating-and-Using-Fragments)

(http://stackoverflow.com/questions/15109017/difference-between-android-app-fragment-and-android-support-v4-app-fragment)

(http://blog.csdn.net/lmj623565791/article/details/24740977)

(http://blog.csdn.net/lmj623565791/article/details/37970961)
