

##Simply build your .apk under build -> build apk

you will find the generated .apk file under
```
MyApplication\app\build\outputs\apk
```


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
