## Change log and release notes for the MngAds SDK for Android.
See [Wiki], [Design Guidelines and Best practices] and [Help Center]  for more detailed informations

you must check [Upgrade Guide]. You need to keep all Ad Network jars up to date. 


## Version 2.2
#### Release date: AUgust 30th, 2016

 - HTTPS support
 - New appsfire template for banner, medium rectangle and interstitial
 - upgrade librairies

Don't forget to update following librairies 

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

 - Don't forget to update following librairies :
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
 - Don't forget to update following librairies :
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

 - The sdk afAdSdk.jar, mngperf-android-sdk.jar, AppNexus-sdk are merged on mngads SDK [mng-ads.jar Android SDK] for better performance and reduce librairies number
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


You must update [mng-ads.jar Android SDK], [SmartAdServer-Android-SDK-6.0.jar], [afAdSdk.jar] and [Google-play-services_lib],[mngperf-android-sdk.jar],[AudienceNetwork.jar] and [Retency-sdk] librairies

## Version 1.3.3

#### Release date: July 8th, 2015

 - sortAdsServersByPriority optimization
 - add click listener (see "Ad click listener" section on wiki )
 - mngperf adserving improvements


You must update [mng-ads.jar Android SDK], [afAdSdk.jar] and [mngperf-android-sdk.jar] librairies

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
 - Update appsfire, Facebook and DFP librairies
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
[SmartAdServer-Android-SDK.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/SmartAdServer-Android-SDK-6.4.jar
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
[presage-lib.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/presage-lib-1.8.1.jar?fileviewer=file-view-default
[interstitial auto-displaying]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-disable-auto-displaying
[In-Feed Ad format]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-infeed
[download and extract here]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsRequiredJars/
[libs]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
