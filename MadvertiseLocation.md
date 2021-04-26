# BlueStack Location SDK

[TOC]

BlueStack Location SDK is and android library. This SDK **works** with a **CMP** (CONSENT MANAGEMENT PROVIDERS) **only** for The **GDPR** (General Data Protection Regulation) rules. We have developed our [BlueStack CMP]

## Prerequisites

 - Android Studio to manage your project.
 - Android 4.4 (API 19) or above 
 - For apps that support Android X, use 3.x version or above.

## Set up the SDK

### 1.Repository
In the main build.gradle of your project, you must declare the Bluestack Location repository: 

```groovy
allprojects {
    repositories {
        google()
        jcenter()
     
    // For All Bluestack SDKs (Mediation, CMP, Location)
    maven 
    {
     credentials 
        {
         username "madvertise-maven"
         password "GpdGZ9GE9SK7ByWdM987"
        } 
     url "https://api.bitbucket.org/2.0/repositories/mngcorp/deploy-maven-bluestack/src/master"
     authentication 
     	{
        basic(BasicAuthentication)
    	}
     }
	}

    }
}
```

### 2.Dependencies

In the build.gradle of to your application module, you can now import the Bluestack Location  SDK by declaring it in the dependencies section:

```groovy
dependencies {

implementation 'com.madvertise:location-sdk:4.0.0'

}
```

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
	- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v2, see with the madvertise team it depends on your implementation.

### 2.Stop Service 
The implementation of this method allows to stop the tracking service

```java
MadvertiseLocation.stop(Context);
```
     

[BlueStack CMP]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home