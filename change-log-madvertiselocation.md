Change log and release notes for MadvertiseLocation for Android.

### Version 4.1.0
#### Release date: January 13, 2022

**Release notes :**

- Support Android 12.
- Fixed a rare crash occurring in LocationFusedReceiver.

**Upgrading :**

- Update targetSdkVersion / compileSdkVersion to 31
- Update kotlin version to 1.6.0 or above
- Added new permission (Apps that target Android SDK 31 or higher should declare com.google.android.gms.permission.AD_ID in the app manifest to access Ad Id).

```xml
<uses-permission android:name="com.google.android.gms.permission.AD_ID" />
```

### Version 4.0.1
#### Release date: July 9, 2021

- issue with proguard-rules and Kotlin

### Version 4.0.0
#### Release date: April 26, 2021

- Migration Java to Kotlin
- Improve Android 11 compatibility.
- Distinguish foreground and background points.
- rewrite workflow/architecture of Receiver (Detect breakpoint, algo optimisations) and Worker (points storage)

### Version 3.2.5
#### Release date: December 16, 2020

Any occurences of location permission have been removed from sdk, in order to respect the safer and transparent access to user location.

*For Foreground access only :*

You need to add those permission to your AndroidManifest.xml if it does not exist.

```xml
<!-- Grants the SDK permission to access approximate location based on cell tower. -->
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<!-- Grants the SDK permission to access a more accurate location based on GPS. -->
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

*For Foreground and background access :*

You need to add those permission to your AndroidManifest.xml if it does not exist.

```xml
<!-- Grants the SDK permission to access approximate location based on cell tower. -->
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<!-- Grants the SDK permission to access a more accurate location based on GPS. -->
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<!-- Grants the SDK permission o access location in the background,since android 10 and target 29. -->
<uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
```


### Version 3.2.4
#### Release date: October 1, 2020

 - fix ArrayIndexOutOfBoundsException issue on decodedMadvertiseTCFV1

### Version 3.2.3
#### Release date: September 18th, 2020

**SDK is now delivered through Maven/Bitbucket repository**

In the main build.gradle of your project, you must declare the Bluestack repository: 


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
```

In the build.gradle of to your application module, you can now import the Bluestack Location by declaring it in the dependencies section:

```groovy
implementation 'com.madvertise:location-sdk:3.2.3'
```



### Version 3.2.2
#### Release date: September 7th, 2020

 - fix TCF v2 issue
 - fix SQLiteDatabaseLockedException

### Version 3.2
#### Release date: July 23th, 2020
 
 TCF v2 support.

**Update configure() method :**  

 
Replace the following line from  :

```groovy
MadvertiseLocation.configure(getApplicationContext(), APP_ID).start()
            
```
with the following line :

```groovy
MadvertiseLocation.configure(getApplicationContext(), YOUR_APP_ID, CONSENT_FLAG).start();
            
```
The configure method takes the following parameters:

- the Application Context instance.
- the App ID.
- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3).
	- 0 = Not allow to send location.
	- 1 = When you managed location according to consent value.
	- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

### Version 3.1
#### Release date: May 25th, 2020

- JobService Optimization.
- Request Location Optimization.

### Version 3.0
#### Release date: February 18th, 2020

 - android 10 support.
- Fully compatible with AndroidX.

### Version 2.8
#### Release date: December 5th, 2019

 - fix restart jobService

### Version 2.7
#### Release date: November 28th, 2019

 - Loc-CheckConsent - header

### Version 2.6
#### Release date: November 4th, 2019

 - implementation onDowngrade for SQLiteOpenHelper

### Version 2.5
#### Release date: September 5th, 2019

 - jobId optimization

### Version 2.4
#### Release date: September 2th, 2019

 - Date management optimizations
 - Battery life optimizations
 - fix dequeueWork() crash on JobIntentService

### Version 2.3
#### Release date: June 25th, 2019

 - Add stop method
 - Date optimzation
 - Add debug logs
 - GDPR consentement optimization
 - number of POI optimization

If you are using madvertiseLocation standalone without the mngads SDK, you must change implementation

replace


```
#!java

@Override
private void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
	
	MadvertiseLocation madvertiseLocation = new MadvertiseLocationBuilder(getApplicationContext())
                .appId(APP_ID)
                .build();

   MadvertiseLocation.with(madvertiseLocation);
}
```

by


```
#!java
MadvertiseLocation.configure(getApplicationContext(), APP_ID).start();

```



### Version 2.2
#### Release date: April 10th, 2019

 - Manage MadvertiseConsent_ConsentString (specific purposes for GPS data) from CMP that replace IABConsent_LocationPurpose
 - Allow debug Mode

### Version 2.1
#### Release date: February 8th, 2019

 - Manage IABConsent_LocationPurpose from CMP

### Version 2.0
#### Release date: January 14th, 2019

 - Optimization accuracy
 - Restart service on android 8/9

### Version 1.1
#### Release date: December 12th, 2018

 - fix issue on android 8

### Version 1.0
#### Release date: October 24th, 2018

 - initial release