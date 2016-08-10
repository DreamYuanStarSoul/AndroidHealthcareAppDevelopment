
##Name your app and give it an icon in Manifest

```
 <application android:theme="@style/AppTheme"
        android:label="@string/app_name"
        android:icon="@drawable/icon">
```

##Simply build your .apk under build -> build apk

you will find the generated .apk file under
```
MyApplication\app\build\outputs\apk
```

##Time is money

In Android Studio go to File -> Settings -> Build, Execution, Deployment -> Build Tools -> Gradle
Check the 'Offline work' under 'Global Gradle settings'
It will dramatically reduce the time used to build apk.



##Bugs

#####Unable to build apk: The number of method references cannot exceed 64K

Add this line to the module's build.gradle file
```
android {
    defaultConfig {
        //...
        multiDexEnabled true
    }
}
```


#####build.gradle uncaught translation error ExecutionException OutOfMemory

Add this line to app build
```
dexOptions {
    javaMaxHeapSize "4g"
}
```
