## Change log and release notes for the MngAds SDK for Android.
See [Wiki], [Design Guidelines and Best practices] and [Help Center]  for more detailed informations

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


[Ad Examples]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/inspiration
[Best practice Mngads]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[mngperf-android-sdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/mngperf-android-sdk.jar?at=master
[mng-ads.jar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/mng-ads-sdk.jar?at=master
[afAdSdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/afAdSdk.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[Retency-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/retency-sdk.jar?at=master
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/AudienceNetwork.jar?at=master
[SmartAdServer-Android-SDK.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/SmartAdServer-Android-SDK-6.1.jar?at=master
[AppNexus-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/sdk/?at=master
[Design Guidelines and Best practices]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[Wiki]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
