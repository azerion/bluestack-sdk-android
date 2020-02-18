# Banner

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

Example | Description| 
------------- | ------------- |
![banner50-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/288211594-banner50-mngads-android-min.png) Banner -  (50dp  or 90dp )  | A banner is a small bar ad that appears at the bottom or top of your content. Usually sized 320 x 50. Only include one ad per page or show one ad at a time if scrolling. In all cases, **the banner width is flexible with a minimum of 320px.**. If you are building your app for iPad  consider using 90px and 50px for iphone. 
 ![banner250-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/4181983461-banner250-mngads-android-min.png) Square - Medium rectangle (300 x 250) |Square banner also known as a *medium rectangle* (300 x 250). This format can increase earnings when both text and image ads are enabled. Performs well when embedded within text content or at the end of articles.


# Integration for Android

## Step 1. Init Banner factory

To create a banner you have to init an object with type MNGAdsSDKFactory.

```java
MNGAdsFactory mngAdsBannerAdsFactory = new MNGAdsFactory(this);

```
## Step 2. Set Placement ID

You have also to set placement Id :

```java
mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

## Step 3. Implement the Listener
Next, implement the Banner Listener in your code. 

```java
mngAdsBannerAdsFactory.setBannerListener(this);
```

The SDK will notify your Listener of all possible events listed below :

- bannerDidLoad(View adView,int preferredHeightDP): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.

```java
@Override
public void bannerDidLoad(View adView ,int preferredHeightDP);
Log.d(TAG, "your banner is ready")
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
...
adLayout.addView(adView);
}
```

- bannerDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
public void bannerDidFail(Exception adsException) {
Log.e(TAG, "banner did fail :" + adsException.toString());
}
```

- bannerResize(MNGFrame frame) : will be called when the banner has changed size

```java
@Override
public void bannerResize(MNGFrame frame) {
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
Log.d(TAG, "Banner did resize w dp " + frame.getWidth() + " h dp " + frame.getHeight());
...
}
```
## Step 4. Loading Banner ad

To make a request you have to call 'loadBanner' using the mng banner size. (in this example it’s the BANNER size used):

```java
mngAdsBannerAdsFactory.loadBanner(MNGAdSize.MNG_DYNAMIC_BANNER)

```

**Note:** if your application support different screen sizes on Tablet and Phone, it is better to use this code :

```java
MNGFrame  mMNGAdSize = getResources().getBoolean(R.bool.is_tablet) ? MNGAdSize.MNG_DYNAMIC_LEADERBOARD : MNGAdSize.MNG_DYNAMIC_BANNER ;
mngAdsBannerAdsFactory.loadBanner(mMNGAdSize)

```

### MNGAdSize
Mng ads provides variant pre-defined sizes, See table below for details about our supported standard banner sizes:


| MNGAdSize | Description |Dimensions in dp (WxH)
| --- | --- | --- |
| MNG_BANNER	| Standard Banner	 | 320 x 50 |
| MNG_ LARGE_BANNER  | Large Banner |320 x 100 |
| MNG_ MEDIUM_RECTANGLE   | Medium Rectangular Banner	 |300 x 250 |
| DYNAMIC BANNER |Adjusted Banner| Screen width x 50 |
| MNG_ FULL_BANNER	| Full Banner  | 468 x 60 |
| LEADERBOARD	| Standard Banner for tablet	 | 728 x 90 |
| MNG_ DYNAMIC_LEADERBOARD	| Adjusted Banner for tablet	 | Screen width x 90 |



## Troubleshooting

### Memory managment
When you have finished your ads plant you must free the memory.

```java
@Override
protected void onDestroy() {
mngAdsBannerAdsFactory.releaseMemory();
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
mngAdsBannerAdsFactory.loadInterstitial(false);
} else {
Log.d(TAG, "Ads Factory is busy");
}
```

### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked

```java
// set click listener
mngAdsBannerAdsFactory.setClickListener(this);


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
mngAdsBannerAdsFactory.setRefreshListener(this);

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


mngAdsBannerAdsFactory.loadBanner(new MNGFrame(320, 50), mngPreference);

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

### Remove Banner View
If you like to Remove banner from the view, you can use this code : 

```java
...  
adLayout.removeView(adView);  
adLayout.requestLayout();
...
```

### Optimized use case for several ad formats on one page

When trying to display several ad formats on one page try to synchronize your requests instead of making multiple ones at the some time. By making the requests at the same time you are decreasing your chance of receving an Ad and you are making your app slow .You can check the number of MNGAdsFactory running a request by calling :


```java
    int mNumberOfRunningFactory=MNGAdsFactory.getNumberOfRunningFactory() ;
```

You can see an example on [AdsFragment.java].


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