# Banner Integration for Android

[TOC]

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).


## Step 1. Init Banner factory

To create a banner you have to init an object with type MNGAdsSDKFactory.

* **Java**

```java
MNGAdsFactory mngAdsBannerAdsFactory = new MNGAdsFactory(this);

```
* **Kotlin**

```java
mngAdsBannerAdsFactory = MNGAdsFactory(this)

```
## Step 2. Set Placement ID

You have also to set placement Id :

* **Java**

```java
mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

* **Kotlin**

```java
mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID")
```

## Step 3. Implement the Listener
Next, implement the Banner Listener in your code. 

* **Java**

```java
mngAdsBannerAdsFactory.setBannerListener(this);
```

* **Kotlin**

```java
mngAdsBannerAdsFactory.setBannerListener(this)
```

The SDK will notify your Listener of all possible events listed below :

- bannerDidLoad(): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.

* **Java**

```java
@Override
public void bannerDidLoad(View adView ,int preferredHeightDP){
Log.d(TAG, "your banner is ready");
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
...
adLayout.addView(adView);
}
```

* **Kotlin**

```java
override fun bannerDidLoad(view: View, preferredHeightDP: Int){
Log.d(TAG, "your banner is ready")
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
...
adLayout.addView(adView)
}
```

- bannerDidFail(): will be called when all ads servers fail. it will return the error of last called ads server.

* **Java**

```java
@Override
public void bannerDidFail(Exception adsException) {
Log.e(TAG, "banner did fail :" + adsException.toString());
}
```

* **Kotlin**

```java
override fun bannerDidFail(e: Exception) {
Log.e(TAG, "banner did fail :" + adsException.toString())
}
```

- bannerResize() : will be called when the banner has changed size

* **Java**

```java
@Override
public void bannerResize(MNGFrame frame) {
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
Log.d(TAG, "Banner did resize w dp " + frame.getWidth() + " h dp " + frame.getHeight());
...
}
```

* **Kotlin**

```java
override fun bannerResize(frame: MNGFrame) {
...
// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
Log.d(TAG, "Banner did resize w dp " + frame.width + " h dp " + frame.height)
...
}
```


## Step 4. Loading Banner ad

To make a request you have to call 'loadBanner' using the mng banner size. (in this example it???s the BANNER size used):

* **Java**

```java
mngAdsBannerAdsFactory.loadBanner(MNGAdSize.MNG_DYNAMIC_BANNER);

```

* **Kotlin**

```java
mngAdsBannerAdsFactory.loadBanner(MNGAdSize.MNG_DYNAMIC_BANNER)

```

**Note:** if your application support different screen sizes on Tablet and Phone, it is better to use this code :

* **Java**

```java
MNGFrame  mMNGAdSize = getResources().getBoolean(R.bool.is_tablet) ? MNGAdSize.MNG_DYNAMIC_LEADERBOARD : MNGAdSize.MNG_DYNAMIC_BANNER ;
mngAdsBannerAdsFactory.loadBanner(mMNGAdSize);

```

* **Kotlin**

```java
val mNGAdSize: MNGFrame = resources.getBoolean(R.bool.is_tablet) ? MNGAdSize.MNG_DYNAMIC_LEADERBOARD : MNGAdSize.MNG_DYNAMIC_BANNER
mngAdsBannerAdsFactory.loadBanner(mNGAdSize)

```

### MNGAdSize
Mng ads provides variant pre-defined sizes, See table below for details about our supported standard banner sizes:


| MNGAdSize | Description |Dimensions in dp (WxH)
| --- | --- | --- |
| MNG_BANNER	| Standard Banner	 | 320 x 50 |
| MNG_LARGE_BANNER  | Large Banner |320 x 100 |
| MNG_MEDIUM_RECTANGLE   | Medium Rectangular Banner	 |300 x 250 |
| DYNAMIC_BANNER |Adjusted Banner| Screen width x 50 |
| MNG_FULL_BANNER	| Full Banner  | 468 x 60 |
| LEADERBOARD	| Standard Banner for tablet	 | 728 x 90 |
| MNG_DYNAMIC_LEADERBOARD	| Adjusted Banner for tablet	 | Screen width x 90 |



## Troubleshooting

### Memory managment
When you have finished your ads plant you must free the memory.

* **Java**

```java
@Override
protected void onDestroy() {
mngAdsBannerAdsFactory.releaseMemory();
super.onDestroy();
}
```

* **Kotlin**

```java
override fun onDestroy() {
mngAdsBannerAdsFactory.releaseMemory()
super.onDestroy()
}
```

### Adapt the banner size after loading

You can resize the Banner View height to match the creative's width/height ratio, this is often the case when your Banner View needs to deliver view over 50 dp. (This does not happen when setting your view as wrap_content)

Here's an example:

*XML Code :*


```xml
<LinearLayout
                android:id="@+id/bannerContainer"
                android:gravity="center"
                android:orientation="vertical"
                android:layout_width="match_parent"
                android:layout_height="50dp"/>
```

*JAVA Code :*

```java
@Override
public void bannerResize(MNGFrame frame) {
bannerContainer.getLayoutParams().height = frame.getHeight();
bannerContainer.requestLayout();
}
```

**OR**


```java
@Override 
public void bannerDidLoad(final View view, int preferredHeightDP) {
bannerContainer.getLayoutParams().height = preferredHeightDP;
bannerContainer.requestLayout();
}
```

*Kotlin Code :*

```java
override fun bannerResize(frame : MNGFrame) {
bannerContainer.layoutParams.height = frame.height
bannerContainer.requestLayout()
}
```

**OR**


```java
override fun bannerDidLoad(view: View, preferredHeightDP: Int) {
bannerContainer.layoutParams.height = preferredHeightDP
bannerContainer.requestLayout()
}
```

### isBusy

Before making a request if you want to check that factory is not busy (Ads factory is busy means that it has not finished the previous request yet).

isBusy will be set to :

- **true :** when factory starts handling request.

- **false :** when factory finishes handling request.

**Example**:

* **Java**

```java
if (!mngAdsBannerAdsFactory.isBusy()) {

Log.d(TAG, "Ads Factory is not busy");
mngAdsBannerAdsFactory.loadInterstitial(false);
} else {
Log.d(TAG, "Ads Factory is busy");
}
```

* **Kotlin**

```java
if (!mngAdsBannerAdsFactory.isBusy()) {
Log.d(TAG, "Ads Factory is not busy")
mngAdsBannerAdsFactory.loadInterstitial(false)
} else {
Log.d(TAG, "Ads Factory is busy")
}
```

### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked

* **Java**

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

* **Kotlin**

```java
// set click listener
mngAdsBannerAdsFactory.setClickListener(this)


...
override fun onAdClicked() {
Log.d(TAG, "Ad Clicked")
}
...
```

### Ad refresh listener
You can also implement MNG refresh listener callback to detect when an Ad refreshed

* **Java**

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

* **Kotlin**

```java
// set refresh listener
mngAdsBannerAdsFactory.setRefreshListener(this)

...
override fun onRefreshSucceed() {
Log.d(TAG, "refresh succeed")
}

override fun onRefreshFailed(e: Exception) {
Log.d(TAG, "refresh failed")
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


* **Java**

```java

Location  myLocation = new Location("I");
myLocation.setLatitude(35.757866);
myLocation.setLongitude(10.810547);

MNGPreference mngPreference = new MNGPreference();
mngPreference.setLocation(location,CONSENT_FLAG,context);
mngPreference.setAge(28);
mngPreference.setGender(MNGGender.MNGGenderFemale);
mngPreference.setKeyword("brand=myBrand;category=sport");
mngPreference.setContentUrl("put your content url here");


mngAdsBannerAdsFactory.loadBanner(new MNGFrame(320, 50), mngPreference);

```

* **Kotlin**

```java

val myLocation = Location("I")
myLocation.setLatitude(35.757866)
myLocation.setLongitude(10.810547)

val mngPreference = MNGPreference()
mngPreference.setLocation(location,CONSENT_FLAG,context)
mngPreference.setAge(28)
mngPreference.setGender(MNGGender.MNGGenderFemale)
mngPreference.setKeyword("brand=myBrand;category=sport")
mngPreference.setContentUrl("put your content url here")


mngAdsBannerAdsFactory.loadBanner(MNGFrame(320, 50), mngPreference)

```

**Note :** 

- This [link] can help you to get device location.

- Do not serialize Location object (like transforming it into a string using gson library), this may lead to a fatal runtime error when that instance is reused.

- The setLocation method takes the following parameters:

	- the Location instance.
	- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3).
		- 0 = Not allow to send location.
		- 1 = When you managed location according to consent value.
		- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

	- the Context instance.

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

* **Java**

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

* **Kotlin**

```java
override fun interstitialDidFail(e: Exception) {

val adException = e as MAdvertiseException

when (adException.errorCode){
MAdvertiseException.BUSY_FACTORY_ERROR -> {...}
MAdvertiseException.INTERSTITIAL_ALREADY_SHOWN_ERROR -> {...}
.
.
.

}
Log.e(TAG, "Interstitial did fail : ${adException.message} error code ${adException.errorCode}")

}
```

### Remove Banner View
If you like to Remove banner from the view, you can use this code : 

* **Java**

```java
...  
adLayout.removeView(adView);  
adLayout.requestLayout();
...
```

* **Kotlin**

```java
...  
adLayout.removeView(adView) 
adLayout.requestLayout()
...
```


### How to adapt the banner size after loading

- In the example below we use preferredHeightDP  parameter to adapt the banner size after loading
- The best place to add the resizing code is in your bannerDidLoad listener.
- This is often the case when your Banner Ad needs to deliver 300x50, 300x250 formats or even 16/9 video,...
 
* **Java**

```java
@Override
public void bannerDidLoad(final View view, int preferredHeightDP) {

// convert Dp To Pixel 

Resources resources = context.getResources();
DisplayMetrics metrics = resources.getDisplayMetrics();
float bannerPreferredHeightPx = preferredHeightDP * (metrics.densityDpi / 160f);

// adapt the banner size
              
bannerContainer.getLayoutParams().height = bannerPreferredHeightPx;
bannerContainer.requestLayout();

}
```

* **Kotlin**

```java
override fun bannerDidLoad(view: View, preferredHeightDP: Int) {

// convert Dp To Pixel 

val resources = context.resources
val metrics: DisplayMetrics = resources.displayMetrics
val bannerPreferredHeightPx = preferredHeightDP * (metrics.densityDpi / 160f)

// adapt the banner size
              
bannerContainer.layoutParams.height = bannerPreferredHeightPx
bannerContainer.requestLayout()

}
```


# Example

 - https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/BannerFragment.kt

Example | Description| 
------------- | ------------- |
![banner50-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/288211594-banner50-mngads-android-min.png) Banner -  (50dp  or 90dp )  | A banner is a small bar ad that appears at the bottom or top of your content. Usually sized 320 x 50. Only include one ad per page or show one ad at a time if scrolling. In all cases, **the banner width is flexible with a minimum of 320px.**. If you are building your app for iPad  consider using 90px and 50px for iphone. 
 ![banner250-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/4181983461-banner250-mngads-android-min.png) Square - Medium rectangle (300 x 250) |Square banner also known as a *medium rectangle* (300 x 250). This format can increase earnings when both text and image ads are enabled. Performs well when embedded within text content or at the end of articles.


[AdsFragment.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.kt?at=master
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
[ApplicationManager.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/utils/ApplicationManager.kt?at=master&fileviewer=file-view-default
[BaseActivity.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/BaseActivity.kt?at=master&fileviewer=file-view-default
[Interstitial Guideline]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial-guideline
[see Proguard rules on our faq]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-if-your-app-uses-proguard-you-must-edit-your-proguard-settings-to-avoid-stripping-google-play-out-of-your-app
[more details about instance on our FAQ]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-interstitial-did-load-callback-without-display
[umooveVx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[build.gradle]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/build.gradle?at=master&fileviewer=file-view-default
[Mopub Marketplace]:https://www.mopub.com/
[AdColony]:https://www.adcolony.com/