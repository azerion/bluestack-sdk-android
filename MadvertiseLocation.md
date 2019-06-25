#Madvertise Location SDK

[TOC]

MadvertiseLocation SDK is and android library. This SDK **works** with a **CMP** (CONSENT MANAGEMENT PROVIDERS) **only** for The **GDPR** (General Data Protection Regulation) rules. We have developed our [Madvertise CMP]

## Prerequisites

 - The latest versions of the Android SDK, [madvertiselocation-x.aar].
 - Android Studio to manage your project.
 - Android 4.0 (API 14) or above

## Set up the SDK

### Repository
In the top level build file. reference the flatDir. 

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

### Dependencies
add the dependency to the library in the application gradle file

```groovy
dependencies {
    /* ... */

	implementation 'com.google.android.gms:play-services-location:16.0.0'
	implementation 'com.loopj.android:android-async-http:1.4.9'
	implementation 'com.google.android.gms:play-services-ads:16.0.0'
    
    // Madvertise Location SDK
    implementation(name: 'madvertiselocation', ext: 'aar')

}
```

[madvertiselocation-x.aar] available on https://bitbucket.org/mngcorp/mngads-demo-android/downloads/

Note : 

 The aar file doesn't contain nested (or transitive) dependecies and doesn't have a pom file which describes the dependencies used by the library.
 It means that, if you are importing a aar file using a flatDir repo you have to specify the dependencies alos in the project.
 
 You should use a maven repository (you have to publish the library in a private or public maven repo), you will not have the same issue.
In this case, gradle downloads the dependencies using the pom file which will contains the dependencies list.


### Permissions
In order to run properly, the library needs the following permissions : 

* android.permission.ACCESS\_FINE_LOCATION : used to get the device last known location

* android.permission.ACCESS\_COARSE_LOCATION : Allows an app to access approximate location.

* android.permission.ACCESS\_NETWORK_STATE : used to detect if the device has connectivity

* android.permission.INTERNET : used to allow the library to send over the internet the data it has collected


Note:

Since Android 6.0 (API level 23), this permission is belongs to the "dangerous permissions" and must be requested at run time.

The library does not implement this mechanism as it could interfere with your application's behavior.

## That for use in standalone without the mngads SDK

Madvertise is built based on Builder creational design pattern.
In order to initialize the MadvertiseLocation SDK, you must have an APP_ID value. 

```java

private static final String APP_ID = "XXXXXX";
//new implementation since v2.3
MadvertiseLocation.configure(getApplicationContext(), APP_ID).start();


//deprecated implementation (v1.0 to v2.2)
@Override
private void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
	
	MadvertiseLocation madvertiseLocation = new MadvertiseLocationBuilder(getApplicationContext())
                .appId(APP_ID)
                .build();

   MadvertiseLocation.with(madvertiseLocation);
}
```
        



[madvertiselocation-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[Madvertise CMP]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home