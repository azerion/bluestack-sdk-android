# Android SDK Integration

[TOC]

## Overview

MNG Ads provides functionalities for monetizing your mobile application: from premium sales with rich media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. 

**You can see :** [Our Sample](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/), [Change Log] and [Upgrade Guide].

## Prerequisites

Before You Start, MNG Ads requires minimum : 

- Android 4.4 (API level 19) or higher.
- CompileSdkVersion at least 29.
- Android Studio 3.5 or higher.
- Since Version 3.0 and later, it’s required that your project migrates from Android Support Libraries to Jetpack Libraries ([Android X]).


## Step 1. Installation using Gradle

**1) In the main build.gradle of your project, you must declare there repositorys :**

```groovy
repositories {
    mavenCentral()


    //For SmartAdServer configuration 
    maven {  
    url 'https://packagecloud.io/smartadserver/android/maven2'  
	}
	
	//For Huawei devices compatibility
	maven { url 'http://developer.huawei.com/repo/' }
	
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
implementation 'com.google.android.gms:play-services-base:17.6.0'
}
```

- Bluestack Mediation SDK

```groovy
dependencies {
// Bluestack SDK
implementation 'com.madvertise:bluestack-core-sdk:3.6.2'
}
```


**Recommended :**

- Google Ads SDK 
- AudienceNetwork 
- SmartAdServer (**Note :** It available as in-App Bidding Bidder)

```groovy
dependencies {
//Google Advertising Id
implementation 'com.google.android.gms:play-services-ads-identifier:17.0.1'

//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:20.2.0'

//Location, if you app use GPS data only with a CMP
implementation 'com.google.android.gms:play-services-location:18.0.0'
        
//Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.5.1'

//Smart Display SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.12.0'

```

- BlueStack Consent Management Provider (CMP) [BlueStack CMP](https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master)

Make your application comply with the new General Data Protection Regulation (GDPR) law applies in Europe. (for additional information please visit our [website](https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home))

- BlueStack Location SDK [BlueStack Location](https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master)

This SDK works with our MAdvertise CMP only for The GDPR rules. (for additional information please visit our [website](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/MadvertiseLocation))

**Recommended in-App Bidding :**

- Amazon APS [AAR file is available here](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/libs/)
- Criteo


```groovy
dependencies {
// Amazon APS SDK
implementation(name: 'amazon-aps-sdk-9.0.0', ext: 'aar')

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:1.1.0'

```

**Optional :**

- AppLovin
- Mopub Marketplace 
- Flurry 
- AdColony 
- Ogury (**Note :** An API Key will be assigned to your application by mngads support team for Ogury library.) 
- Sync


```groovy
dependencies {
// AppLovin SDK
implementation 'com.applovin:applovin-sdk:9.13.0'
implementation 'com.madvertise:bluestack-mediation-applovin:1.0.0'

// MoPub Marketplace SDK
implementation('com.mopub:mopub-sdk:5.13.1@aar') {
        transitive = true
        exclude module: 'libAvid-mopub' // To exclude AVID
        exclude module: 'moat-mobile-app-kit' // To exclude Moat
    }
implementation 'com.madvertise:bluestack-mediation-mopub:1.0.0'
    
// Adcolony SDK
implementation 'com.adcolony:sdk:4.5.0'
implementation 'com.madvertise:bluestack-mediation-adcolony:1.1.0'

//Ogury SDK
implementation 'co.ogury:ogury-sdk:5.0.9'
implementation 'com.madvertise:bluestack-mediation-ogury:1.1.0'

//Sync SDK
implementation 'tv.sync:syncdisplay:3.2.1'

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
    <uses-permission android:name="android.permission.VIBRATE" />

```

**2) Google Play Services** 

Add the following  inside the <application> tag in your AndroidManifest , if not done already:

```xml
  <meta-data
            android:name="com.google.android.gms.ads.AD_MANAGER_APP"
            android:value="true"/>
```

**3) AppLovin SDK key**


Add your AppLovin SDK key to the app’s AndroidManifest as a child of the application tag, like so: 
 
```java
<meta-data android:name="applovin.sdk.key"
          android:value="YOUR_SDK_KEY" />
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

To verify if the SDK is fully initialized you have to call isInitialized():

```java

public class MainActivity extends Activity implements MNGAdsSDKFactoryListener{
...
if(MNGAdsFactory.isInitialized()){

//The SDK is initialized

}else {

//The SDK is initializing
//set up a callback that will be called when is fully initialized
MNGAdsFactory.setMNGAdsSDKFactoryListener(this);

}
...

...
@Override
    public void onMNGAdsSDKFactoryDidFinishInitializing() {

        Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
    }

    @Override
    public void onMNGAdsSDKFactoryDidFailInitialization(Exception e) {

        Log.d(TAG, "MNGAdsSDKFactoryDidFailInitialization: " + e);
    }

    @Override
    public void onMNGAdsSDKFactoryDidResetConfig() {

        Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
    }

...

```

**Note:**

 - onMNGAdsSDKFactoryDidFinishInitializing() is called when the the first initialisation finished.
 
 - onMNGAdsSDKFactoryDidResetConfig() is called when the sdk configuraiton has been updated and finished reinitialisation.
 
 - onMNGAdsSDKFactoryDidFailInitialization() is called when an error occurs during initialisation or configuration update.

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
classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.4.0"
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
   implementation "org.jetbrains.kotlin:kotlin-stdlib:1.4.0"
}
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