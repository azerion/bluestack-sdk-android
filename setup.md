# Android SDK Integration

[TOC]

## Overview

MNG Ads provides functionalities for monetizing your mobile application: from premium sales with rich media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. 

**You can see :** [Our Sample](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/), [Change Log] and [Upgrade Guide].

## Prerequisites

Before You Start, MNG Ads requires minimum : 

- Android 4.4 (API level 19) or higher.
- CompileSdkVersion at least 31.
- Android Studio 4.0 or higher.


## Step 1. Installation using Gradle

**1) In the main build.gradle of your project, you must declare there repositories :**

```groovy
repositories {
    mavenCentral()

    //For SmartAdServer configuration 
    maven {  
    url 'https://packagecloud.io/smartadserver/android/maven2'  
	}
	
	// Optional: Huawei services dependencies repository
	maven { url 'https://developer.huawei.com/repo/' }
	
    //For Ogury configuration
      maven {
        url 'https://maven.ogury.co/'
    }

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
     
     
      // For Sync SDK 
    maven {
             url 'https://api.bitbucket.org/2.0/repositories/sync_tv/maven-sync/src/master'
            credentials {
                username "guestsync"
                password "ELn3qwzMCWmJcawgHdqM"
            }
            authentication {
                basic(BasicAuthentication)
            }
     }
}
```

**2) Include JCenter/Maven repository and add the following lines to your app's build.gradle, and make sure the latest SDK is used:**


**Mandatory :**

- Google play services 

```groovy
dependencies {
//Google Ads SDK
implementation 'com.google.android.gms:play-services-base:18.0.1'
}
```

- Bluestack Mediation SDK

```groovy
dependencies {
// Bluestack SDK
implementation 'com.madvertise:bluestack-core-sdk:4.1.0'
}
```


**Recommended :**

- Google Ads SDK 
- AudienceNetwork 
- SmartAdServer (**Note :** It available as in-App Bidding Bidder)

```groovy
dependencies {
//Google Advertising Id
implementation 'com.google.android.gms:play-services-ads-identifier:18.0.1'

//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:20.6.0'
implementation 'androidx.work:work-runtime-ktx:2.7.1'

//Location, if you app use GPS data only with a CMP
implementation 'com.google.android.gms:play-services-location:19.0.1'
        
//Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.8.0'

//Smart Display SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.17.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'
```

- BlueStack Consent Management Provider (CMP) [BlueStack CMP](https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master)

Make your application comply with the new General Data Protection Regulation (GDPR) law applies in Europe. (for additional information please visit our [website](https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home))

- BlueStack Location SDK [BlueStack Location](https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master)

This SDK works with our MAdvertise CMP only for The GDPR rules. (for additional information please visit our [website](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/MadvertiseLocation))

**Recommended in-App Bidding :**

- Amazon APS 
- Criteo


```groovy
dependencies {
// Amazon SDK
implementation ("com.amazon.android:aps-sdk:9.4.2")

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:4.4.0'

```

**Optional :**

- AdColony 
- Ogury (**Note :** An API Key will be assigned to your application by mngads support team for Ogury library.) 
- Sync



```groovy
dependencies {  
// Adcolony SDK
implementation 'com.adcolony:sdk:4.6.4'
implementation 'com.madvertise:bluestack-mediation-adcolony:4.6.4'

//Ogury SDK
implementation 'co.ogury:ogury-sdk-no-data:5.2.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.2.0'

//Sync SDK
implementation 'tv.sync:syncdisplay:3.2.1'

```
**Support library for Huawei devices :**

In the dependencies section of your application module build.gradle file, declare the BlueStack huawei support library dependency and the Huawei library:

```groovy
//Huawei devices
implementation 'com.huawei.hms:ads-identifier:3.4.39.302'
implementation 'com.madvertise:bluestack-mediation-huawei:1.0.0'
```

**See our [build.gradle] sample**

## Step 2. Update AndroidManifest.xml

**1) Manifest Permissions**

Add the following permissions to your AndroidManifest.xml file inside the manifest tag but outside the <application> tag, if not done already:
 
```java
    <!-- Grants the SDK permission to access approximate location based on cell tower. -->
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    
    <!-- Grants the SDK permission to access a more accurate location based on GPS. -->
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    
    <!-- External storage is used for pre-caching features if available -->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
     
    <!--Used by Sync-->
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
        
    <!--Used by AdColony-->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <!--Used by AdColony-->
    <uses-permission android:name="android.permission.VIBRATE"
    <!--Grants the SDK permission to access the Ad Id,since android 12 and target 31-->
    <uses-permission android:name=""com.google.android.gms.permission.AD_ID" />

```

**2) Google Play Services** 

Add the following  inside the <application> tag in your AndroidManifest , if not done already:

```xml
  <meta-data
            android:name="com.google.android.gms.ads.AD_MANAGER_APP"
            android:value="true"/>
```


## Step 3. Configuring the SDK

### Init the SDK

You have to init the SDK in your application class


```java
...
import com.mngads.MNGAdsFactory;
...
public class DemoApp extends Application{

@Override
public void onCreate() {
super.onCreate();
MNGAdsFactory.initialize(this,"YOUR_APP_ID");
}
}
```

### Verify Your Integration

To verify if the SDK is fully initialized, you have to implement the Factory Listener in your code:  

```java
MNGAdsFactory.setMNGAdsSDKFactoryListener(new MNGAdsSDKFactoryListener() {
            @Override
            public void onMNGAdsSDKFactoryDidFinishInitializing() {
                Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
            }

            @Override
            public void onMNGAdsSDKFactoryDidFailInitialization(Exception e) {
                Log.d(TAG, "MNGAdsSDKFactoryDidFailInitialization: " + e);
            }
        });

```

The SDK will notify your Listener of all possible events listed below :

 - onMNGAdsSDKFactoryDidFinishInitializing() is called when the initialisation finished or is already installed.
 
 - onMNGAdsSDKFactoryDidFailInitialization() is called when an error occurs during initialisation.

## Troubleshooting

### Enabling debug mode
To enbale debug mode you need to set debug mode to true :

```java
...
MNGAdsFactory.setDebugModeEnabled(true);
...

```


### CompileOptions

You have to add compileOptions to your module's gradle file like so:

```groovy
android {
    // …

    compileOptions {
        sourceCompatibility 1.8
        targetCompatibility 1.8
    }
}

```
### OKHTTP issue

If you use okhhtp in your project or in an other dependency, add these lines in your build.gradle to avoid build error :

```java
buildTypes
{
packagingOptions {
exclude 'META-INF/maven/com.squareup.okhttp3/okhttp/pom.properties'
exclude 'META-INF/maven/com.squareup.okhttp3/okhttp/pom.xml'
exclude 'META-INF/maven/com.squareup.okio/okio/pom.xml'
exclude 'META-INF/maven/com.squareup.okio/okio/pom.properties'
}
}
```
### Android multidex issue

For more information, please see this [AndroidMultidex]

### Include Kotlin to an existing app

Your build.gradle files should look similar to the examples below:

- Add Kotlin to your project classpath : 

**Project build.gradle file**

```
dependencies {
classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.6.20"
}
```

- Applies the Kotlin Android plugin to each module that contains Kotlin files.

**Module build.gradle file**

```
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'
```

```
dependencies {
   implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk8:1.6.20"
}
```

### Network Security Configuration
Since Android 9 (API level 28), all network requests must use HTTPS protocol, basic HTTP requests will be blocked by default.
To avoid your ads being blocked by the default network security configuration, you should create your own network security configuration XML file.

In your **res** folder, create the folder **xml** (if not created yet) then create a file named **network-security-configuration.xml**.

Your file must be formatted like this:


```
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <base-config cleartextTrafficPermitted="true">
        <trust-anchors>
            <certificates src="system" />
            <certificates src="user" />
        </trust-anchors>
    </base-config>
</network-security-config>
```

Once the file created, make sure to add **android:networkSecurityConfig="@xml/network_security_config"** in the application tag of your AndroidManifest.xml file. For instance:

```
<application
  android:name=".MyApplication"
  android:icon="@mipmap/ic_launcher"
  android:label="@string/app_name"
  android:networkSecurityConfig="@xml/network_security_config">
</application>
```

## Select an ad format

MNG SDK offers a number of different ad formats :

- Banner [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/banner)

- Interstitial [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial)

- Native Ads [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/nativead)

- Rewarded Video [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/rewarded-video)

- Infeed [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/infeed)

- Thumbnail [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/thumbnail)

- Sync [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/sync)

[omsdk-x.x.x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[link]:https://developer.android.com/training/location/retrieve-current.html
[SmartAdServer]:http://documentation.smartadserver.com/displaySDK
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mngads-sdk-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[MngAds sample app]:https://bitbucket.org/mngcorp/mngads-demo-android/src
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
[Change Log]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/change-log
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsRequiredJars/AudienceNetwork.jar?at=master&fileviewer=file-view-default
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[mngAds state diagram]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/diagram
[Amazon]:https://developer.amazon.com/public/resources/development-tools/sdk
[Amazon.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[DTBAndroidSDK-x.x.x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Flurry]:https://developer.yahoo.com/flurry/
[FlurryAds.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[FlurryAnalytics.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Best practice Mngads and Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[AndroidMultidex]:http://developer.android.com/intl/ko/tools/building/multidex.html
[Ogury]:http://www.ogury.co/
[ogury-x.x.x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Native Ads guidelines]:./nativead
[ApplicationManager.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/utils/ApplicationManager.java?at=master&fileviewer=file-view-default
[BaseActivity.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/BaseActivity.java?at=master&fileviewer=file-view-default
[Interstitial Guideline]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial-guideline
[see Proguard rules on our faq]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-if-your-app-uses-proguard-you-must-edit-your-proguard-settings-to-avoid-stripping-google-play-out-of-your-app
[more details about instance on our FAQ]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-interstitial-did-load-callback-without-display
[umooveVx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[build.gradle]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/build.gradle?at=master&fileviewer=file-view-default
[Android X]:https://developer.android.com/jetpack/androidx/migrate