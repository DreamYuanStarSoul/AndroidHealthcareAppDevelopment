##### If you download project sourse code from the Internet and try to run them, there might be something that you need to handle.


## SDK & build tool version

File -> Project Structure -> Module -> Choose the right version of SDK and build tool


##Change the grid files, examples:
APP:
```
android {
    compileSdkVersion 23
    buildToolsVersion "24.0.0"

    defaultConfig {
        applicationId "com.example.qq33991.mainapp"
        minSdkVersion 21
        targetSdkVersion 23
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }

    repositories {
        mavenCentral()
        jcenter {
            url "http://jcenter.bintray.com/"
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    //testCompile 'junit:junit:4.12'
    compile 'com.android.support:appcompat-v7:23.4.0'
    compile 'com.android.support:design:23.4.0'
    compile 'com.android.support:support-v4:23.4.0'
    compile 'com.google.android.gms:play-services:9.2.1'
}
```

Project:
```
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.1.2'
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

##Gradle version xxxx is required
1. In File-Setting-gradle, change the project-leveling settiong to auto
2. In project_root/gradle/wrapper/gradle-wrapper.properties, change the gradle version to the wanted one
```
distributionUrl=https\://services.gradle.org/distributions/gradle-2.10-all.zip
```
3. Also, change the gradle dependency version in project's build.gradle file
```
dependencies {
        classpath 'com.android.tools.build:gradle:2.1.2'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
```
