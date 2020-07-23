# Madvertise Location SDK

[TOC]

MadvertiseLocation SDK is and android library. This SDK **works** with a **CMP** (CONSENT MANAGEMENT PROVIDERS) **only** for The **GDPR** (General Data Protection Regulation) rules. We have developed our [Madvertise CMP]

## Prerequisites

 - Android Studio to manage your project.
 - Android 4.0 (API 14) or above 
 - For apps that support Android X, use 3.x version or above. 
 - If not yet, use 2.x version.

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

    implementation(name: 'madvertiselocation-X.X', ext: 'aar')

}
```


madvertiselocation-X.X available on : [https://bitbucket.org/mngcorp/mngads-demo-android/downloads/](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/)


### 3.Permissions
In order to run properly, the library needs the following permissions : 

* android.permission.ACCESS_BACKGROUND_LOCATION : Allows an app to access location in the background for android 10 since target 29
* android.permission.ACCESS_FINE_LOCATION : used to get the device last known location
* android.permission.ACCESS_COARSE_LOCATION : Allows an app to access approximate location.
* android.permission.ACCESS_NETWORK_STATE : used to detect if the device has connectivity
* android.permission.INTERNET : used to allow the library to send over the internet the data it has collected

```xml

<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<!-- Grants the SDK permission to access approximate location based on cell tower. -->
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<!-- Grants the SDK permission to access a more accurate location based on GPS. -->
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<!-- Grants the SDK permission o access location in the background,since android 10 and target 29. -->
<uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />

```

You don't need to add those permission to your AndroidManifest.xml unless your application already uses them.



**Note:**

- Since Android 6.0 (API level 23), this permission is belongs to the "dangerous permissions" and must be requested at run time.

- The library does not implement this mechanism as it could interfere with your application's behavior.

- **It is therefore your job to ask the user to grant the permission.** This is very well described in the official [Android documentation](https://developer.android.com/training/permissions/requesting.html).


Here is an example :

```java

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.Q) {
            if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED
                    && ActivityCompat.checkSelfPermission(this, ACCESS_COARSE_LOCATION) != PackageManager.PERMISSION_GRANTED
                    && ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_BACKGROUND_LOCATION) != PackageManager.PERMISSION_GRANTED) {
                    
                    ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.ACCESS_FINE_LOCATION, Manifest.permission.ACCESS_COARSE_LOCATION, Manifest.permission.ACCESS_BACKGROUND_LOCATION}, LOCATION_REQUEST_CODE);
			
            }
        } else {
            if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) != PackageManager.PERMISSION_GRANTED
                    && ActivityCompat.checkSelfPermission(this, ACCESS_COARSE_LOCATION) != PackageManager.PERMISSION_GRANTED) {
                    
                    ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.ACCESS_FINE_LOCATION, Manifest.permission.ACCESS_COARSE_LOCATION}, LOCATION_REQUEST_CODE);
                
            }
        }

```

## That for use in standalone without the mngads SDK

Madvertise is built based on Builder creational design pattern.
In order to initialize the MadvertiseLocation SDK, you must have an APP_ID value. 

```java
private static final String APP_ID = "XXXXXX";

```

### 1.Implementation 

```java
MadvertiseLocation.configure(getApplicationContext(), APP_ID, CONSENT_FLAG).start();
```
The configure method takes the following parameters:

- the Application Context instance.
- the App ID.
- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3). (since 3.2)
	- 0 = Not allow to send location.
	- 1 = When you managed location according to consent value.
	- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

### 2.Stop Service 
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