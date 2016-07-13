First, we need to download and install JDK. Well, we haven't been done this for a long time. The only thing that we might forget is to set up environment variables. We need to set the path of JDK as a new environment variable "JAVA_HOME":
```
C:\Program Files\Java\jdk1.8.0_91
```

Then we edit the "PATH" variable and add at the end:
```
;%JAVA_HOME%\bin
```
Open your cmd window (a new one if you have already opened one), enter "java -version" and "javac -version" to check whether your setup is successful.


Second, we install Andriod Studio. I encountered a problem after I turned on the VT-x in BIOS, which is needed to launch a emulator. I can't create a new project and the welcome page I saw is weird and different from all the tutorials. Simply uninstall and reinstall didn't work, so I *manually delete* all Andriod files under User folder and reinstalled. I think I accidently remove some kind of settings or path. 

After I created the project, this package "import android.support" and also "junit" have been highlighted with red, indicating it's not properly applied. To resolve this issue, we comment out the junit line in "build.gradle". My programs are free from this compiler error after I did so. 
```
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    //testCompile 'junit:junit:4.12'
    compile 'com.android.support:appcompat-v7:23.4.0'
    compile 'com.android.support:design:23.4.0'
}
```
