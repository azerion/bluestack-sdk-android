## Change log and release notes for the MngAds SDK for Android.
See [Wiki], [Design Guidelines and Best practices] and [Help Center]  for more detailed informations

you must check [Upgrade Guide]. You need to keep all Ad Network jars/aar up to date. 

## Version 3.6.1
#### Release date: June 25th, 2021

**Fixed**

 - crash WebView cannot be initialized on a thread that has no Looper. at com.mngads.sdk.perf.g.b.a(:49)

**Updated SDKs**

- Use new version of BlueStack Mediation SDK (Version : 3.6.1)

## Version 3.6.0
#### Release date: June 18th, 2021

**New features**

 - Add Support of Semantic link.

**Fixed**

 - Issue with VAST trackings.
 - Issue with Viewability enhancement.
 - Issue with MRAID View cause a crash (com.mngads.sdk.perf.f.c.a) 

**Updated SDKs**

- Use new version of BlueStack Mediation SDK (Version : 3.6.0)
- Use new version of BlueStack CMP SDK (Version : 59.0.0) 
- Use new version of Google Ads SDK (Version : 20.1.0) 
- Use new version of Audience Network SDK (Version : 6.5.0)  
- Use new version of Smart Ad Server SDK (Version : 7.12.0)
- Use new version of Amazon APS SDK (Version : 9.0.0)  
- Use new version of Ogury SDK (Version : 5.0.9) + BlueStack Ogury Mediation SDK (Version : 1.1.0) 
- Use new version of AdColony SDK (Version : 4.5.0) + BlueStack Adcolony Mediation SDK (Version : 1.1.0) 
- Use new version of Criteo SDK (Version : 4.4.0) + BlueStack Criteo Mediation SDK (Version : 1.1.0) 



## Version 3.5.0
#### Release date: April 26th, 2021

**New features**

 - In order to avoid reference of unused mediation adapter on https://exodus-privacy.eu.org/en/, we are using separate adaptor and Android Reflexion.Do not forget to add com.madvertise:bluestack-mediation-[ADAPTER_NAME] aar on your build.gradle file.
 - Implement new major Google version (v20).

**Improvements**

 - Clean TCF v1 management
 - Capping optimization



**Fixed**

 - Issue with isLimitAdTrackingEnabled.
 - Issue with some interstitial creatives were not properly displayed.
 - Issue with interstitial ad cause a crash (com.mngads.sdk.perf.f.c.a).
 - Issue with native ad cause a crash (android.view.ViewGroup.removeAllViews()).

**Updated SDKs**

- Use new version of BlueStack Mediation SDK (Version : 3.5.0)
- Use new version of BlueStack CMP SDK (Version : 57.0.0) 
- Use new version of BlueStack Location SDK (Version : 4.0.0) 
- Use new version of Google Ads SDK (Version : 20.0.0) 
- Use new version of Sync SDK (Version : 3.2.1)  
- Use new version of Audience Network SDK (Version : 6.4.0)  
- Use new version of Amazon APS SDK (Version : 8.4.3)  
- Use new version of Ogury SDK (Version : 5.0.8) + BlueStack Ogury Mediation SDK (Version : 1.0.0) 
- Use new version of AdColony SDK (Version : 4.4.1) + BlueStack Adcolony Mediation SDK (Version : 1.0.0) 
- Use new version of Criteo SDK (Version : 4.3.0) + BlueStack Criteo Mediation SDK (Version : 1.0.0) 
- Use new version of MoPub SDK (Version : 5.13.1) + BlueStack MoPub Mediation SDK (Version : 1.0.0) 
- Use new version of Applovin SDK (Version : 9.13.0) + BlueStack Applovin Mediation SDK (Version : 1.0.0) 

## Version 3.4.0
#### Release date: January 22th, 2021

**New features**

- New ad format: 
     - [Thumbnail Ad] For Ogury SDK.
      - Added [Sync Display SDK] for mediation 
- Support of Facebook Audience Network bidding for in-app ads.

**Improvements**

 - The SDK is now compatible and certified for IAB Open Measurement SDK  1.3.15.
 - Improve SDK performance and stability.

**Fixed**

 - Issue with ad choice view cause a crash (com.mngads.sdk.perf.request.L)
 - Issue with native ad cause a crash (com.mngads.c.e.a) 
 - Issue with close button cause a crash (com.mngads.sdk.perf.b.c.initCloseableContainer) 
 - Issue with tracking script cause a crash (com.mngads.MNGAdsFactory.eventEnd)  

**Updated**

- Upgarde SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.4.0)
    - Use new version of BlueStack CMP SDK (Version : 55) 
    - Use new version of Google Ads SDK (Version : 19.6.0) 
    - Use new version of Ogury SDK (Version : 5.0.5) 
    - Use new version of Smart Ad Server SDK (Version : 7.8.1)
    - Use new version of AdColony SDK (Version : 4.3.1)
    - Use new version of Criteo SDK (Version : 4.2.1)
    - Use new version of Sync SDK (Version : 3.2.0)

## Version 3.3.6
#### Release date: January 08th, 2021

**Fixed**

 - Fixed an issue with Appsfire Badge cause a crash (android.content.res.Resources$NotFoundException).

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.5)
    - Use new version of BlueStack CMP SDK (Version : 54.0.0)

## Version 3.3.5
#### Release date: December 24th, 2020

**Fixed**

 - rewardVideo: now Timer start on video start event for VAST / VPAID / video

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.5)


## Version 3.3.4
#### Release date: December 17th, 2020

**Improvements**

 - All SDK classes are now compiled using AndroidX libraries.
 - Added isRewardedVideoReady() to check the current status of a rewarded video. 

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.4)
    - Use new version of BlueStack CMP SDK (Version : 51.0.0) 
    - Use new version of BlueStack Location SDK (Version : 3.2.5)

## Version 3.3.3
#### Release date: November 6th, 2020

**Fixed**

 - Fixed an issue with Renderscript. 
 - Fix smartAdserver crash (SASBiddingManager 7.6.1 on Android 11)

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.3)
    - Use new version of BlueStack CMP SDK (Version : 49) 
    - Use new version of Google Ads SDK (Version : 19.5.0) 
    - Use new version of Audience Network SDK (Version : 6.2.0)
    - Use new version of Ogury SDK (Version : 5.0.3) 
    - Use new version of Smart Ad Server SDK (Version : 7.6.2)
    - Use new version of AdColony SDK (Version : 4.3.0)
    - Use new version of Amazon APS SDK (Version :  8.4.1)

## Version 3.3.2
#### Release date: October 26th, 2020

**Fixed**

 - Fixed a crash with video (wrong method between Bluestack and appLovin)

## Version 3.3.1
#### Release date: October 22th, 2020

**Fixed**

 - Fixed an issue with debug mode cause a crash (com.mngads.util.j.a). 
 - Fixed an issue with MRAID Video cause a crash (com.mngads.sdk.perf.video.util.b.c)

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.1)
    - Use new version of BlueStack CMP SDK (Version : 48)

## Version 3.3.0
#### Release date: October 20th, 2020

**New features**

- New ad format: RewardVideo For BlueStack Ads.

**Improvements**

 - Update Open Measurement SDK to version 1.3.11.

**Fixed**

 - Fix com.mngads.sdk.perf.g.b.a crash (Webview)
 - Fix com.mngads.sdk.perf.interstitial.MNGInterstitialAdActivity crash
 - Fix chromium-TrichromeWebViewGoogle crash (Facebook)


**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.3.0)
    - Use new version of BlueStack CMP SDK (Version : 46)
    - Use new version of Google Ads SDK (Version : 19.4.0) 
    - Use new version of Audience Network SDK (Version : 6.1.0)
    - Use new version of Ogury SDK (Version : 5.0.2) 
    - Use new version of Criteo SDK (Version : 3.10.1) 

## Version 3.2.5
#### Release date: October 8th, 2020

 - Change maven option for implementation 'com.madvertise:bluestack-core-sdk:3.2.5',do not download automatically all mediation dependencies.


## Version 3.2.4
#### Release date: September 24th, 2020

**Fixed**

 - Fix AdChoices issue for nativeAd
 - Fix NativeAd Bitmap issue

**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.2.4)

## Version 3.2.3
#### Release date: September 18th, 2020

**Improvements**

 - SDK is now delivered through Maven/Bitbucket repository.
 - Improve SDK performance and stability.
 
**Updated**

- Upgrade SDKs : 
    - Use new version of BlueStack Mediation SDK (Version : 3.2.3)
    - Use new version of BlueStack CMP SDK (Version : 42)
    - Use new version of BlueStack Location SDK (Version : 3.2.3)


## Version 3.2.2
#### Release date: September 10th, 2020

**Fixed**

 - Fix ANR issues
 - Fix TCF v2 issue for GAID
 
**Updated**

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.2.2)
    - Use new version of Google Ads SDK (Version : 19.3.0) 
    - Use new version of Play Services SDK (Version : 17.4.0) 
    - Use new version of Audience Network SDK (Version : 5.11.0) 
    - Use new version of Smart Ad Server SDK (Version : 7.6.1)
    - Use new version of Criteo SDK (Version 3.9.0) 
    - Use new version of Ogury SDK (Version : 4.8.3) 
    - Use new version of Amazon APS SDK (Version : 8.3.2)  
    - Use new version of Madvertise CMP SDK [madvertisecmp-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/) (Version : 41)



## Version 3.2.0
#### Release date: July 23th, 2020

**New features**

 - New adUnit (Banner Ad) for Ogury SDK.
 - Support for GDPR TCF v2
 - Minimisation of collected data according user consent

**Fixed**

 - Fixed an issue where clicking close Appearance Delay.
 - Improve SDK performance and stability.
 
**Updated**

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.2.0)
    - Use new version of Criteo SDK (Version 3.7.0) 
    - Use new version of Ogury SDK (Version : 4.8.1) 
    - Use new version of MoPub SDK (Version : 5.13.1)
    - Use new version of Google Ads SDK (Version : 19.2.0) 
    - Use new version of Play Services SDK (Version : 17.3.0) 
    - Use new version of Audience Network SDK (Version : 5.9.1)  
    - Use new version of Madvertise CMP SDK [madvertisecmp-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/) (Version : 41)
    - Use new version of Madvertise Location SDK [madvertiselocation-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/) (Version : 3.2.2)


## Version 3.1.4
#### Release date: June 26th, 2020

**Fixed**

 - fix issue on com.mngads.sdk.nativead.MNGNativeAd.getAdChoiceView
 - Fix crash VPAID (wrong method between Bluestack and appLovin)

**Updated**

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.1.4)

## Version 3.1.3
#### Release date: May 25th, 2020

**Improvements**

 - Improve SDK stability.

**Updated**

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.1.3)
    - Use new version of Ogury SDK (Version : 4.7.0) 
    - Use new version of Smart Ad Server SDK (Version : 7.6.0)
    - Use new version of Audience Network SDK (Version : 5.9.0)
    - Use new version of Madvertise Location SDK [madvertiselocation-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/), (Version : 3.1)


## Version 3.1.2
#### Release date: May 12th, 2020

**Improvements**

 - Improve SDK stability.

**Fixed**
 - Fix smartAdserver crash SCSUtil.getAdvertisingID

**Updated**

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.1.2)
    - Use new version of Google Ads SDK (Version : 19.1.0) 
    - Use new version of Smart Ad Server SDK (Version : 7.4.1) 
    - Use new version of Criteo SDK (Version 3.5.0) 

## Version 3.1.1
#### Release date: May 5th, 2020

**Added**

 - Change interstitial behavior on click event.


- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.1.1)


## Version 3.1.0
#### Release date: April 28th, 2020

**Added**

- Add support for the Transparency and Consent Framework V2 (accept TCF v2 consentString https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-is-the-cmp-in-app-internal-structure-for-the-defined-api).
- Native Ad performances.

**Updated**

- IAB Open Measurement SDK updated to version 1.3.1.

- Upgrade mediation SDKs : 
    - Use new version of MNG Ads SDK (Version : 3.1.0)
    - Use new version of Ogury SDK (Version : 4.3.12) 
    - Use new version of Smart Ad Server SDK (Version : 7.4.1) 
    - Use new version of MoPub SDK (Version : 5.11.1) 
    - Use new version of AppLovin SDK (Version : 9.11.6) 
    - Use new version of AdColony SDK (Version : 4.1.4) 
    - Use new version of Google Ads SDK (Version : 19.0.1) 
    - Use new version of Audience Network SDK (Version : 5.8.0) 



## Version 3.0.2
#### Release date: March 19th, 2020

**Added**

 - Manage placement stack

**Fixed**

 - Fix SASWebView.java line 60 crash onSmartAdserver (android 5 and low cost devices)

**Updated**

 - Use new version of MNG Ads SDK (Version : 3.0.2)


## Version 3.0.1
#### Release date: March 12th, 2020

**Added**

 - Interstitial performances

**Fixed**

 - fix MNGAnalyticsService crash
 - fix Binder.java - android.os.BinderProxy.transactNative. - TransactionTooLargeException crash

**Updated**

 - Use new version of MNG Ads SDK (Version : 3.0.1)

## Version 3.0
#### Release date: February 18th, 2020

**"It’s required that your project migrates from Android Support Libraries to Jetpack Libraries (Android X) if you are using this version."**

**Added**

 - In-App Bidding feature.
 - Support for Parallax on Infeed format.
 - Fully compatible with [Android X].

**Fixed**

- Fixed an issue in VPAID player.
- Fixed an issue where clicking a close button on MRAID Ad.
- Fixed an issue related to MNGAnalyticsService.


**Updated**

- Updated mediation to support latest SDKs of every network : 
    - Added Criteo SDK (Version 3.4.0) 
    - Replace Amazon Ads SDK from "amazon-ads-X.X.X.jar" or "DTBAndroidSDK-X.X.X.aar" to 'com.amazon.android:aps-sdk:8.2.1@aar'
    - Use new version of MNG Ads SDK (Version : 3.0)
    - Use new version of Ogury SDK (Version : 4.1.10) 
    - Use new version of Flurry SDK (Version : 12.1.0) 
    - Use new version of Smart Ad Server SDK (Version : 7.4.0) 
    - Use new version of MoPub SDK (Version : 5.11.0) 
    - Use new version of AppLovin SDK (Version : 9.11.2) 
    - Use new version of AdColony SDK (Version : 4.1.3) 
    - Use new version of Google Ads SDK (Version : 18.3.0) 


## Version 2.16
#### Release date: February 4th, 2020

- **Bug Fixes**

 - Fix Native Ad issue (icon)

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.16
    - Use new "com.facebook.android:audience-network-sdk:5.6.1"

## Version 2.15.2
#### Release date: November 4th, 2019

- **Bug Fixes**

 - fix nativeAd issue (com.google.android.gms.ads.formats.NativeAd$Image.getDrawable())

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.15.2
    - Use new  [madvertiselocation-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/), version 2.8

## Version 2.15.1
#### Release date: October 16th, 2019
- **Features**

     - Support 64-bit architectures.

- **Bug Fixes**

	- Fixed auto refresh issue for appsfire.
	- NativeAd: Put **null** to hide icon (instead of iconImageView) or image cover (instead of mediaViewGroup).

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.15.1

## Version 2.15
#### Release date: September 25th, 2019
- **Features**
    - Upgrade version 1.2.19 of Open Measurement SDK (Viewability), include by default on mngads-sdk-x.aar
    - Support Android 10.
    - Added AppLovin SDK for mediation.
    - Added support for VAST 4.2.
    - Support ImageView for NativeAd's ad for Facebook Audience Network .
	- Upgraded min sdk version to 19, buildToolVersion to 28.0.3.
    - New Demo BlueStack Demo app
- **Bug Fixes**
	- Appsfire templates changes (button background color, square icon position).
	- Fixed auto refresh issue for amazon APS.
	- Improving capping functionality.
    - Open Measurement SDK version in debug gyro popup.

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.15
    - Use new  [madvertiselocation-x.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/), version 2.5
    - Use new [MAdvertiseCmp-xx.aar], version 22
    - Use new “com.smartadserver.android:smart-display-sdk:7.2.0@aar”
    - Use new "com.mopub:mopub-sdk:5.8.0@aar" 
    - Use new "com.adcolony:sdk:4.1.0" 
    - Use new "com.facebook.android:audience-network-sdk:5.5.0"
    - Use new "ogury-4.1.4.aar"
    - Use new "DTBAndroidSDK-8.0.0.aar" (Amazon)

## Version 2.14.1
#### Release date: July 23th, 2019

- **Features**
	- Blocked the following ad networks when they are disabled by cmp: Facebook Audience, Amazon Publisher Service (require [MadvertiseCMP v19](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/) ).
    - Blocked retency when it is disabled by cmp (require [MadvertiseCMP v19](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/) ).

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.14.1

## Version 2.14
#### Release date: June 25th, 2019

- **Features**
	- New AmazonAPS mediation adapter.
    - Fresh initialization after an update of the sdk.
    - Infeed loading method changed, see more in upgrading guide.
    - Infeed is available for dfp ads.
    - Infeed's ad view ratio is fixed to 16:9 or 4:3
    - Viewability feature to track how much of the ad had been seen.
    - Enabling debug MAdvertiseLocation sdk along with the MAdvertise SDK.

- **Bug Fixes**
    - Fixed returning to forground after opening external url.
    - Fixed wrong banner size for some ads.
    - Fixed accelometer initialization issue.
    - Fixed http call not permitted.
    - Fixed Appsfire's video becoming black.

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.14
    - Use new "com.smartadserver.android:smart-display-sdk:7.0.5@aar"
    - Use new "com.google.android.gms:play-services-ads:17.2.1"
    - Use new "com.adcolony:sdk:3.3.10"
    - Use new [madvertiselocation-x.aar], version 2.3
    - Use new [MAdvertiseCmp-xx.aar], version 18
    - Use new [Amazon-APS], version 7.4.3, [AmazonPublisherService](https://bitbucket.org/mngcorp/mngads-demo-android/wiki/AmazonPublisherService)


## Version 2.13.1
#### Release date: May 24th, 2019

- **Bug Fixes**

     - Fix potential application crash when migrating to 7.x from 6.x due to obsolete cache files for smartAdserver SDK
     - Fix potential Native crash for smartAdserver

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.13.1
    - Use new com.smartadserver.android:smart-display-sdk:7.0.5@aar
    - Use new com.google.android.gms:play-services-ads:17.2.0

**Important :You should note that it is mandatory that you add to your AndroidManifest.xml file:**


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
#### Release date: February 14th, 2019

- **Features**
    - Management of the banner's undefined height error.

- **Bug Fixes**
    - Fixed flurry native ad error.
    - Fixed the banner's undefined height error.

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.13
    - Use new com.smartadserver.android:smart-display-sdk:7.0.3@aar (check upgradind guide)
    - Use new com.flurry.android:analytics:11.4.0@aar
    - com.flurry.android:ads:11.4.0@aar


## Version 2.12.2
#### Release date: December 17th, 2018

- **Features**
    - Updated tracking events' management.

- **Bug Fixes**
    - Fixed recycled bitmap error.
    - Fixed OnAdClicked not been called for certain adServers.
    - Fixed Smart AdServer SDK Vulnerability


- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.12.2
    - Use new com.smartadserver.android:displaylibrary:6.10.1@aar


## Version 2.12.1
#### Release date: October 31th, 2018

- **Features**
    - Changed mopub adChoice's size.

- **Bug Fixes**
    - Fixed recycled bitmap error.
    - Fixed OnAdClicked not been called for smartAdserver.

- **Ad Network Mediation Updates**
    - Use new mngads-sdk-x.aar, version 2.12.1
    - Use new com.google.android.gms:play-services-ads:16.0.0
    - Use new com.mopub:mopub-sdk:5.4.0@aar
    - Use new io.vectaury.android:sdk:1.3.3


## Version 2.12
#### Release date: October 14th, 2018

- **Features**
    - ![omsdk.png](https://bitbucket.org/repo/GyRXRR/images/3400517277-omsdk.png) IAB Open Measurement compliant (viewability https://iabtechlab.com/technology-compliant-companies/#) 
    - GDPR : Automatic consent management (from CMP) so you don't have to export it manually to the sdk, MAdvertiseConsent is now deprecated.
    - Added preferredHeight argument to the infeed ad's load callback.
    - You can now request MAS banners / squares with a height of more then 250 dp.
    - Upgraded target sdk version to 28, buildToolVersion to 28.0.2
    - Upgraded Gradle version to 4.4
    - Upgraded Android Plugin dependency to 3.2.0
    - Changed Amazon ads dependency to a .jar file to support the latest version.

- **Bug Fixes**
    - Fixed gif ads not animated.
    - Updated sound management on video ads.
    - Fix MNGAnalyticsService issue on android 8

- **Ad Network Mediation Updates**
    - Add new [omsdk-android-x-Madvertise.jar] for IAB Viewability
    - Use new [mngads-sdk-x.aar], version 2.12
    - Use new amazon-ads-5.9.0.jar
    - Use new com.google.android.gms:play-services-ads:15.0.1
    - Use new com.smartadserver.android:displaylibrary:6.10.0@aar
    - Use new com.flurry.android:analytics:11.3.0@aar', 'com.flurry.android:ads:11.3.0@aar
    - Use new com.mopub:mopub-sdk:5.3.0@aar
    - Use new com.adcolony:sdk:3.3.5
    - Use new presage-moat-3.0.26-3.0.14.aar
    - Use new Support-v4: com.android.support:support-v4:28.0.0

## Version 2.11.2
#### Release date: September 26th, 2018

- **Bug Fixes**
    - Fixed timeout/lag for infeed format

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.11.2
    - Use [amazon-ads-x.jar], version 5.9.0 (instead of compile 'com.amazon.android:mobile-ads:5.8.1.1' we are waiting an upgrade on Jcenter from Amazon team), this version is GDPR compliant


## Version 2.11.1
#### Release date: August 3th, 2018

- **Bug Fixes**
    - Fixed gif images not being animated
    - Fixed an umoove crash
    - Fixed an image loading error


- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.11.1
    - use new com.adcolony:sdk:3.3.4

## Version 2.11
#### Release date: June 14th, 2018

- **Features**

    - Retency tracking is now supported by our sdk. See [Retency]
    - [MAdvertiseVectaury] is now GDPR compliant
    - Our Demo implements [GDPR Madvertise CMP for Android]

- **Bug Fixes**

  - Fix CalledFromWrongThreadException crash from Appsfire

- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.11
    - Use new [presage-x.aar], version 3.0.17-3.0.10 (with MOAT)
    - Use new com.mopub:mopub-sdk:5.1.0@aar
    - Use new [retency-sdk-x.jar], version 1.0.1
    - Use new io.vectaury.android:sdk:1.3.1

## Version 2.10
#### Release date: May 11th, 2018


- **Features**
    - According to the General Data Protection Regulation, we now have the option to provide the consent strings to MAdvertise. See [GDPR] doc.
    - targetSdkVersion has changed to 27.
    - Added AdColony sdk for mediation (com.adcolony:sdk:3.3.3)
    - Vectaury tracking is now supported by our sdk. See [MAdvertiseVectaury]
    - Added a custom close button for mngperf interstitial ads.
    - You don't have to configure your proguard for our sdk anymore, you should keep the configurations that are specific to your app though.

- **Bug Fixes**
    - Fixed umoove engine unavailable 
    - Interstitial close process optimisation.


- **Ad Network Mediation Updates**
    - Use new [mngads-sdk-x.aar], version 2.10
    - Use new [SmartAdServer-Android-SDK-x.aar], version 6.9
    - Use new [presage-x.aar], version 3.0.13-3.0.8 (with MOAT)
    - Use new com.google.android.gms:play-services-ads:15.0.0
    - Use new com.facebook.android:audience-network-sdk:4.28.1
    - Use new com.flurry.android:analytics:10.0.0@aar and com.flurry.android:ads:10.0.0@aar
    - Use new com.adcolony:sdk:3.3.3
    

## Version 2.9.5
#### Release date: March 29th, 2018

- **Features**

    - Mopub native ad support.
    - Appsfire templates changes (background, icon position)

- **Bug Fixes**

    - Appsfire NativeAd bug fix

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9.5

## Version 2.9.4
#### Release date: March 15th, 2018

- **Features**

     - Support transparent interstitials (smartAdserver + MAS).
     - Removed retency library.
     - Edit c_facedetection = 0 if the user refuses to grant permission to use the camera (Eyes Tracking).
     - Support native ad video and vast (MAS).

- **Bug Fixes**

    - Mopub version in debug gyro popup
    - Vast tracking events (MAS).
    - Mraid close button visibility.
    - Date change errors for mediation dispatcher.

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9.4
    - Use new com.facebook.android:audience-network-sdk:4.28.0
    - Use new com.flurry.android:analytics:9.0.0@aar
    - Use new com.flurry.android:ads:9.0.0@aar
    - Use new com.mopub:mopub-sdk:4.20.0@aar


## Version 2.9.3
#### Release date: February 16th, 2018

- **Bug Fixes**

   - Fix synchronization issue on MNGAdsFactory.isInitialized for some case + background for dispatcher update

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9.3


## Version 2.9.2
#### Release date: February 15th, 2018

- **Bug Fixes**

   - Fix synchronization issue on MNGAdsFactory.isInitialized

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9.2

## Version 2.9.1
#### Release date: February 9th, 2018

- **Bug Fixes**

   - Fix crash for mraid ads from MAS without  [umooveVx.aar] (Eyes Tracking)

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9.1


## Version 2.9
#### Release date: February 6th, 2018

- **Features**
     - We added more callbacks to our MNGAdsSDKFactoryListener 
     - The SDK can now handle multiple App_IDs in the same app without causing any issues.
     - Eyes tracking feature extended to include native ads as well.
     - Improve dispatcher Ad Network tracking for MAT (adrequest-adn).
     - [Native Ad Choice position].
     - Support native video ads provided by smartAdserver.
     - Transparent Interstitial provided by smartAdserver.

- **Bug Fixes**

    - Fix Eyes tracking issue for html without mraid
    - Fix crash - com.mngads.util.MNGPreference.setKeyword
    - Fix crash - org.chromium.device.sensors.DeviceSensors.convertRotationVectorToAngles

- **Ad Network Mediation Updates**

    - Use new [mngads-sdk-x.aar], version 2.9
    - **Add com.mopub:mopub-sdk:4.19.0@aar]**
    - Use new com.google.android.gms:play-services-ads:11.8.0
    - Use new [Presage-lib.jar], version 2.2.8


## Version 2.8.1
#### Release date: December 22th, 2017

- **Features**

        - Banners optimizations
        - Change your native Ad container layout to MAdvertiseNativeContainer which is a custom viewGroup that extends FrameLayout.
        - registerViewForInteraction now has two arguments: your MAdvertiseNativeContainer and your callToAction view instead of only the callToAction view.

- **Bug Fixes**
	- Eyes Tracking issues
        - Fix DFP's adchoice misposition issue on [nativead format].
        - Fix mraid rendering and click on MAS ads.
        - Fix appsfire.MNGAFUtils.scaleBitmap crash


- **Ad Network Mediation Updates**
    - new com.facebook.android:audience-network-sdk:4.27.0
    - new [mngads-sdk-x.aar], version 2.8.1
    - new [Presage-lib.jar], version 2.2.7
    - new com.flurry.android:ads:8.2.0@aar
    - new Eyes Tracking  [umooveVx.aar], see [eyes-tracking doc]

    - Updated dependencies :

```groovy
    compile(name: 'mngads-sdk-2.8.1', ext: 'aar')
    provided files('libs/presage-lib-2.2.7-obfuscated.jar')
    compile 'com.facebook.android:audience-network-sdk:4.27.0'
    compile 'com.flurry.android:analytics:8.2.0@aar'
    compile 'com.flurry.android:ads:8.2.0@aar'
    compile(name: 'umooveV2.12.5', ext: 'aar')
```

## Version 2.8
#### Release date: November 23th, 2017

- **Features**

    - use targetSdkVersion to 26.
    - Implemented new preferredHeight logic for banner ads and MAS.
    - New [Rewarded Video for Android].
    - New reset SDK button in debug gyro.
    - now MAS support video and vast format for infeed, interstitial and medium rectangle
    - New blurry background for video ads (multiple formats).
    - Proguard compliant

- **Bug Fixes**
	- Eyes Tracking issues

- **Ad Network Mediation Updates**
    - new com.facebook.android:audience-network-sdk:4.26.1
    - new com.google.android.gms:play-services-ads:11.6.0
    - new [mngads-sdk-x.aar], version 2.8
    - new [SmartAdServer-Android-SDK-x.aar], version 6.7.2
    - new [Presage-lib.jar], version 2.1.17
    - new com.flurry.android:ads:8.1.0@aar
    - new Eyes Tracking  [umooveVx.aar], see [eyes-tracking doc]

    - Updated dependencies :

```groovy
    compile(name: 'mngads-sdk-2.8', ext: 'aar')
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
#### Release date: September 27th, 2017

 - clean permissions on aar [mngads-sdk-x.aar], version 2.7.3
 - please [configure-your-manifest] according libs in used in your application or if your app uses the GPS.


## Version 2.7.2
#### Release date: September 18th, 2017

- New feature: Implementing the new eyes detection feature in Mraid ads.
- Fix blank screen after appsfire click.
- Edit Vast ads selecting mediaUrl algorithm to prioritize videos(mp4/3gpp) over vpaid ads.
- use new com.facebook.android:audience-network-sdk:4.26.0
- use new com.google.android.gms:play-services-ads:11.2.2
- use new [mngads-sdk-x.aar], version 2.7.2
- use new [SmartAdServer-Android-SDK-x.aar], version 6.7.1
- Updated dependencies :

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
#### Release date: August 31th, 2017
Changed Presage library configuration in manifest.
You have to manually add presage library's manifest configuration according to [Ogury Integration].

- Updated dependencies :

```groovy
  //madvertise mediation+adserving
  compile(name: 'mngads-sdk-2.7.1', ext: 'aar')
```



## Version 2.7
#### Release date: August 29th, 2017
- Major configuration change:
   - We now use aar file instead of a jar file.
   - We reduced the AndroidManifest configuration needed to work with our sdk.
   - If you are using Proguard you don't have to add extra configurations, it will be done automatically.
- What we added :
   - Mopub adapter for mngads sdk.
   - AppsFire menu in demo app.
   - AchoiceView for MAdvertise ads.
   - Call impressions from a js script.
   - Event status ignored(8) for Analytics events.
- Bug fixes :
    - In app click issue with deeplink fallback url. 
    - Debug gyro showing a popup when the app is on background.
    - Out of memory error in appsFire shashimi view.
- AdNetworks version:
  - [mngads-sdk-x.aar], version 2.7
  - FacebookAudience, version 4.25.0
  - Flurry, version 7.2.3
  - [SmartAdServer-Android-SDK-x.aar], version 6.7
  - DFP, version 11.2.0

- Updated dependencies :
```
java
  //madvertise mediation+adserving
  compile(name: 'mngads-sdk-2.7', ext: 'aar')
  //mediation - Audience Network (Facebook)
  compile 'com.facebook.android:audience-network-sdk:4.25.0'
  //mediation - Flurry
  compile 'com.flurry.android:analytics:7.2.3@aar'
  compile 'com.flurry.android:ads:7.2.3@aar'
  //Smart AdServer SDK
  compile(name: 'SmartAdServer-Android-SDK-6.7', ext: 'aar')
  //mediation - ogury
  compile files('libs/presage-lib-2.1.13-obfuscated.jar')
  //mediation - ogury
  compile files('libs/presage-lib-2.1.13-obfuscated.jar')
  //Google Play Services with Google Mobile Ads
  compile 'com.google.android.gms:play-services-ads:11.2.0'
  compile 'com.google.android.gms:play-services-location:11.2.0'
 
```


## Version 2.6
#### Release date: June 23th, 2017

- Implemented new feature in MAdvertiseAdserver (MAS) that tracks the user's face to determine if he is really watching the ad or not , and for how long. You must add [umooveVx.aar]
- New infeed ad format in mngadserver (MAS).
- Fix possible bug where the cascade would be blocked without returning a valid ad, no a fail error.
- Fix click issue with deeplink 
- Edit impression requirements.
- Add sdk version to cache : reset the dispatcher on new sdk version.
- Remove spaces from keywords.
- Debug gyro : add adsize to request details.
- use new AdNetworks version:

  1.  use new SmartAdServer 6.6.6 version
  2. use new FacebookAudience 4.23.0 version
  3. use new Flurry 7.1.1 version 
  4. use new Ogury 2.1.6 version 
  5. use new DFP 11.0.0 version


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
 //mediation - DFP
    compile 'com.google.android.gms:play-services-ads:11.0.0'
    compile 'com.google.android.gms:play-services-location:11.0.0'
```


## Version 2.5.2
#### Release date: May 10th, 2017

 - Bug fixes :

    - fix crash in MNGAdPreferences : fix out of memory error related to big data in String object
    - fix Ogury crash
 
Don't forget to update following librairies :

```
compile files('libs/mng-ads-sdk.jar')
compile files('libs/presage-lib-2.0.7-obfuscated.jar')

```

## Version 2.5.1
#### Release date: Avril 25th, 2017

 - use setSSLSocketFactory instead of setDefaultSSLSocketFactory for HttpsURLConnection (SSL)

Don't forget to update following libraries :

 - [mng-ads.jar Android SDK]

```
compile files('libs/mng-ads-sdk.jar')
```

## Version 2.5
#### Release date: April 14th, 2017

 - Some methods in MNGAdsFactory are now deprecated and will be removed in next version:

| Depecated method | New method |
| --- | --- |
| createBanner() | loadBanner() |
| createBanner(MNGFrame frame) | loadBanner(MNGFrame frame)  |
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

- MAdvertiseException : in case of fail, the didFail callback will be fired with an Exception, if you want to check which exception was invoked, you can cast it to MAdvertiseException and use getErrorCode().
- persisent seenAd : seenAd is now managed in the sdk cache without life time.
- native ad adChoice : adserver can return an adchoice view for native ad.
- clarify doc about native ad registerViewForInterraction.
- add crashlitycs in MngAdsDemo. 
 - Fixed bugs:
   - Interstitial Disapper callback : in some case the listener Disapper is not called in back pressed, the problem appear only with smart interstitial . 
   - Null values in Request : don't send the parameter to the adNetwork if it is null or empty.
   - Inall : fix dfp custom targetting and key words.
   - utf8 Encoding : fix ut8 encoding for adserver html pubs.
- use new AdNetworks version:
    - use new FBAudienceNetwork 4.21.0 version
    - use new Flurry 7.0.0 version
    - use new SmartAdServer 6.6.5 version
    - use new BeaconForStore 2.2.3 version 
    - use new Ogury 2.0.5 version 
Don't forget to update following librairies :


```
compile files('libs/mng-ads-sdk.jar')
compile 'com.facebook.android:audience-network-sdk:4.21.1'
compile files('libs/SmartAdServer-Android-SDK-6.6.5.jar')
compile 'com.flurry.android:analytics:7.0.0@aar'
compile 'com.flurry.android:ads:7.0.0@aar'
compile(name: 'b4s-android-sdk', ext: 'aar')
compile files('libs/presage-lib-2.0.5-obfuscated.jar')

```
Don't forget to change flurry dependencies from JAR to AAR

```
Important
It is highly recommended to use the AAR format of the Flurry SDK. Using jars is now deprecated. Please update to AARs as Flurry will be removing jars in a future release.
```

```
Note
If you are adding the AAR format of the Flurry dependencies, you do not need to add flurry activity  in your AndroidManifest file. 
   <activity
    android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
    android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode| screenSize|smallestScreenSize">
    </activity>
    
    And you do not need to add flurry proguard rules to your proguard.cfg file
    -keep class com.flurry.** { *; }
    -dontwarn com.flurry.**
    
```

## Version 2.4.1
#### Release date: March 27th, 2017

 - onBackPressed button close interstitial
 - use mute for appsfire videos
 - demo sample for isTablet
 - clarify doc about debug gyro that requires


```
#!xml

<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
```
Don't forget to update following librairies :


```
compile files('libs/mng-ads-sdk.jar')
```

## Version 2.4
#### Release date: March 08th, 2017
 - add support for vast inline
 - add Interstitial singleton manager : your request is  ignored if you have already an Interstitial loded.
 - add inall targetting
 - new custom badge for native ad
 - new content url in MNGPreference : now you can pass  to the sdk an URL for content related to your app (url must be a string which length not exceed 512 caracters)
 - persistent capping : capping is now managed on cache.
 - use new AdNetworks version:
    - use new FBAudienceNetwork 4.20.0 version,  [AudienceNetwork.jar]
    - use new DFP 10.2.0 version
    - use new Flurry 6.9.1 version,  ([flurryAds.jar] and [flurryAnalytics.jar] )
    - use new SmartAdServer 6.6.3 version, [SmartAdServer-Android-SDK.jar]
    - use new Ogury 2.0.2 version, [Presage-lib.jar]

Don't forget to update following librairies :


```
compile files('libs/mng-ads-sdk.jar')
compile 'com.google.android.gms:play-services-ads:10.2.0'
compile 'com.google.android.gms:play-services-location:10.2.0'
compile 'com.flurry.android:analytics:6.9.1'
compile 'com.flurry.android:ads:6.9.1'
compile 'com.facebook.android:audience-network-sdk:4.20.0'
compile files('libs/presage-lib-2.0.2-obfuscated.jar')
compile files('libs/SmartAdServer-Android-SDK-6.6.3.jar')
```

## Version 2.3.4
#### Release date: February 9th, 2017

 - Smart Interstitial ( clean interstitial container on smart failed)
 - fix dispatcher cache on placement pause


Don't forget to update following libraries :

 - [mng-ads.jar Android SDK]

```
compile files('libs/mng-ads-sdk.jar')
```

## Version 2.3.3
#### Release date: January 30th, 2017
 - Smart Interstitial, manage State
 - use new BeaconForStore 2.1.4 version
 - use new Flurry 6.8.0 version, compile 'com.flurry.android:analytics:6.8.0', compile 'com.flurry.android:ads:6.8.0'
 - use new  SmartAdServer 6.6.2 version, [SmartAdServer-Android-SDK.jar]
 - use new Ogury 1.8.3 version, [Presage-lib.jar]
 - use new Facebook sdk 4.19.0 version, compile 'com.facebook.android:audience-network-sdk:4.19.0'
- add *Shake To Debug* system, [debug-mode-gyro]
 - add support contentURL for DFP
 - improve Demo:
    - add view pager sample: contains a native ad page, https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/SwipeAdFragment.java?at=master&fileviewer=file-view-default


## Version 2.3.2
#### Release date: December 21th, 2016

 - new template interstitial and square (Appsfire [mng-ads.jar Android SDK] )
 - use new Facebook [AudienceNetwork.jar] 4.18.0 version
 - use new Google DFP 10.0.1 version
 - use new Flurry 6.7.0 version ([flurryAds.jar] and [flurryAnalytics.jar] )
 - use new BeaconForStore 2.0.13 version
 - use new [SmartAdServer-Android-SDK.jar] 6.6 version

Don't forget to update following libraries :


```
compile files('libs/mng-ads-sdk.jar')
compile files('libs/SmartAdServer-Android-SDK-6.6.jar')
compile 'com.google.android.gms:play-services-ads:10.0.1'
compile 'com.google.android.gms:play-services-location:10.0.1'
compile 'com.flurry.android:analytics:6.7.0'
compile 'com.flurry.android:ads:6.7.0'
compile 'com.facebook.android:audience-network-sdk:4.18.0'
```

## Version 2.3.1
#### Release date: November 11th, 2016

 - core optimization (dispatcher)
 - use new SmartAdServer 6.5 version [SmartAdServer-Android-SDK.jar]

Don't forget to update following libraries :
```

   compile files('libs/mng-ads-sdk.jar')
   compile 'com.google.android.gms:play-services-ads:9.8.0'
   compile 'com.google.android.gms:play-services-location:9.8.0'
   compile files('libs/SmartAdServer-Android-SDK-6.5.jar')
   compile 'com.facebook.android:audience-network-sdk:4.17'
```


## Version 2.3
#### Release date: October 28th, 2016

 - Now MNGADS becomes MADVERTISE MEDIATION and MADVERTISE ADSERVING
 - VAST 2 /VPAID 1 support for MADVERTISE ADSERVING
 - Upgrading MADVERTISE MEDIATION libraries
 - Improve Native Ad assets management with 
```
 nativeObject.downloadAssetsForType(mMAdvertiseType,mImageView);
```
 - Cache Optimisations
 - Bugs fixes




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

available on 

 - [nl.qbusict:cupboard:2.1.4]
 - [de.greenrobot:eventbus:2.4.0]
 - [com.squareup.retrofit2:converter-jackson:2.0.0]
 - [b4s-android-sdk]
 - [b4s-android-sdk-playservices830]



## Version 2.2.1
#### Release date: September 9th, 2016

 - Now appsfire support videos for square, nativeAds and interstitials

Don't forget to update following libraries 

 - [mng-ads.jar Android SDK] 

## Version 2.2
#### Release date: AUgust 30th, 2016

 - HTTPS support
 - New appsfire template for banner, medium rectangle and interstitial
 - upgrade libraries

Don't forget to update following libraries 

 - [mng-ads.jar Android SDK] 
 - [Presage-lib.jar]


Don't forget to update following lines to your app's build.gradle
:
```
#!graddle
   //Google Play Services
   compile 'com.google.android.gms:play-services-ads:9.4.0'

  //Audience Network 
  compile 'com.facebook.android:audience-network-sdk:4.15.0'
  
 //Amazon
    compile 'com.amazon.android:mobile-ads:5.8.1'

 //Flurry
    compile 'com.flurry.android:analytics:6.5.0'
    compile 'com.flurry.android:ads:6.5.0'
```
If using Intellij IDEA or Eclipse, [download and extract here] and on [libs]


 


## Version 2.1.1
#### Release date: July 13th, 2016

you must check [Upgrade Guide]. You must update [mng-ads.jar Android SDK] and [SmartAdServer-Android-SDK.jar]

 - fix smart issue (thread and interstitial)
 - Add constants for banner size (MNGAdSize.MNG_DYNAMIC_LEADERBOARD for tablets, MNGAdSize.MNG_DYNAMIC_BANNER for mobiles)

 - Don't forget to update following libraries :
    - [mng-ads.jar Android SDK]
    - com.facebook.android:audience-network-sdk:4.13.0
    - [SmartAdServer-Android-SDK.jar]
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


## Version 2.1
#### Release date: June 20th, 2016

you must check [Upgrade Guide]

 - Native Ad, add getAdChoiceBadgeView for Google/Adx certification
 - Add Smart [In-Feed Ad format] (Parallax or Video)
 - Fixes for appsfire crashes and out of memory
 - Improve mng adserving (interstitial capping, keywords)
 - Improve logging system
 - Improved preferredHeightDP
 - Add listener for refresh event
 - Remove [Liverail.jar]
 - Use gradle dependency for Amazon compile 'com.amazon.android:mobile-ads:5.7.2' instead of compile files('amazon-ads-5.6.20.jar')
 - Don't forget to update following libraries :
    - [mng-ads.jar Android SDK]
    - [AudienceNetwork.jar]  (com.facebook.android:audience-network-sdk:4.12.1)
    - [Amazon.jar]   (com.amazon.android:mobile-ads:5.7.2)
    - [FlurryAds.jar] and [FlurryAnalytics.jar]

## Version 2.0.8
#### Release date: May 24th, 2016


 - Now you can disable [interstitial auto-displaying] 

## Version 2.0.7
#### Release date: May 12th, 2016

 - bug fix for [mng-ads.jar Android SDK] (mraid webView callback called after destroy)
 - Now MNGAdapter methods are public to allow extends (e.g Xamarin integration)

## Version 2.0.6
#### Release date: April 8th, 2016

you must check [Upgrade Guide]. You need to keep all Ad Network jars up to date. You must update [mng-ads.jar Android SDK]

 - MNGAnalyticsService collecting data optimisation
 - Now MNGAdapter methods are public to allow extends (e.g Xamarin integration)

## Version 2.0.5
#### Relase date: April 6th, 2016

you must check [Upgrade Guide]. You need to keep all Ad Network jars up to date.

 - MNG Ads Factory will ignore any interstitial request while there is a pending request or there is interstitial shown at that moment.
 - MNG Ads Factory will ignore any interstitial request if interstitial was just closed and there is a new interstitial request before 5s delay.
 - Banner rotation for appsfire
 - NativeAd improvement for DFP
 - Check with proguard 

## Version 2.0.4
#### Release date: March 14th, 2016

you must check [Upgrade Guide]. You need to keep all Ad Network jars up to date.

 - bug fixes for [mng-ads.jar Android SDK]
 - Add new adnetwork Ogury [Presage-lib.jar]
 - update [SmartAdServer-Android-SDK.jar]


## Version 2.0.3
#### Release date: March 2th, 2016

You need to keep all Ad Network jars up to date.

 - bug fixes for [mng-ads.jar Android SDK]

## Version 2.0.2
#### Release date: February 21th, 2016

You need to keep all Ad Network jars up to date.

 - fix issues.
 - appsfire performance optimisations

## Version 2.0.1
#### Release date: February 1th, 2016

You need to keep all Ad Network jars up to date.

 - fix nativead issues.

## Version 2.0
#### Release date: January 27th, 2016

you must check [Upgrade Guide]. You need to keep all Ad Network jars up to date.

 - The sdk afAdSdk.jar, mngperf-android-sdk.jar, AppNexus-sdk are merged on mngads SDK [mng-ads.jar Android SDK] for better performance and reduce libraries number
 - We have added - [Amazon.jar], [Liverail.jar], [FlurryAds.jar] to mngads mediation in order to increase fill rate and revenus



## Version 1.5.2

#### Release date: January 8th, 2016

 - fix appsfire bugs + cleans
 - code optimisations for smart banner

## Version 1.5.1

#### Release date: November 19th, 2015

 - Banner improvement for dynamic height

You must update [mng-ads.jar Android SDK]. **Implementation has changed, you mus check [Upgrade Guide]

## Version 1.5

#### Release date: November 10th, 2015

 - New appsfire version (use mngads adserver)

You must update [mng-ads.jar Android SDK], [afAdSdk.jar].

## Version 1.4.4

#### Release date: October 26th, 2015

 - bug appsfire

You must update [mng-ads.jar Android SDK], [afAdSdk.jar].

## Version 1.4.3

#### Release date: October 22th, 2015

 - clean warnings
 - Update FB SDK (impression issue on FB SDK 4.6)

You must update [mng-ads.jar Android SDK], [AudienceNetwork.jar].

## Version 1.4.2

#### Release date: October 16th, 2015

 - Now Mngads supports android 23
 - Interstitial improvement, now isInterstitialShowen is managed by SDK
 - Update New SmartAdserver SDK

You must update [mng-ads.jar Android SDK], [SmartAdServer-Android-SDK.jar].

## Version 1.4.1

#### Release date: September 18th, 2015

 - new smart SDK
 - new facebook SDK
 - new appsfire SDK (use Himono format for banner
 - Manage banner size (fixed or responsive) server side

You must update [mng-ads.jar Android SDK], [SmartAdServer-Android-SDK.jar], [afAdSdk.jar], [AudienceNetwork.jar] and [AppNexus-sdk]

## Version 1.4

#### Release date: July 30th, 2015

 - new smart SDK (+prefetch support)
 - new facebook SDK
 - new appsfire SDK
 - nativeAd, now we support DFP for premium nativeAd
 - Keywords can be managed server side


You must update [mng-ads.jar Android SDK], [SmartAdServer-Android-SDK-6.0.jar], [afAdSdk.jar] and [Google-play-services_lib],[mngperf-android-sdk.jar],[AudienceNetwork.jar] and [Retency-sdk] libraries

## Version 1.3.3

#### Release date: July 8th, 2015

 - sortAdsServersByPriority optimization
 - add click listener (see "Ad click listener" section on wiki )
 - mngperf adserving improvements


You must update [mng-ads.jar Android SDK], [afAdSdk.jar] and [mngperf-android-sdk.jar] libraries

## Version 1.3.2

#### Release date: June 19th, 2015

 - debug mode improvements

## Version 1.3.1

You must check [Upgrade Guide]

#### Release date: June 1th, 2015

 - Manage dynamic size for DFP and appNexus banners
 - Add remote debug mode
 - MNGNativeObject.getPriceType() (use to add "free" icon)
 - Add [Best practice Mngads], optimized use case for several ad formats on one page
 - Update appsfire, Facebook and DFP libraries
 - Add retency adNetwork


## Version 1.2.7

#### Release date: April 16th, 2015

 - Fix issue with square format and dynamic width
 - update appsfire and Facebook SDKs

## Version 1.2.6

#### Release date: April 14th, 2015

 - Adding AppNexus preference keyworks
 - update + appsfire SDK bug  fixing

## Version 1.2.5

#### Release date: April 9th, 2015

 - Adding AppNexus adNetwork
 - nativeAd improvements
 - Adding MNGAdsFactory.isInitialized()

## Version 1.2.4

#### Release date: March 30th, 2015

 - timeout improvement
 - capping improvement (on placementId and not on MNGAdsFactory)
 - Add keyword preferences
 -  bug fix for FB and appsfire

## Version 1.2.3

#### Release date: March 16th, 2015

 - bug fix NullPointerException

## Version 1.2.1

#### Release date: March 11th, 2015

 - Refreshing of ads is now done by mng ads, improving capping functionality + remove debug mode

## Version 1.2

#### Release date: February 21th, 2015

 - Add new **carousel** placement, see [Ad Examples]
 - Add new layout for demo project (inspiration to get you started)

## Version 1.1

#### Release date: February 11th, 2015

 - MngAds skips Ad Networks with wrong IDs

## Version 1.0

#### Release date: February 4th, 2015

 - Initial version


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
[SmartAdServer-Android-SDK-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
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
[Wiki]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home
[presage-lib.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[interstitial auto-displaying]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-disable-auto-displaying
[In-Feed Ad format]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-infeed
[download and extract here]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsRequiredJars/
[libs]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[nl.qbusict:cupboard:2.1.4]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[de.greenrobot:eventbus:2.4.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[com.squareup.retrofit2:converter-jackson:2.0.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk-playservices830]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[debug-mode-gyro]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/debug-mode-gyro
[mngads-sdk-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Ogury Integration]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-ogury-integration
[configure-your-manifest]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-configure-your-manifest
[Rewarded Video for Android]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/rewarded-video
[umooveVx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[eyes-tracking doc]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-eyes-tracking
[nativead format]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/nativead
[Native Ad Choice position]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/nativead#markdown-header-customize-native-ad-adchoice
[presage-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[GDPR]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/gdpr
[MAdvertiseVectaury]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/MAdvertiseVectaury
[retency-sdk-x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[Retency]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Retency
[GDPR Madvertise CMP for Android]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/wiki/Home
[amazon-ads-x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[omsdk-android-x-Madvertise.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[madvertiselocation-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[MAdvertiseCmp-xx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[Amazon-APS]:https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/libs/DTBAndroidSDK-7.4.3.aar
[Android X]:https://developer.android.com/jetpack/androidx/migrate
[Sync Display SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/syncDisplay
[Thumbnail Ad]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/thumbnail