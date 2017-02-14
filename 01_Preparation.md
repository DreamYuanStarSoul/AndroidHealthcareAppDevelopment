#First - Install JDK
Well, we haven't been done this for a long time. The only thing that we might forget is to set up environment variables. We need to set the path of JDK as a new environment variable "JAVA_HOME":
```
C:\Program Files\Java\jdk1.8.0_91
```

Then we edit the "PATH" variable and add at the end:
```
;%JAVA_HOME%\bin
```
Open your cmd window (a new one if you have already opened one), enter "java -version" and "javac -version" to check whether your setup is successful.


#Second - Install Android Studio

I follow the tutorial here:
https://developer.android.com/training/basics/firstapp/index.html

## Problem 1 - Can't create a normal new project
I encountered a problem after I turned on the VT-x in BIOS, which is needed to launch a emulator. I can't create a new project and the welcome page I saw is weird and different from all the tutorials. Simply uninstall and reinstall didn't work, so I *manually delete* all Andriod files under User folder and reinstalled. I think I accidently remove some kind of settings or path. 

## Problem 2 - Program does not compile
After I created the project, this package "import android.support" and also "junit" have been highlighted with red, indicating it's not properly applied. To resolve this issue, we comment out the junit line in "build.gradle". My programs are free from this compiler error after I did so. 
```
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    //testCompile 'junit:junit:4.12'
    compile 'com.android.support:appcompat-v7:23.4.0'
    compile 'com.android.support:design:23.4.0'
}
```
Two alternatives to solve this issue, but they didn't work in my case, probably because of company proxy.

*1. Go to File -> Project Structure. Following window will open: remove the junit library (select junit and press "-" button below ) and add it again (select "+" button below, select "library dep.", search for "junit", press OK ). Press OK to apply changes. After around 30 seconds your gradle sync should work fine.*

*2. Add this part to "build.gradle":*
```
repositories {
    maven { url 'http://repo1.maven.org/maven2' }
}
```
(http://stackoverflow.com/questions/32519219/error23-17-failed-to-resolve-junitjunit4-12)

##Problem 3 - Launch the emulator

Well, there are a bunch of problems when I tried to launch my emulator.
##### 1. VM heap size is not enough
Tools-Android-ADV Manager-Edit-Advance, scroll down and you will see the size option. I entered 512MB and everything is ok.

##### 2. Could not get wglGetExtensionsStringARB
Use Host GPU. Tools-Android-ADV Manager-Edit-Advance, change "auto" to "software".
(http://stackoverflow.com/questions/11407501/android-emulator-could-not-get-wglgetextensionsstringarb-error)

There are some other minor issues, but they didn't prevent me from launching the VM, so, here we go.

## Problem 4 - Upgrade SDK version
Adjust:  
1. compileSdkVersion: The way to tell Gradle what version of the Android SDK to compile your app with. A new Android SDK is required to use any of the new APIs added in that level. Changing it does not change runtime behavior. Therefore it is strongly recommended that you always compile with the latest SDK;  
2. minSdkVersion: The lower bound for your app. The minSdkVersion is one of the signals used to determine which of a user’s devices an app can be installed on. When deciding on a minSdkVersion, you should consider the stats on the [Dashboards](https://developer.android.com/about/dashboards/index.html);  
3. targetSdkVersion: The main way Android provides forward compatibility by not applying behavior changes unless the targetSdkVersion is updated. Please test before updating your targetSdkVersion;  

Link: https://medium.com/google-developers/picking-your-compilesdkversion-minsdkversion-targetsdkversion-a098a0341ebd#.tz5zzucma
