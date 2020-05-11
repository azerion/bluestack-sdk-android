# Madvertise Location SDK

[TOC]

MadvertiseLocation SDK is and android library. This SDK **works** with a **CMP** (CONSENT MANAGEMENT PROVIDERS) **only** for The **GDPR** (General Data Protection Regulation) rules. We have developed our [Madvertise CMP]

## Prerequisites

 - The latest versions of the Android SDK, [madvertiselocation-x.aar].
 - Android Studio to manage your project.
 - Android 4.0 (API 14) or above
 - for androidx app use 3.x version or above.
 - For apps that support library APIs and not androidx, use 2.x version

## Set up the SDK

### 1.Repository
In the main build.gradle of your project, reference the flatDir. 

```groovy
allprojects {
    repositories {
        google()
        jcenter()
        flatDir {
            dirs 'libs'
        }
    }
}
```

### 2.Dependencies
Include JCenter/Maven repository and add the following lines to your app's build.gradle, and make sure the latest SDK is used:

```groovy
dependencies {
    /* ... */

	implementation 'com.google.android.gms:play-services-location:16.0.0'
	implementation 'com.loopj.android:android-async-http:1.4.9'
	implementation 'com.google.android.gms:play-services-ads:16.0.0'
    
    // Madvertise Location SDK
    implementation(name: 'madvertiselocation-X.X', ext: 'aar')

}
```

**Note :** 

- madvertiselocation-X.X available on : [https://bitbucket.org/mngcorp/mngads-demo-android/downloads/](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/)


- The aar file doesn't contain nested (or transitive) dependecies and doesn't have a pom file which describes the dependencies used by the library.
 It means that, if you are importing a aar file using a flatDir repo you have to specify the dependencies alos in the project.
 
- You should use a maven repository (you have to publish the library in a private or public maven repo), you will not have the same issue.
In this case, gradle downloads the dependencies using the pom file which will contains the dependencies list.


### 3.Permissions
In order to run properly, the library needs the following permissions : 

* android.permission.ACCESS_BACKGROUND_LOCATION : Allows an app to access location in the background for android 10 since target 29
* android.permission.ACCESS_FINE_LOCATION : used to get the device last known location
* android.permission.ACCESS_COARSE_LOCATION : Allows an app to access approximate location.
* android.permission.ACCESS_NETWORK_STATE : used to detect if the device has connectivity
* android.permission.INTERNET : used to allow the library to send over the internet the data it has collected

```
#!xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<!-- Grants the SDK permission to access approximate location based on cell tower. -->
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<!-- Grants the SDK permission to access a more accurate location based on GPS. -->
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />

```


**Note:**

- Since Android 6.0 (API level 23), this permission is belongs to the "dangerous permissions" and must be requested at run time.

- The library does not implement this mechanism as it could interfere with your application's behavior.

## That for use in standalone without the mngads SDK

Madvertise is built based on Builder creational design pattern.
In order to initialize the MadvertiseLocation SDK, you must have an APP_ID value. 

```java
private static final String APP_ID = "XXXXXX";

```

### 1.Implementation 
#### New implementation (Since v2.3)

```java
MadvertiseLocation.configure(getApplicationContext(), APP_ID).start();
```

#### Deprecated implementation (v1.0 to v2.2)

```java
MadvertiseLocation madvertiseLocation = new MadvertiseLocationBuilder(getApplicationContext())
                .appId(APP_ID)
                .build();

MadvertiseLocation.with(madvertiseLocation);

```


### 2.Stop service (Since 2.3 version)
The implementation of this method allows to stop the tracking service

```java
    public static void stop() {
        if (mContext != null && !TextUtils.isEmpty(mAppId)) {
        MadvertiseLocationReceiver.stop(mContext);
            MadvertiseAlarmReceiver.stop(mContext);
        }
    }
```
        



[madvertiselocation-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[Madvertise CMP]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home