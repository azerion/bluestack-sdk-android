# Infeed
Ads that show up in the middle of the stream as you scroll through your content Parallax or Video.

[TOC]

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

## Integration for Android

## Step 1. Init Infeed factory

To create a infeed you have to init an object with type MNGAdsSDKFactory.

```java
MNGAdsFactory mngInfeedAdsFactory = new MNGAdsFactory(this);

```
## Step 2. Set Placement ID

You have also to set placement Id :

```java
mngInfeedAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

## Step 3. Implement the Listener

Next, implement the Infeed Listener in your code. 

```java
mngAdsInfeedAdsFactory.setInfeedListener(this);
```

The SDK will notify your Listener of all possible events listed below :

- infeedDidLoad(View infeedView): will be called by the SDK when your infeedView is ready. now you can add your infeedView to your view.

```java
@Override
public void infeedDidLoad(View infeedView, int preferredHeightDP) {
Log.d(TAG, "your infeed view is ready")
...
adLayout.addView(infeedView);
}
```

- infeedDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
public void infeedDidFail(Exception adsException) {
Log.e(TAG, "infeed did fail :" + adsException.toString());
}
```

**Note :** infeed does not return preferredHeight like banner because infeed height depends of width.

## Step 4. Loading Infeed ad

To make a request you have to call 'loadInfeed' using MAdvertise Infeed Frame:

```java
mngAdsInfeedAdsFactory.loadInfeed(new MAdvertiseInfeedFrame(300, MAdvertiseInfeedFrame.INFEED_RATIO_16_9)

```

**Note :** 

- You have to choose the convenient frame for your infeed when loading the ad by using the MAdvertiseInfeedFrame class.

- Add the width (in dp) of your frame and the desired ratio.

- Choose one of the following ratios for the ad:

 - MAdvertiseInfeedFrame.**INFEED_RATIO_16_9** for **16:9** (is the international standard format of HDTV, the one used in our demo)
 - MAdvertiseInfeedFrame.**INFEED_RATIO_4_3** for **4:3**

The default ratio is 16:9

## Troubleshooting

### Memory managment
When you have finished your ads plant you must free the memory.

```java
@Override
protected void onDestroy() {
mngAdsInfeedAdsFactory.releaseMemory();
super.onDestroy();
}
```

### isBusy

Before making a request if you want to check that factory is not busy (Ads factory is busy means that it has not finished the previous request yet).

isBusy will be set to :

- **true :** when factory starts handling request.

- **false :** when factory finishes handling request.

**Example**:

```java
if (!mngAdsBannerAdsFactory.isBusy()) {

Log.d(TAG, "Ads Factory is not busy");
mngAdsInfeedAdsFactory.loadInterstitial(false);
} else {
Log.d(TAG, "Ads Factory is busy");
}
```

### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked

```java
// set click listener
mngAdsInfeedAdsFactory.setClickListener(this);


...
@Override
public void onAdClicked() {
Log.d(TAG, "Ad Clicked");
}
...
```

### Ad refresh listener
You can also implement MNG refresh listener callback to detect when an Ad refreshed

```java
// set refresh listener
mngAdsInfeedAdsFactory.setRefreshListener(this);

...
@Override
public void onRefreshSucceed() {
Log.d(TAG, "refresh succeed");
}

@Override
public void onRefreshFailed(Exception e) {
Log.d(TAG, "refresh failed");
}
...
```
### Preferences Object
Preferences object is an optional parameter that allow you select ads by user info.
informations that you can set are:

- **Age :**  age of user
- **Location :**  geographical position of the user.
- **Language :** : language of user (ISO code)
- **Gender :**  gender of user
- **KeyWord :**  Use free-form key-values when you want to pass targeting values dynamically into an ad tag based on information you collect from your users. You can also use free-form key-values when there are too many possible values to define in advance. Separator in case of multiple entries is **;**.
- **Content URL :**  URL for content related to your app (url must be a string which length not exceed 512 caracters).

```java

Location  myLocation = new Location("I");
myLocation.setLatitude(35.757866);
myLocation.setLongitude(10.810547);

mngPreference = new MNGPreference();
mngPreference.setLocation(myLocation);
mngPreference.setAge(28);
mngPreference.setGender(MNGGender.MNGGenderFemale);
mngPreference.setKeyword("brand=myBrand;category=sport");
mngPreference.setLanguage("fr");
mngPreference.setContentUrl("put your content url here")


mngAdsInfeedAdsFactory.loadInfeed(new MAdvertiseInfeedFrame(300, MAdvertiseInfeedFrame.INFEED_RATIO_16_9), mngPreference);

```
**Note :** 

- This [link] can help you to get device location.

- Do not serialize Location object (like transforming it into a string using gson library), this may lead to a fatal runtime error when that instance is reused.

### Exceptions
|Exception|Error code|Message|Meaning|
| --- | --- | --- | --- |
|MAdvertiseWrongPlacementIdException|WRONG_PLACEMENT_ERROR = 0   |    Wrong placement | You have set a wrong placement |
|MAdvertiseInternetException|NO_INTERNET_ERROR = 1   |    No Internet | There is no internet connection at the moment      |
|MAdvertiseSDKUninitializedException|SDK_UNINITIALIZED_ERROR = 2   |    MNGAds is not initialized | The sdk is not initialized, you have to call  MNGAdsFactory.initialize(context,"your app id");      |
|MAdvertiseRequestCappedException|CAPPED_REQUEST_ERROR = 3  |    Your request has been capped | Your request is capped, If you are in doubt, check your capping value related to the placement|
|MAdvertiseBusyFactoryException|BUSY_FACTORY_ERROR = 5   |    Your factory is busy| Your factory is busy by an other request at the moment     |
|MAdvertiseNoAdException|NO_AD_ERROR = 7   |    No Ad found | Therese no ad to dilver at the moment     |
|MAdvertiseTimeOutException|TIME_OUT_ERROR = 10   |  no ad to deliver before time out | Therese no ad to deliver before the specified time out  |

**Handle Exception :** If you want to check which exception was invoked, in the didFail callback you have to cast the exception to MAdvertiseException and then use getErrorCode() to get exception code.
Also you can get exception message by calling getMessage().
In the example below we use interstitialDidFail, even you can use this logic in all our didFail callBack(bannerDidFail, infeedDidFail,nativeAdCollectionDidFail and nativeObjectDidFail)

```java
@Override
public void interstitialDidFail(Exception e) {

MAdvertiseException adException=(MAdvertiseException)e;

switch (adException.getErrorCode())
{
case MAdvertiseException.BUSY_FACTORY_ERROR :
case MAdvertiseException.INTERSTITIAL_ALREADY_SHOWN_ERROR :
.
.
.

}
Log.e(TAG, "Interstitial did fail : " + adException.getMessage()+" error code "+adException.getErrorCode());
}
```




[AdsFragment.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.java?at=master
[omsdk-x.x.x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[link]:https://developer.android.com/training/location/retrieve-current.html
[SmartAdServer]:http://documentation.smartadserver.com/displaySDK
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
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
[Mopub Marketplace]:https://www.mopub.com/
[AdColony]:https://www.adcolony.com/