# upgrading SDK
**You need to keep all Ad Network jars up to date.**


## Version 2.7
#### Release date: August 25th, 2017

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

- *your app’s build.gradle must also be updated to specify a compileSdkVersion of at least 26 (Android O)* 

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

Your app’s build.gradle must also be updated to specify a compileSdkVersion of at least 26 (Android O)

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