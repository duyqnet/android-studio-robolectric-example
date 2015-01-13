![build status](https://travis-ci.org/mutexkid/android-studio-robolectric-example.svg)

## Android Studio Robolectric Test Example
--- 
This example project shows how to use robolectric, junit and fest with gradle-based Android Studio projects (as of Android Studio 0.8.1). Examine the top-level build.gradle and app/build.gradle files for a new project configuration gradle boilerplate. 

Uses :

- [Android Unit Test](https://github.com/JCAndKSolutions/android-unit-test)  
- [Android Studio Unit Test](https://github.com/evant/android-studio-unit-test-plugin) 

Both will need to be installed (see instructions below).

### To set up from a new Android Studio Project: 

your top-level build.gradle file should look like this: 

```javascript
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:1.0.0'
    	classpath 'com.github.jcandksolutions.gradle:android-unit-test:2.1.1'
    }
}


allprojects {
    repositories {
        jcenter()
    }
}
```

your app/build.gradle file should look like this: 

```javascript
apply plugin: 'com.android.application'

android {
    compileSdkVersion 21
    buildToolsVersion '21.1.2'

    defaultConfig {
        applicationId "com.example.joshskeen.myapplication"
        minSdkVersion 14
        targetSdkVersion 21
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

apply plugin: 'android-unit-test'

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    testCompile 'org.easytesting:fest:1.0.16'
    testCompile 'junit:junit:4.+'
    testCompile 'org.robolectric:robolectric:2.3'
    testCompile 'com.squareup:fest-android:1.0.8'
}
```


2. Create directories matching src/test/java/ and add a package matching your project's packagename. eg src/test/java/com.example.joshskeen.myapplication
 <img src="https://www.evernote.com/shard/s313/sh/d69d9f94-76cb-42ac-858f-b6f7da68a6fb/f8d5f3ca3223094317d895c78cae5103/deep/0/TestMyActivity.java----app----android-studio-robolectric-example------code-foo-bar-android-studio-robolectric-example----Android-Studio-(Beta)-0.8.4.png" width="600">

1. Install [Android Studio Unit Test](https://github.com/evant/android-studio-unit-test-plugin) plugin to Android Studio under Preferences > Plugins.
 <img src="https://www.evernote.com/shard/s313/sh/fd96c364-d3f7-44bf-b47f-a92a120a2b31/05956583f739e98b5c3e40242bcae820/deep/0/Preferences-and-TestMyActivity.java----app----My-Application------AndroidStudioProjects-MyApplication----Android-Studio-(Beta)-0.8.1.png" width="600">


3. You may need to restart Android Studio to allow the android studio unit test plugin to see src/test as a test directory.

4. click 'Sync Project with Gradle Files'
 <img src="https://www.evernote.com/shard/s313/sh/75d04b22-0ef0-449e-b137-e65dd4948865/28376be9739b21ca941d8fb6a4eeda88/deep/0/README.md----MyApplication----My-Application------AndroidStudioProjects-MyApplication----Android-Studio-(Beta)-0.8.1.png" width="600">

4. Write Robolectric Tests! For more intel on how to write tests using robolectric + fest, check out [http://blog.bignerdranch.com/2583-testing-the-android-way/](http://blog.bignerdranch.com/2583-testing-the-android-way/)


