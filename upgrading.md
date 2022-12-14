# upgrading SDK
See [Wiki] and [Help Center]  for more detailed informations.
you must check [Change Log]. You need to keep all Ad Network jars/aar up to date

## Version 4.1.3

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.1.3'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:63.0.0'

// DFP SDK
implementation 'com.google.android.gms:play-services-ads:21.1.0'
implementation 'com.google.android.gms:play-services-ads-identifier:18.0.1'
implementation 'com.google.android.gms:play-services-base:18.1.0''
// Starting from version 20.4.0, Google Mobile Ads SDK require an explicit dependency :
implementation 'androidx.work:work-runtime-ktx:2.7.1'

// SmartAdServer SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.19.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'

//Amazon SDK
implementation ("com.amazon.android:aps-sdk:9.5.7")

// Ogury SDK
implementation 'co.ogury:ogury-sdk-no-data:5.3.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.3.0'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.6.1'
implementation 'com.madvertise:bluestack-mediation-criteo:4.6.2'

```

## Version 4.1.2

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.1.2'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:63.0.0'

// DFP SDK
implementation 'com.google.android.gms:play-services-ads:20.6.0'
implementation 'com.google.android.gms:play-services-ads-identifier:18.0.1'
implementation 'com.google.android.gms:play-services-base:18.0.1'
// Starting from version 20.4.0, Google Mobile Ads SDK require an explicit dependency :
implementation 'androidx.work:work-runtime-ktx:2.7.1'

// SmartAdServer SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.17.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk-no-data:5.3.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.3.0'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:4.4.0'

```


**Support library for Huawei devices :**

```groovy
implementation 'com.huawei.hms:ads-identifier:3.4.39.302'
implementation 'com.madvertise:bluestack-mediation-huawei:1.0.1'
```

## Version 4.1.1

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.1.1'

// For BlueStack Location SDK 
implementation 'com.madvertise:location-sdk:4.1.1'

```

## Version 4.1.0

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.1.0'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:63.0.0'

// DFP SDK
implementation 'com.google.android.gms:play-services-ads:20.6.0'
implementation 'com.google.android.gms:play-services-ads-identifier:18.0.1'
implementation 'com.google.android.gms:play-services-base:18.0.1'
// Starting from version 20.4.0, Google Mobile Ads SDK require an explicit dependency :
implementation 'androidx.work:work-runtime-ktx:2.7.1'

// SmartAdServer SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.17.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk-no-data:5.2.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.2.0'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:4.4.0'

```


## Version 4.0.4

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.0.4'
```


## Version 4.0.3

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.0.3'
```


## Version 4.0.2

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.0.2'
```


## Version 4.0.1

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.0.1'

// For BlueStack Location SDK 
implementation 'com.madvertise:location-sdk:4.1.0'

```

## Version 4.0.0

**Prerequisites**
Update targetSdkVersion / compileSdkVersion to 31

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:4.0.0'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:63.0.0'

// DFP SDK
implementation 'com.google.android.gms:play-services-ads:20.5.0'
implementation 'com.google.android.gms:play-services-ads-identifier:18.0.0'
implementation 'com.google.android.gms:play-services-base:18.0.0'
// Starting from version 20.4.0, Google Mobile Ads SDK require an explicit dependency :
implementation 'androidx.work:work-runtime-ktx:2.7.1'

// SmartAdServer SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.15.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk-no-data:5.1.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.1.1'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:4.4.0'

```

**Interstitial Listener**

Add the interstitialDidShown new callback to better count impressions of Interstitial Ad formats: 

```java
@Override
public void interstitialDidShown() {
Log.d(TAG, "interstitial Did Shown")
}
```
**Support library for Huawei devices :**

 In the main build.gradle of your project, declare the huawei repository:

```groovy
maven { url 'https://developer.huawei.com/repo/' }
```

In the dependencies section of your application module build.gradle file, declare the BlueStack huawei support library dependency and the Huawei library:

```groovy
implementation 'com.huawei.hms:ads-identifier:3.4.39.302'
implementation 'com.madvertise:bluestack-mediation-huawei:1.0.0'
```

	
**Initialized Listener**

The onMNGAdsSDKFactoryDidResetConfig() method has been removed from setMNGAdsSDKFactoryListener.  

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


## Version 3.6.5

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.5'

```

## Version 3.6.4

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.4'

```

**Update Amazon SDK :** 


In your app's build.gradle, replace the following line from the "dependencies" :
  
```groovy
implementation(name: 'amazon-aps-sdk-9.0.0', ext: 'aar')
```
with the following line :

```groovy
repositories {
    mavenCentral()
}
dependencies {
    implementation ("com.amazon.android:aps-sdk:9.2.2")
}
```

## Version 3.6.3

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.3'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:62.0.0'

// For BlueStack Location SDK 
implementation 'com.madvertise:location-sdk:4.0.1'

// DFP SDK
implementation 'com.google.android.gms:play-services-ads:20.4.0'
implementation 'com.google.android.gms:play-services-ads-identifier:17.1.0'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.8.0'
    
// SmartAdServer SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.14.0'
// Optional : add Smart support library for Huawei devices
implementation 'com.smartadserver.android:smart-core-sdk-huawei-support:1.0.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk:5.1.0'
implementation 'com.madvertise:bluestack-mediation-ogury:5.1.0'

// AdColony SDK
implementation 'com.adcolony:sdk:4.6.4'
implementation 'com.madvertise:bluestack-mediation-adcolony:4.6.4'
```

## Version 3.6.2

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.2'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.5.1'
```



## Version 3.6.1
```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.1'
```

## Version 3.6.0


**Upgrade mediation SDKs**


In your project build.gradle, Add the following line from  :

```groovy
mavenCentral()
```

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.6.0'

// BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:59.0.0'

// Google SDK
implementation 'com.google.android.gms:play-services-ads:20.2.0'
implementation 'com.google.android.gms:play-services-ads-identifier:17.0.1'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.5.0'
    
// Smartadserver SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.12.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk:5.0.9'
implementation 'com.madvertise:bluestack-mediation-ogury:1.1.0'
```

- **Update Amazon SDK :** 

In your app's build.gradle, replace the following line from the "dependencies" :

```groovy 
//Amazon SDK
implementation 'com.amazon.android:aps-sdk:8.4.3@aar'
```
with the following line [AAR file is available here](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/libs/) :
  
```groovy
implementation(name: 'amazon-aps-sdk-9.0.0', ext: 'aar')
```

- **Update Criteo SDK :** 

In your project build.gradle, **remove** the following line from  :

```groovy 
maven { 
url "https://pubsdk-bin.criteo.com/publishersdk/android" 
}
```
In your app's build.gradle, **update** the following line from the "dependencies" :
  
```groovy
// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.4.0'
implementation 'com.madvertise:bluestack-mediation-criteo:1.1.0'
```

- **Update AdColony SDK :** 

In your project build.gradle, **remove** the following line from  :

```groovy 
maven {  
	url  "https://adcolony.bintray.com/AdColony"  
}
```

In your app's build.gradle, **update** the following line from the "dependencies" :
  
```groovy
// AdColony SDK
implementation 'com.adcolony:sdk:4.5.0'
implementation 'com.madvertise:bluestack-mediation-adcolony:1.1.0'
```

 

## Version 3.5.0

In order to avoid reference of unused mediation adapter on https://exodus-privacy.eu.org/en/, we are using separate adaptor and Android Reflexion.Do not forget to add com.madvertise:bluestack-mediation-[ADAPTER_NAME] aar on your build.gradle file

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.5.0'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:57.0.0'

// For BlueStack Location SDK 
implementation 'com.madvertise:location-sdk:4.0.0'

// Google SDK
implementation 'com.google.android.gms:play-services-ads:20.0.0'
implementation 'com.google.android.gms:play-services-base:17.6.0'

//Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.4.0'

//Sync Display SDK
implementation 'tv.sync:syncdisplay:3.2.1'

//Amazon SDK
implementation 'com.amazon.android:aps-sdk:8.4.3@aar'
    
// Ogury SDK
implementation 'co.ogury:ogury-sdk:5.0.8'
implementation 'com.madvertise:bluestack-mediation-ogury:1.0.0'

//AdColony SDK
implementation 'com.adcolony:sdk:4.4.1'
implementation 'com.madvertise:bluestack-mediation-adcolony:1.0.0'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.3.0'
implementation 'com.madvertise:bluestack-mediation-criteo:1.0.0'

// Applovin SDK
implementation 'com.applovin:applovin-sdk:9.13.0'
implementation 'com.madvertise:bluestack-mediation-applovin:1.0.0'

// MoPub SDK
implementation('com.mopub:mopub-sdk:5.13.1@aar') {
        transitive = true
        exclude module: 'libAvid-mopub' // To exclude AVID
        exclude module: 'moat-mobile-app-kit' // To exclude Moat
    }
implementation 'com.madvertise:bluestack-mediation-mopub:1.0.0'

```

## Version 3.4.0


**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.4.0'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:55.0.0'

// Google SDK
implementation 'com.google.android.gms:play-services-ads:19.6.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk:5.0.5'

//AdColony SDK
implementation 'com.adcolony:sdk:4.3.1'  

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:4.2.1'

```

**Update SmartAdServer SDK :**

In your app's build.gradle, replace the following lines from the "dependencies" :

```groovy
// Smartadserver SDKs
implementation 'com.smartadserver.android:smart-display-sdk:7.6.2@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.6.2@aar'
// Add dependencies required by Smart Display SDK
implementation 'com.squareup.okhttp3:okhttp:3.12.1'
implementation 'com.google.android.exoplayer:exoplayer:2.11.0'
implementation 'com.huawei.hms:ads-identifier:3.4.28.305'
implementation 'com.huawei.hms:location:4.0.2.300'
```
with the following line :

```groovy
implementation 'com.smartadserver.android:smart-display-sdk:7.8.1'
```

**Add Thumbnail and Sync format :**

- Thumbnail [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/thumbnail)

- Sync [Integration guides](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/syncDisplay)

## Version 3.3.6

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.6'
implementation 'com.madvertise:cmp-sdk:54.0.0'
```

## Version 3.3.5

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.5'
```
## Version 3.3.4

**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.4'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:51.0.0'

// For BlueStack Location SDK
implementation 'com.madvertise:location-sdk:3.2.5'

```

**Upgrade Retency SDKs**

- Remove retency sdk jar file.
- In your app's build.gradle, replace the following line from the "dependencies":
  
```groovy
implementation files('libs/retency-sdk-1.0.1.jar')
```

with the following line :

```groovy
implementation 'com.retency:sdk:2.0.0'
```

## Version 3.3.3


**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.3'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:49.0.0'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.2.0'

// Google SDK
implementation 'com.google.android.gms:play-services-ads:19.5.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk:5.0.3'

// SmartAdServer SDKs
implementation 'com.smartadserver.android:smart-display-sdk:7.6.2@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.6.2@aar'

//AdColony SDK
implementation 'com.adcolony:sdk:4.3.0'  

//Amazon SDK
implementation 'com.amazon.android:aps-sdk:8.4.1@aar'

```

## Version 3.3.2


**Upgrade mediation SDKs**
In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.2'

```

## Version 3.3.1


**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.1'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:48.0.0'

```

## Version 3.3.0


**Upgrade mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.3.0'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:42.0.0'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:3.10.1'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:6.1.0'

// Google SDK
implementation 'com.google.android.gms:play-services-ads:19.4.0'

```

**Update Ogury SDK :**  
 
In your project/app build.gradle, **replace** the following line from  :
  
```groovy
repositories {
maven {
        url 'https://maven.ogury.co/beta'
    }
}
dependencies {
    implementation 'co.ogury:ogury-sdk:4.8.3'
}
```
with the following line :

```groovy
repositories {
 maven {
        url 'https://maven.ogury.co'
    }
}
dependencies {
    implementation 'co.ogury:ogury-sdk:5.0.2'
}

```


## Version 3.2.3

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

In the build.gradle of to your application module, you can now import the Bluestack SDKs by declaring it in the dependencies section:

```groovy
// For BlueStack Mediation SDK 
implementation 'com.madvertise:bluestack-core-sdk:3.2.3'

// For BlueStack CMP SDK 
implementation 'com.madvertise:cmp-sdk:42.0.0'

// For BlueStack Location SDK
implementation 'com.madvertise:location-sdk:3.2.3'
```




## Version 3.2.2

**Upgrade mediation SDKs**

Google has made a change in desugar & dex using Gradle artifact tranforms, which allow more parallelism and caching. To avoid any problems you might get, you can add in **gradle.properties** this line below : 


```java
android.enableDexingArtifactTransform=false 
```

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy

// MNG Ads SDK  
implementation(name: 'mngads-sdk-3.2.2', ext: 'aar')

// Google SDK
implementation 'com.google.android.gms:play-services-ads:19.3.0'
implementation 'com.google.android.gms:play-services-base:17.4.0'

// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:5.11.0'

// SmartAdServer SDKs
implementation 'com.smartadserver.android:smart-display-sdk:7.6.1@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.6.1@aar'

// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:3.9.0'

// Ogury SDK
implementation 'co.ogury:ogury-sdk:4.8.3'

// Amazon APS SDK
implementation 'com.amazon.android:aps-sdk:8.3.2@aar'

// Madvertise CMP
implementation(name: 'madvertisecmp-41.0.0', ext: 'aar')

// Madvertise Data
implementation(name:  'madvertiselocation-3.2.2', ext:  'aar')

// Android SDK
implementation 'androidx.appcompat:appcompat:1.2.0'
implementation 'com.google.android.material:material:1.2.0'


```

## Version 3.2.0


**Update setLocation() method :**  

 
Replace (**if you are use location data only**) the following line from  :

```groovy
mngPreference.setLocation(location);
            
```
with the following line :

```groovy
mngPreference.setLocation(location,CONSENT_FLAG,context);
            
```
The setLocation method takes the following parameters:

- the Location instance.
- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3).
	- 0 = Not allow to send location.
	- 1 = When you managed location according to consent value.
	- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

- the Context instance.


**Upgarde mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.2.0', ext: 'aar')
//Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:5.9.1'
//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:19.2.0'
// Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:3.7.0'
//Google Ads SDK
implementation 'com.google.android.gms:play-services-base:17.3.0'
// MoPub Marketplace SDK
implementation('com.mopub:mopub-sdk:5.13.1@aar') {
        transitive = true
        exclude module: 'libAvid-mopub' // To exclude AVID
        exclude module: 'moat-mobile-app-kit' // To exclude Moat
    }
//For Madvertise data 
implementation(name:  'madvertiselocation-3.2', ext:  'aar')
//For Madvertise CMP
implementation(name: 'madvertisecmp-39.0.0', ext: 'aar')

```

**Update Ogury SDK :**  
 
In your project/app build.gradle, **replace** the following line from  :
  
```groovy
repositories {
maven {
        url 'https://maven.ogury.co'
    }
}
dependencies {
    implementation 'co.ogury:ogury-sdk:4.3.12'
}
```
with the following line :

```groovy
repositories {
 maven {
        url 'https://maven.ogury.co/beta'
    }
}
dependencies {
    implementation 'co.ogury:ogury-sdk:4.8.1'
}

```

## Version 3.1.4

```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.1.4', ext: 'aar')

```
## Version 3.1.3

**Upgarde mediation SDKs**

In your app's build.gradle, don't forget to update your dependencies as following:

```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.1.3', ext: 'aar')

//SmartAdServer SDKs
implementation 'com.smartadserver.android:smart-display-sdk:7.6.0@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.6.0@aar'

//Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:5.9.0'

//Ogury SDK
implementation 'co.ogury:ogury-sdk:4.7.0'

//For Madvertise data 
implementation(name:  'madvertiselocation-3.1', ext:  'aar')

```


## Version 3.1.2


In your app's build.gradle, don't forget to update your dependencies as following:

```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.1.2', ext: 'aar')

//SmartAdServer SDKs
implementation 'com.smartadserver.android:smart-display-sdk:7.4.1@aar'
	implementation 'com.smartadserver.android:smart-core-sdk:7.4.1@aar'

//Criteo SDK
implementation 'com.criteo.publisher:criteo-publisher-sdk:3.5.0'

//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:19.1.0'

```


## Version 3.1.1

```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.1.1', ext: 'aar')

```

## Version 3.1.0

- It???s required that your project migrates from Android Support Libraries to Jetpack Libraries (Android X) if you are using this version.

- Update targetSdkVersion / compileSdkVersion to 29


- **Update Ogury SDK :**  

In your app's build.gradle, **replace** the following line from the "dependencies" and **remove** the ogury-X.X.X.aar file :
  
```groovy
implementation(name: 'ogury-X.X.X', ext: 'aar')

```
with the following line :

```groovy
repositories {
    maven {
        url 'https://maven.ogury.co'
    }
}
dependencies {
    implementation 'co.ogury:ogury-sdk:4.3.12'
}

```


- **Network Mediation Updates :** 

In your app's build.gradle, don't forget to update your dependencies as following:


```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.1.0', ext: 'aar')

// MoPub Marketplace SDK
implementation('com.mopub:mopub-sdk:5.11.1@aar') {
        transitive = true
 exclude module: 'libAvid-mopub' // To exclude AVID
 exclude module: 'moat-mobile-app-kit' // To exclude Moat
    }
    
//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:19.0.1'
 
//AdColony SDK
implementation 'com.adcolony:sdk:4.1.4'  
 
// App Lovin SDK
implementation 'com.applovin:applovin-sdk:9.11.6'

// Smart Display SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.4.0@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.4.1@aar'

// Dependencies required by Smart Display SDK
implementation 'com.squareup.okhttp3:okhttp:3.12.0'
implementation 'com.google.android.exoplayer:exoplayer:2.8.3'
 
// Audience Network SDK
implementation 'com.facebook.android:audience-network-sdk:5.8.0'

//For GDPR Madvertise CMP
implementation(name: 'madvertisecmp-33.0.0', ext: 'aar')

```


## Version 3.0
- **It???s required that your project migrates from Android Support Libraries to Jetpack Libraries (Android X) if you are using this version.**

- **Update targetSdkVersion / compileSdkVersion to 29**

- **Add Criteo SDK :**  

Add Criteo's maven repository into your project-level build.gradle:
	
```groovy
allprojects {
    repositories {
        google()
        jcenter()

        maven { url "https://pubsdk-bin.criteo.com/publishersdk/android" }
    }
}
```

Then, in your app's build.gradle, add the following line to the "dependencies" section in order to import Criteo SDK and its dependencies :
  
```groovy
implementation 'com.criteo.publisher:criteo-publisher-sdk:3.4.0'
```
- **Update Amazon APS SDK :** 

In your app's build.gradle, replace the following line from the "dependencies" :
  
```groovy
implementation files('libs/amazon-ads-5.9.0.jar')

or

implementation(name: 'DTBAndroidSDK-X.X.X', ext: 'aar')
```
with the following line :

```groovy
implementation 'com.amazon.android:aps-sdk:8.2.1@aar'
```

- **Network Mediation Updates :** 

In your app's build.gradle, don't forget to update your dependencies as following:


```groovy

//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.0', ext: 'aar')

// Ogury SDK
implementation(name: 'ogury-4.3.7', ext: 'aar')

// Flurry SDK
implementation 'com.flurry.android:analytics:12.1.0@aar'
implementation 'com.flurry.android:ads:12.1.0@aar'

// MoPub Marketplace SDK
implementation('com.mopub:mopub-sdk:5.11.0@aar') {
        transitive = true
 exclude module: 'libAvid-mopub' // To exclude AVID
 exclude module: 'moat-mobile-app-kit' // To exclude Moat
    }
    
//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:18.3.0'
 
//AdColony SDK
implementation 'com.adcolony:sdk:4.1.3'  
 
// App Lovin SDK
implementation 'com.applovin:applovin-sdk:9.11.2'

// Add Smart Display SDK
implementation 'com.smartadserver.android:smart-display-sdk:7.4.0@aar'
implementation 'com.smartadserver.android:smart-core-sdk:7.4.0@aar'
// Add dependencies required by Smart Display SDK
implementation 'com.squareup.okhttp3:okhttp:3.12.1'
implementation 'com.google.android.exoplayer:exoplayer:2.8.3'

//For GPS data 
 implementation(name:  'madvertiselocation-3.0', ext:  'aar')

//For GDPR Madvertise CMP
implementation(name: 'madvertisecmp-29.0.0', ext: 'aar')

```


## Version 2.16

- Don't forget to update your dependencies as following :

```groovy

implementation(name: 'mngads-sdk-2.16', ext: 'aar')

//FaceBook SDK  
implementation 'com.facebook.android:audience-network-sdk:5.6.1'
```

## Version 2.15.2

- Don't forget to update your dependencies as following :

```groovy

implementation(name: 'mngads-sdk-2.15.2', ext: 'aar')
//For GPS data 
 implementation(name:  'madvertiselocation-2.6', ext:  'aar')
```

## Version 2.15.1

- Don't forget to update your dependencies as following :

```groovy

implementation(name: 'mngads-sdk-2.15.1', ext: 'aar')

```
Don't forget the following dependencies required by Smart Display SDK

```groovy
/ Add dependencies required by Smart Display SDK
	implementation 'com.google.android.gms:play-services-ads-identifier:16.0.0'
	implementation 'com.google.android.gms:play-services-location:16.0.0'
	implementation 'com.squareup.okhttp3:okhttp:3.12.0'
	implementation 'com.google.android.exoplayer:exoplayer:2.8.3'
```

## Version 2.15
- **remove implementation files('libs/omsdk-android-1.2.4-Madvertise.jar') now include on mngads-sdk-2.15**

- **Update minSdkVersion to 19 (If it's less) and targetSdkVersion / compileSdkVersion to 28**

- **Support ImageView for NativeAd's ad for Facebook Audience Network**

replace 
```java
String iconUrl=nativeObject.getAdIconUrl();
String coverImageUrl=nativeObject.getAdCoverImageUrl();

//to handle impressions and user interactions you have to register your MAdvertiseNativeContainer as your root layout container and your callToActionView view as following
nativeObject.registerViewForInteraction(nativeAdContainerView, nativeAdCallToActionView);
```
by
```java
//to handle impressions, user interactions and to display icon, image cover or the media video 
nativeObject.registerViewForInteraction(nativeAdContainerView,mediaViewGroup,iconImageView,nativeAdCallToActionView);
```
`Note : `
##### iconImageView = ImageView for NativeAd's ad Icon
##### mediaContainer = viewGroup, the sdk will handle the rendering process ( displaying) the image cover or the media video inside the view group that depends on the ad network result.

- **Added AppLovin SDK  (This guide is intended for publishers who want to load and display ads from AppLovin )**
 
 Add new dependency :

```groovy
implementation 'com.applovin:applovin-sdk:9.8.4'
```
 Add your AppLovin SDK key to the app???s AndroidManifest as a child of the `<application></application>` tag, like so: 
```java
<meta-data android:name="applovin.sdk.key"
          android:value="YOUR_SDK_KEY" />
```


- **Don't forget to update your dependencies as following :**

```groovy

implementation(name: 'mngads-sdk-2.15', ext: 'aar')
//For GDPR Madvertise CMP
implementation(name: 'MAdvertiseCmp-22', ext: 'aar')
//For GPS data 
 implementation(name:  'madvertiselocation-2.5', ext:  'aar')
 
/* Updated Network Adapters */

// MoPub Display SDK  
implementation('com.mopub:mopub-sdk:5.8.0@aar') {  
    transitive = true  
  exclude module: 'libAvid-mopub' // To exclude AVID  
  exclude module: 'moat-mobile-app-kit' // To exclude Moat  
}  
    // Add Smart Display SDK
    implementation 'com.smartadserver.android:smart-display-sdk:7.2.0@aar'
    implementation 'com.smartadserver.android:smart-core-sdk:7.2.0@aar'
    // Add dependencies required by Smart Display SDK
    implementation 'com.squareup.okhttp3:okhttp:3.12.1'
    implementation 'com.google.android.exoplayer:exoplayer:2.8.3'
//FaceBook SDK  
implementation 'com.facebook.android:audience-network-sdk:5.5.0'
// Adcolony SDK  
implementation 'com.adcolony:sdk:3.3.11'
// Amazon  
implementation(name: 'DTBAndroidSDK-8.0.0', ext: 'aar')
```

- **Ogury SDK , You must replace : (This guide is intended for publishers who used Ogury SDK )**

replace
```groovy
implementation(name: 'presage-moat-3.0.26-3.0.14', ext: 'aar')
```
by
```groovy
implementation(name: 'ogury-4.1.4', ext: 'aar')
```


## Version 2.14.1

- Don't forget to update your dependencies as following :

```groovy

implementation(name: 'mngads-sdk-2.14.1', ext: 'aar')
//For GDPR Madvertise CMP
implementation(name: 'MAdvertiseCmp-19', ext: 'aar')

```

## Version 2.14

**Important :You should note that it is mandatory that you add to your AndroidManifest.xml file:


```
#!xml

        <meta-data
            android:name="com.google.android.gms.ads.AD_MANAGER_APP"
            android:value="true"/>
```

and remove


```
#!xml

        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
```

- Infeed has fixed ratio when loading, it can be either 16:9 (MAdvertiseInfeedFrame.INFEED_RATIO_16_9) or 4:3 (INFEED_RATIO_4_3)
 you have to update your loading method to:
```java
loadInfeed(new MAdvertiseInfeedFrame(widthDP, ratio));
```

or you can use the 16:9 ratio by default:
```java
loadInfeed(new MAdvertiseInfeedFrame(widthDP));
```

replace
```groovy
implementation files('libs/amazon-ads-5.9.0.jar')
```

by

```groovy
implementation(name: 'DTBAndroidSDK-7.4.3', ext: 'aar')
```

- Don't forget to update your dependencies as following :

```groovy
implementation(name: 'DTBAndroidSDK-7.4.3', ext: 'aar')
implementation(name: 'mngads-sdk-2.14', ext: 'aar')
implementation 'com.smartadserver.android:smart-display-sdk:7.0.5@aar'
implementation 'com.adcolony:sdk:3.3.10'
implementation 'com.google.android.gms:play-services-ads:17.2.0'

//For GDPR Madvertise CMP
implementation(name: 'MAdvertiseCmp-18', ext: 'aar')

//For GPS data
implementation(name: 'madvertiselocation-2.3', ext: 'aar')
```

## Version 2.13.1
- Don't forget to update your dependencies as following :
```groovy
implementation(name: 'mngads-sdk-2.13.1', ext: 'aar')
implementation 'com.smartadserver.android:smart-display-sdk:7.0.5@aar'
implementation 'com.google.android.gms:play-services-ads:17.2.0'
```

**Important :You should note that it is mandatory that you add to your AndroidManifest.xml file:


```
#!xml

        <meta-data
            android:name="com.google.android.gms.ads.AD_MANAGER_APP"
            android:value="true"/>
```

and remove


```
#!xml

        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
```


## Version 2.13

- Don't forget to update your dependencies as following :
```groovy
implementation(name: 'mngads-sdk-2.13', ext: 'aar')
implementation 'com.smartadserver.android:smart-display-sdk:7.0.3@aar'
```

Add the following dependencies that goes along with the smart ad server

```groovy
/ Add dependencies required by Smart Display SDK
	implementation 'com.google.android.gms:play-services-ads-identifier:16.0.0'
	implementation 'com.google.android.gms:play-services-location:16.0.0'
	implementation 'com.squareup.okhttp3:okhttp:3.12.0'
```
Update Flurry's dependency

```groovy
implementation 'com.flurry.android:analytics:11.4.0@aar'
implementation 'com.flurry.android:ads:11.4.0@aar'
```

## Version 2.12.1

- Don't forget to update your dependencies as following :
```groovy
implementation(name: 'mngads-sdk-2.12.2', ext: 'aar')
implementation 'com.smartadserver.android:displaylibrary:6.10.1@aar'
```

## Version 2.12.1

- Don't forget to update your dependencies as following :
```groovy
implementation(name: 'mngads-sdk-2.12.1', ext: 'aar')
implementation 'com.google.android.gms:play-services-ads:16.0.0'
implementation 'io.vectaury.android:sdk:1.3.3'
implementation 'com.mopub:mopub-sdk:5.4.0@aar'
```

## Version 2.12

- Add implementation files('libs/omsdk-android-1.2.4-Madvertise.jar') for IAB Viewability
- Update infeed load callback to include preferredHeight:

```java

 infeedDidLoad(View view, int preferredHeightDP)
```

- You can remove the MAdvertiseConsent class usage, the consent will be automatically passed to the sdk after been saved properly in cache by the CMP.

- Don't forget to update your dependencies as following :

```groovy

implementation(name: 'mngads-sdk-2.12', ext: 'aar')
implement
ation 'com.google.android.gms:play-services-ads:15.0.1'
implementation 'com.smartadserver.android:displaylibrary:6.10.0@aar'
implementation files('libs/amazon-ads-5.9.0.jar')
implementation 'com.flurry.android:analytics:11.3.0@aar'
implementation 'com.flurry.android:ads:11.3.0@aar'
implementation('com.mopub:mopub-sdk:5.3.0@aar')
implementation(name: 'presage-moat-3.0.26-3.0.14', ext: 'aar')
implementation 'com.adcolony:sdk:3.3.5'

```

## Version 2.11.2
- Don't forget to update your dependencies as following :
```groovy
   implementation(name: 'mngads-sdk-2.11.2', ext: 'aar')
   implementation 'com.adcolony:sdk:3.3.4'
```

    - Use new mngads-sdk-x.aar, version 2.11.2
    - Use [amazon-ads-x.jar], version 5.9.0 (instead of compile 'com.amazon.android:mobile-ads:5.8.1.1' we are waiting an upgrade on Jcenter from Amazon team), this version is GDPR compliant


## Version 2.11.1
#### Release date: August 3rd, 2018

- Don't forget to update your dependencies as following :
```groovy
   implementation(name: 'mngads-sdk-2.11.1', ext: 'aar')
   implementation files('libs/amazon-ads-5.9.0.jar')
```

## Version 2.11

 - You can implement our [GDPR Madvertise CMP for Android].

 - Don't forget to update your dependencies as following :
```groovy
   implementation(name: 'mngads-sdk-2.11', ext: 'aar')
   implementation(name: 'presage-3.0.17-3.0.10', ext: 'aar')
   implementation 'io.vectaury.android:sdk:1.3.1'
   implementation 'com.mopub:mopub-sdk:5.1.0@aar'
   implementation 'com.google.android.gms:play-services-base:15.0.0'
   implementation files('libs/retency-sdk-1.0.1.jar')
```

## Version 2.10

- You can remove the proguard configuration previously made for mngads
- Update targetSdkVersion to 27, compileSdkVersion to 27
- Use MAdvertiseConsent to provide the user's concent relative to the new General Data Protection Regulation [GDPR].
- In your dependency section of your build.gradle file, change the keyword compile to implementation.

- Don't forget to update your dependencies as following :
```groovy
   implementation(name: 'mngads-sdk-2.10', ext: 'aar')
   implementation(name: 'presage-3.0.13-3.0.8', ext: 'aar')
   implementation 'com.google.android.gms:play-services-ads:15.0.0'
   implementation(name: 'SmartAdServer-Android-SDK-6.9', ext: 'aar')
   implementation 'com.facebook.android:audience-network-sdk:4.28.1'
   implementation 'com.flurry.android:analytics:10.0.0@aar'
   implementation 'com.flurry.android:ads:10.0.0@aar'
   implementation 'com.adcolony:sdk:3.3.3'
   implementation 'io.vectaury.android:sdk:1.2.0'
```

## Version 2.9.5

- Don't forget to update your dependencies as following :

```groovy

compile(name: 'mngads-sdk-2.9.5', ext: 'aar')

```

## Version 2.9.4

- Don't forget to update your dependencies as following :

```groovy
    compile(name: 'mngads-sdk-2.9.4', ext: 'aar')
    compile 'com.facebook.android:audience-network-sdk:4.28.0'
    compile 'com.flurry.android:analytics:9.0.0@aar'
    compile 'com.flurry.android:ads:9.0.0@aar'
    compile('com.mopub:mopub-sdk:4.20.0@aar')

```

## Version 2.9.3

- Don't forget to update your dependencies as following :

```groovy

compile(name: 'mngads-sdk-2.9.3', ext: 'aar')

```

## Version 2.9.2

- Don't forget to update your dependencies as following :

```groovy

compile(name: 'mngads-sdk-2.9.2', ext: 'aar')

```

## Version 2.9.1

- Don't forget to update your dependencies as following :

```groovy

compile(name: 'mngads-sdk-2.9.1', ext: 'aar')

```

## Version 2.9

- We added more callbacks to our MNGAdsSDKFactoryListener so you can handle the intialisation success, failure or reload properly. So if you are using this callback make sure that your MNGAdsSDKFactoryListener implements all the following methods:
```java
	onMNGAdsSDKFactoryDidFinishInitializing();
	onMNGAdsSDKFactoryDidFailInitialization(Exception e);
	onMNGAdsSDKFactoryDidResetConfig();
```

 - check [Native Ad Choice position] for this placement
 - Add new dependency for Mopub Marketplace
 - If you are using proguard you have to update your settings as described in our [proguard rules].

```groovy
compile('com.mopub:mopub-sdk:4.19.0@aar')
```

- Don't forget to update your dependencies as following :

```groovy
compile(name: 'mngads-sdk-2.9', ext: 'aar')
compile 'com.google.android.gms:play-services-ads:11.8.0'
compile files('libs/presage-lib-2.2.8-obfuscated.jar')
```

## Version 2.8.1

- Change your native Ad container layout to MAdvertiseNativeContainer which is a custom viewGroup that extends FrameLayout.
- registerViewForInteraction now has two arguments: your MAdvertiseNativeContainer and your callToAction view instead of only the callToAction view.

- Don't forget to update your dependencies as following :
```groovy
    compile(name: 'mngads-sdk-2.8.1', ext: 'aar')
    provided files('libs/presage-lib-2.2.7-obfuscated.jar')
    compile 'com.facebook.android:audience-network-sdk:4.27.0'
    compile 'com.flurry.android:analytics:8.2.0@aar'
    compile 'com.flurry.android:ads:8.2.0@aar'
    compile(name: 'umooveV2.12.5', ext: 'aar')
```

## Version 2.8

- Update your targetSdkVersion to 26.

- Don't forget to update your dependencies as following :
```groovy
    provided files('libs/presage-lib-2.1.17-obfuscated.jar')
    compile(name: 'SmartAdServer-Android-SDK-6.7.2', ext: 'aar')
    compile 'com.google.android.gms:play-services-ads:11.6.0'
    compile 'com.google.android.gms:play-services-location:11.6.0'
    compile 'com.android.support:support-v4:26.1.0'
    compile 'com.facebook.android:audience-network-sdk:4.26.1'
    compile 'com.flurry.android:analytics:8.1.0@aar'
    compile 'com.flurry.android:ads:8.1.0@aar'
    compile(name: 'umooveV2.12.1', ext: 'aar')
```


## Version 2.7.3

Updated dependencies :


```groovy

//madvertise mediation+adserving
compile(name: 'mngads-sdk-2.7.3', ext: 'aar')

```

 - please [configure-your-manifest] according libs in used in your application or if your app uses the GPS.

## Version 2.7.2

Updated dependencies :

```groovy
//Smart AdServer SDK
compile(name: 'SmartAdServer-Android-SDK-6.7.1', ext: 'aar')


//madvertise mediation+adserving
compile(name: 'mngads-sdk-2.7.2', ext: 'aar')

//mediation - Audience Network (Facebook)
compile 'com.facebook.android:audience-network-sdk:4.26.0'


//Google Play Services with Google Mobile Ads
compile 'com.google.android.gms:play-services-ads:11.2.2'
compile 'com.google.android.gms:play-services-location:11.2.2'
```

## Version 2.7.1

You have to manually add presage library's manifest configuration.

####AndroidManifest Configuration
#####Ogury
If you are using presage library you need to add these lines

<!-- PRESAGE LIBRARY -->
```xml
<meta-data
    android:name="presage_key"
    android:value="presage_key" />

<provider
    android:name="io.presage.provider.PresageProvider"
    android:authorities="${applicationId}.PresageProvider"
    android:enabled="true"
    android:exported="true" />

<service
    android:name="io.presage.PresageService"
    android:enabled="true"
    android:exported="true"
    android:process=":remote">
    <intent-filter>
        <action android:name="io.presage.PresageService.PIVOT" />
    </intent-filter>
</service>

<activity
    android:name="io.presage.activities.PresageActivity"
    android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
    android:hardwareAccelerated="true"
    android:label="@string/app_name"
    android:theme="@style/Presage.Theme.Transparent">
    <intent-filter>
        <action android:name="io.presage.intent.action.LAUNCH_WEBVIEW" />

        <category android:name="android.intent.category.DEFAULT" />
    </intent-filter>
</activity>

<receiver android:name="io.presage.receiver.NetworkChangeReceiver">
    <intent-filter>
        <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
        <action android:name="android.net.wifi.WIFI_STATE_CHANGED" />
        <action android:name="io.presage.receiver.NetworkChangeReceiver.ONDESTROY" />
    </intent-filter>
</receiver>
<receiver android:name="io.presage.receiver.AlarmReceiver" />

```


## Version 2.7

In this new version we managed to reduce the configuration needed to work with our sdk.
We now use, instead of a .jar file, an .aar file that includes most of the AndroidManifest.xml, proguard file and resources setup.

####AndroidManifest Configuration
#####Ogury
If you are using presage library you need to add these lines

```xml
 <!-- PRESAGE LIBRARY -->
        <!-- !!!!!! An API Key will be assigned to your application by mngads support team for Ogury library . !!!!!!-->
<meta-data
     android:name="presage_key"
     android:value="presage_key" />

<provider
    android:name="io.presage.provider.PresageProvider"
    android:authorities="${applicationId}.PresageProvider"
    android:exported="true" />
```
Adding a style for Presage library is also no longer necessary.

#####Google DFP

```xml
<meta-data
    android:name="com.google.android.gms.version"
    android:value="@integer/google_play_services_version" />
```

####Dependencies update

```groovy
//madvertise mediation+adserving
compile files('libs/mng-ads-sdk.jar')
//mediation - Audience Network (Facebook)
compile 'com.facebook.android:audience-network-sdk:4.25.0'
//mediation - Flurry
compile 'com.flurry.android:analytics:7.2.3@aar'
compile 'com.flurry.android:ads:7.2.3@aar'
//Smart AdServer SDK
compile(name: 'SmartAdServer-Android-SDK-6.7', ext: 'aar')
//mediation - ogury
compile files('libs/presage-lib-2.1.13-obfuscated.jar')

//Google Play Services with Google Mobile Ads
compile 'com.google.android.gms:play-services-ads:11.2.0'
compile 'com.google.android.gms:play-services-location:11.2.0'
```

####Note:
#####If you are using the version 11.2.0 of google play services

- *your app???s build.gradle must also be updated to specify a compileSdkVersion of at least 26 (Android O)* 

- *Dependencies of google play services are available from maven.google.com, you have to specify it in your build.gradle script as following:*

```groovy
allprojects {
    repositories {
        jcenter()
        maven {
            url "https://maven.google.com"
        }
    }
}
```

Your app???s build.gradle must also be updated to specify a compileSdkVersion of at least 26 (Android O)

Dependencies of google play services are available from maven.google.com, you have to specify it in your build.gradle script as following:

```groovy
allprojects {
    repositories {
        jcenter()
        maven {
            url "https://maven.google.com"
        }
    }
}
```


## Upgrading to 2.6


- the face tracking feature was implemented to determine wether the user is watching the ad or not , and for how long (in ms). this feature is optional and disabled by default, to enable it you need to :
- download [umooveV2.aar] library and place it in the /libs folder in your project.
- edit your build.gradle, add the library : 
```
 //face detection umoove
    compile(name: 'umooveV2', ext: 'aar')
```
- you need to declare your flat file repository.
```
allprojects {
    repositories {
        jcenter()
        flatDir{
            dirs 'libs'
        }
    }

}
```
- and you have to specify abiFilters to avoid some problems with arm64-v8a devices : add abiFilters to your build.gradle like this
```
    defaultConfig 
            {
            .
            .
            .
            ndk {
            abiFilters "armeabi-v7a","x86"
            }
        }
                    
```
- and you need to allow deprecated ndk in your gradle.properties file.
```
android.useDeprecatedNdk=true
```

- Don't forget to update following librairies :
```java
  //madvertise mediation+adserving
  compile files('libs/mng-ads-sdk.jar')
   //mediation - smart Adserver
    compile files('libs/SmartAdServer-Android-SDK-6.6.6.jar')
  //mediation - Audience Network (Facebook)
    compile 'com.facebook.android:audience-network-sdk:4.23.0'
  //mediation - Flurry
  compile 'com.flurry.android:analytics:7.1.1@aar'
  compile 'com.flurry.android:ads:7.1.1@aar'
  //mediation - ogury
    compile files('libs/presage-lib-2.1.6-obfuscated.jar')
   //Google Play Services with Google Mobile Ads only ( Individual APIs and corresponding )
    compile 'com.google.android.gms:play-services-ads:11.0.0'
    compile 'com.google.android.gms:play-services-location:11.0.0'
    //or use All Google PLay service compile 'com.google.android.gms:play-services:11.0.0'
```

## Upgrading to 2.5.2
Don't forget to update following libraries :
```
compile files('libs/mng-ads-sdk.jar')
compile files('libs/presage-lib-2.0.7-obfuscated.jar')

```


## Upgrading to 2.5.1

Don't forget to update following libraries :

 - [mng-ads.jar Android SDK]

```
compile files('libs/mng-ads-sdk.jar')
```

## Upgrading to 2.5
Dont forget to change your implementation, don't use deprecated methods. 

|Depecated method|New method|
| --- | --- |
|createBanner()|loadBanner() |
|createBanner(MNGFrame frame)|loadBanner(MNGFrame frame)  |
|createBanner(MNGPreference preference)|loadBanner(MNGPreference preference)   |
|createBanner(MNGFrame frame, MNGPreference preference)|loadBanner(MNGFrame frame, MNGPreference preference) |
|createInterstitial()|loadInterstitial()   |
|createInterstitial(boolean autoDisplay)|loadInterstitial(boolean autoDisplay)  |
|createInterstitial(MNGPreference preference)|loadInterstitial(MNGPreference preference)   |
|createInterstitial(MNGPreference preference, boolean autoDisplay)|loadInterstitial(MNGPreference preference, boolean autoDisplay)   |
|createNative()|loadNative()   |
|createNative(MNGPreference preference)|loadNative(MNGPreference preference)   |
|createNativeCollection(int requestedAdNumber)|loadNativeCollection(int requestedAdNumber)  |
|createNativeCollection(int requestedAdNumber, MNGPreference preference)|loadNativeCollection(int requestedAdNumber, MNGPreference preference)   |
|createInfeed()|loadInfeed() |
|createInfeed(MNGFrame frame)|loadInfeed(MNGFrame frame) |
|createInfeed(MNGPreference preference)|loadInfeed(MNGPreference preference) |
|createInfeed(MNGFrame frame, MNGPreference preference)|loadInfeed(MNGFrame frame, MNGPreference preference) |



Don't forget to update following libraries :
```
compile files('libs/mng-ads-sdk.jar')
compile 'com.facebook.android:audience-network-sdk:4.21.1'
compile files('libs/SmartAdServer-Android-SDK-6.6.5.jar')
compile 'com.flurry.android:analytics:7.0.0@aar'
compile 'com.flurry.android:ads:7.0.0@aar'
compile(name: 'b4s-android-sdk', ext: 'aar')
compile files('libs/presage-lib-2.0.5-obfuscated.jar')

```
For flurry users, change your dependencies from JAR to AAR
remove this lines :
```
compile 'com.flurry.android:analytics:6.9.1'
compile 'com.flurry.android:ads:6.9.1'
```
add this lines : 
```
compile 'com.flurry.android:ads:7.0.0@aar'
compile(name: 'b4s-android-sdk', ext: 'aar')
```


## Upgrading to 2.4
Don't forget to update following libraries :
```
 compile files('libs/mng-ads-sdk.jar')
 compile 'com.facebook.android:audience-network-sdk:4.20.0'
 compile 'com.flurry.android:analytics:6.9.1'
 compile 'com.flurry.android:ads:6.9.1'
 compile files('libs/SmartAdServer-Android-SDK-6.6.3.jar')
 compile files('libs/presage-lib-2.0.2-obfuscated.jar')

```
For **Ogury integration**, Add these lines in your build.gradle
```
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
Tracking, shortcut and boot permissions aren't required so you can remove them from manifest.xml
   
   ```xml
   <!--remove these lines if you don't use them in your app -->
   <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
    <uses-permission android:name="com.android.browser.permission.WRITE_HISTORY_BOOKMARKS" />
    <uses-permission android:name="com.android.launcher.permission.INSTALL_SHORTCUT" />
   ```
BootReceiver is deleted, so remove it from you manifest.xml
   ```xml
     <!--remove the BootReceiver-->
        <receiver android:name="io.presage.receivers.BootReceiver">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.intent.action.DATE_CHANGED" />
                <action android:name="io.presage.receivers.BootReceiver.RESTART_SERVICE" />
            </intent-filter>
        </receiver>
```
Add NetworkChangeReceiver, AlarmReceiver and persageProvider in your manifest.xml
```xml
      <receiver android:name="io.presage.receiver.NetworkChangeReceiver">
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
                <action android:name="android.net.wifi.WIFI_STATE_CHANGED" />
                <action android:name="io.presage.receiver.NetworkChangeReceiver.ONDESTROY" />
            </intent-filter>
        </receiver>
        <receiver android:name="io.presage.receiver.AlarmReceiver" />
        <provider
            android:name="io.presage.provider.PresageProvider"
            android:authorities="${applicationId}.PresageProvider"
            android:enabled="true"
            android:exported="true" />
```
Perasage Service declaration is changed, so try to remove 
```xml
        <service android:name="io.presage.services.PresageServiceImp" />
```

and add these lines
```xml
  <service
            android:name="io.presage.PresageService"
            android:enabled="true"
            android:exported="true"
            android:process=":remote">
            <intent-filter>
                <action android:name="io.presage.PresageService.PIVOT" />
            </intent-filter>
        </service>
```


###Upgrading to 2.3.3

You must update :
```
compile files('libs/mng-ads-sdk.jar')

 //mediation - smart Adserver
compile files('libs/SmartAdServer-Android-SDK-6.6.2.jar')
 
//mediation - Audience Network (Facebook)
compile 'com.facebook.android:audience-network-sdk:4.19.0'

//mediation - Flurry
compile 'com.flurry.android:analytics:6.8.0'
compile 'com.flurry.android:ads:6.8.0'

//mediation - b4s - beacons support
 compile 'nl.qbusict:cupboard:2.1.4'
 compile 'de.greenrobot:eventbus:2.4.0'
 compile 'com.squareup.retrofit2:converter-jackson:2.0.0'
 compile(name: 'b4s-android-sdk', ext: 'aar')
 compile(name: 'b4s-android-sdk-playservices830', ext: 'aar')

 //mediation - ogury
 compile files('libs/presage-lib-1.8.3.jar')

```

###Upgrading to 2.3.2

You must update :
```
compile files('libs/mng-ads-sdk.jar')
compile files('libs/SmartAdServer-Android-SDK-6.6.jar')
compile 'com.google.android.gms:play-services-ads:10.0.1'
compile 'com.google.android.gms:play-services-location:10.0.1'
compile 'com.flurry.android:analytics:6.7.0'
compile 'com.flurry.android:ads:6.7.0'
compile 'com.facebook.android:audience-network-sdk:4.18.0'
```

###Upgrading to 2.3


Don't forget to update following libraries :

```

    compile 'com.amazon.android:mobile-ads:5.8.1.1'
    compile files('libs/SmartAdServer-Android-SDK-6.4.1.jar')
    compile 'com.flurry.android:analytics:6.6.0'
    compile 'com.flurry.android:ads:6.6.0'
    compile 'com.facebook.android:audience-network-sdk:4.16.1'  
    compile 'com.google.android.gms:play-services-ads:9.8.0'
        
```

For  Ebeacon technology withB4S , you must add following libraries

```
       //b4s
    compile 'nl.qbusict:cupboard:2.1.4'
    compile 'de.greenrobot:eventbus:2.4.0'
    compile 'com.squareup.retrofit2:converter-jackson:2.0.0'
    compile(name: 'b4s-android-sdk', ext: 'aar')
    compile(name: 'b4s-android-sdk-playservices830', ext: 'aar')
```
#### Native Ad

you dont have to download assets, the sdk will do it.

```
 nativeObject.downloadAssetsForType(mMAdvertiseType,mImageView);
```

## Upgrading to 2.1.1

 - Flurry as gradle dependency

remove  
```
#!groovy
repositories {
compile files('libs/flurryAds-6.3.1.jar')
compile files('libs/flurryAnalytics-6.3.1.jar')
```

add
```
#!groovy
repositories {
 //Flurry
  compile 'com.flurry.android:analytics:6.3.1'
  compile 'com.flurry.android:ads:6.3.1'
```


## Upgrading to 2.1
### New features
Now you can create an [In-Feed Ad format]

```
#!java

public boolean createInfeed() 

public boolean createInfeed(MNGFrame frame) 

public boolean createInfeed(MNGPreference preference)

public boolean createInfeed(MNGFrame frame, MNGPreference preference)

```
### libraries

 - The following libraries are not required anymore for the sdk

      - [Liverail.jar]


 - amazon as gradle dependency

remove  
```
#!groovy
repositories {
compile files('amazon-ads-5.6.20.jar')
```

add
```
#!groovy
repositories {
compile 'com.amazon.android:mobile-ads:5.7.2'
```



 - Don't forget to update following libraries :
    - [mng-ads.jar Android SDK]
    - [AudienceNetwork.jar]  (com.facebook.android:audience-network-sdk:4.12.1)
    - [FlurryAds.jar] and [FlurryAnalytics.jar]

## Upgrading to 2.0.8
### New features
Now you can disable [interstitial auto-displaying] 
interstitial


```
#!java

public boolean createInterstitial() 

public boolean createInterstitial(boolean autoDisplay) 

public boolean createInterstitial(MNGPreference preference) 

public boolean createInterstitial(MNGPreference preference, boolean autoDisplay) 

public boolean isInterstitialReady()

public boolean displayInterstitial()
```


### libraries
Don't forget to update the other libraries :
- [SmartAdServer-Android-SDK.jar]

## Upgrading to 2.0.5
### Implementation

The MNGNativeObject registerViewForInteraction methode now accapte only Button , TextView or ImageView instead of View as a parameter

```
#!java


public void registerViewForInteraction(Button adClickButton)

public void registerViewForInteraction(TextView adClickTextView)

public void registerViewForInteraction(ImageView adClickImageView)
```



see https://bitbucket.org/mngcorp/mngads-demo-android/wiki/nativead#markdown-header-5-v25-or-above

## Upgrading to 2.0.4
MNG Ads requires minimum Android API level 11


Contact mngads support to get presage API key .

### libraries
#### Added

The following librairie is required for the sdk

 - [Presage-lib.jar]

Don't forget to update the other libraries :

- [SmartAdServer-Android-SDK.jar]
 
### AndroidManifest.xml
#### Added

```
#!xml
<manifest
...
    <!-- Grants the SDK permission to receive the ACTION_BOOT_COMPLETED that is broadcast after the system finishes booting. -->
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <!--Grants the SDK permission to create windows using the type TYPE_SYSTEM_ALERT, shown on top of all other apps.-->
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <!--Tracking permissions -->
    <uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
    <uses-permission android:name="com.android.browser.permission.WRITE_HISTORY_BOOKMARKS" />
    <!--Shortcut permissions -->
    <uses-permission android:name="com.android.launcher.permission.INSTALL_SHORTCUT" />
    <uses-permission android:name="com.android.launcher.permission.UNINSTALL_SHORTCUT" />
... 

<application
 ...
 <!-- PRESAGE LIBRARY -->
        <!-- !!!!!! An API Key will be assigned to your application by mngads support team for Ogury library . !!!!!!-->
        <meta-data android:name="presage_key" android:value="presage_key"/>
        <service android:name="io.presage.services.PresageServiceImp" />
        <activity
            android:name="io.presage.activities.PresageActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
            android:hardwareAccelerated="true"
            android:label="@string/app_name"
            android:theme="@style/Presage.Theme.Transparent" >
            <intent-filter>
                <action android:name="io.presage.intent.action.LAUNCH_WEBVIEW" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
        <receiver android:name="io.presage.receivers.BootReceiver" >
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.intent.action.DATE_CHANGED" />
                <action android:name="io.presage.receivers.BootReceiver.RESTART_SERVICE" />
            </intent-filter>
        </receiver>
 ...
```

### Styles
If you have styles.xml inside res/values folder, copy the following lines inside else, create styles.xml inside res/values folder with these lines inside:
```
#!XML
<style name="Presage.Theme.Transparent" parent="android:Theme">
    <item name="android:windowIsTranslucent">true</item>
    <item name="android:windowBackground">@android:color/transparent</item>
    <item name="android:windowContentOverlay">@null</item>
    <item name="android:windowNoTitle">true</item>
    <item name="android:backgroundDimEnabled">false</item>
</style>
```
## Upgrading to 2.0

MNG Ads requires minimum Android API level 10

### libraries
#### Removed

The following libraries are not required any more for the sdk

 - afAdSdk.jar
 - mngperf-android-sdk.jar
 - AppNexus-sdk

#### Added

The following libraries are required for the sdk

- [Amazon.jar]
- [Liverail.jar]
- [FlurryAds.jar] and [FlurryAnalytics.jar]

Don't forget to update the other libraries :

- Google-play-services_lib (com.google.android.gms:play-services:8.4.0)
- [SmartAdServer-Android-SDK.jar]
- [AudienceNetwork.jar]
- [Android-support-v4.jar]
- [Retency-sdk]

### AndroidManifest.xml
#### Removed

```
#!xml

<application
 ...
<!--appNexus SDK Ad activity  -->
    <activity 
        android:name="com.appnexus.opensdk.AdActivity"/>    <!-- to display this activity in fullscreen mode :  android:theme="@android:style/Theme.Light.NoTitleBar" -->
    <!--mngPref SDK Ad activitys  -->
    <activity
            android:name="com.adsdk.sdk.banner.InAppWebView"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    <activity
            android:name="com.adsdk.sdk.video.RichMediaActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:hardwareAccelerated="true" />
    <activity
            android:name="com.adsdk.sdk.mraid.MraidActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    <activity
            android:name="com.adsdk.sdk.mraid.MraidBrowser"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    ...
```
#### Added

```
#!xml
<manifest
...
 <!-- External storage is used for pre-caching features if available -->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
...

 <application
 ...
        <!--MNG Ad server activity -->
        <activity
            android:name="com.mngads.sdk.MNGInAppWebView"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
        <activity
            android:name="com.mngads.sdk.interstitial.MNGInterstitialAdActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
        <activity
            android:name="com.mngads.sdk.MNGVideoPlayerActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />

        <activity
            android:name="com.mngads.sdk.nativead.MNGNativeAdActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
          
        <!--Amazon SDK Ad activity  -->
        <activity
            android:name="com.amazon.device.ads.AdActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"/>

        <!--Flurry SDK Ad activity  -->
        <activity
            android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
    ...
```

 ### Implementation
You can also integrate video ads into your Native Ad experience by calling setMediaContainer(mediaViewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result
```
#!java
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
    ...
    String title=nativeObject.getTitle();
    String body=nativeObject.getBody();
    String callToAction=nativeObject.getCallToAction();
    String price=nativeObject.getPriceText();
    Bitmap badge=nativeObject.getBadge();
    
    String iconUrl=nativeObject.getAdIconUrl();
   // String coverImageUrl=nativeObject.getAdCoverImageUrl();
   //  there is no need to use coverurl
   nativeObject.setMediaContainer(mediaViewGroup);
    
    //to handle impression and user interaction you have to call 
    nativeObject.registerViewForInteraction(nativeAdCallToActionView);
   ...
}
```
## Upgrading to 1.5.1
The following method have been changed. int preferredHeightDP is now available to more easily resize banners.

```
#!java
 /**
     * Notifies the Listener that the creative from the banner ad had been
     * loaded.
     * @param adView 
     * @param Ad preferredHeightDP this value is in dp
     */
    public void bannerDidLoad(View adView ,int preferredHeightDP);
```
instead of
```
#!java
   /**
     * Notifies the Listener that the creative from the banner ad had been
     * loaded.
     * @param adView 
     */
    public void bannerDidLoad(View adView);
```
The following methode was added to the banner listener
```
#!java
   /**
     * Notifies the listener that the creative from the banner ad had been
     * resized.
     * @param frame Ad frame size width  dp , height dp
     */
    public void bannerResize(MNGFrame frame);
```
##### Note : it's preferable to adjust the ad container view size to match the returned Ad size for a better display.

## Upgrading to 1.3.1

 - You must add [retency-sdk]
 - Update AndroidManifest.xml

```
#!XML
    ...
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    ...
    <!--Grants the SDK permission to start mng analytics service -->
    <service android:name="com.mngads.service.MNGAnalyticsService"/>
    ...
    <!--Retency SDK Ad activitys  -->
    <activity android:name="com.retency.sdk.android.banner.InAppWebView"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|u Mode|screenSize|smallestScreenSize" />
    <activity android:name="com.retency.sdk.android.video.RichMediaActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:hardwareAccelerated="false" />
    <activity android:name="com.retency.sdk.android.mraid.MraidBrowser"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    ...
```

## Upgrading to 1.2.5

You must add **AppNexus-sdk** 

## Upgrading from 1.1 to 1.2

New method for carousel can be used, see [Ad Examples]

To make a request you have to call 'createNativeCollection(int requestedAdNumber)'. this method return a bool value (canHandleRequest) 

```
#!java
if(mngAdsNativeAdsFactory.createNativeCollection(int requestedAdNumber){
//Wait callBack from native listener
}else{
//adsFactory can not handle your request
}
```

## Upgrading from 1.0 to 1.1

No special steps are required to upgrade to v1.1.



[Ad Examples]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/inspiration
[Retency-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/retency-sdk.jar?at=master
[link]:https://developer.android.com/training/location/retrieve-current.html
[Smart ads server]:http://help.smartadserver.com/fr/Default.htm#../../../../specifications/Content/MobileSpecifications/Apps.htm
[Mng-perf]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mngperf-android-sdk.jar?at=master
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mng-ads.jar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mng-ads-sdk.jar?at=master
[MngAds sample app]:https://bitbucket.org/mngcorp/mngads-demo-android/src
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
[Change Log]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/change-log
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/AudienceNetwork.jar?at=master
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[SmartAdServer-Android-SDK.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[mngAds state diagram]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/diagram
[Retency]:http://www.retency.com/public/
[Retency-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/retency-sdk.jar?at=master
[Amazon]:https://developer.amazon.com/public/resources/development-tools/sdk
[Liverail]:https://platform4.liverail.com
[Flurry]:https://developer.yahoo.com/flurry/
[Amazon.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Liverail.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[FlurryAds.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[FlurryAnalytics.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Best practice Mngads and Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[AndroidMultidex]:http://developer.android.com/intl/ko/tools/building/multidex.html
[Native Ads guidelines]:../nativead
[presage-lib.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/presage-lib-1.7.2.jar?fileviewer=file-view-default
[interstitial auto-displaying]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-disable-auto-displaying
[In-Feed Ad format]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-infeed
[umooveV2.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/umooveV2.aar?at=master&fileviewer=file-view-default
[Wiki]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home
[configure-your-manifest]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-configure-your-manifest
[Native Ad Choice position]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/nativead#markdown-header-customize-native-ad-adchoice
[proguard rules]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-if-your-app-uses-proguard-you-must-edit-your-proguard-settings-to-avoid-stripping-google-play-out-of-your-app
[GDPR]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/gdpr
[GDPR Madvertise CMP for Android]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home
[omsdk-android-x-Madvertise.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[madvertiselocation-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[MAdvertiseCmp-xx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/