#![MNG-Ads-1.png](https://bitbucket.org/repo/aen579/images/3739691856-MNG-Ads-1.png) for Android

MNG Ads provides functionalities for monetizing your mobile application: from premium sales with reach media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. MngAds SDK is a library that allow you to handle the following Ads servers with the easy way :

- [Smart ads server]
- [Google DFP]
- [Facebook Audience Network]
- [Mng-perf]
- [Appsfire]

![mng-ads-state-diagram.png](https://bitbucket.org/repo/aen579/images/949359413-mng-ads-state-diagram.png)

It contains a dispacher that will select an ads server according to the priority and state.

## Version
v1.0. See [Change Log] and [Upgrade Guide].

## Manual Install

- download [mng-ads.jar Android SDK] from our demo project, **you must use version of  Ads servers's librairies in used on demo project.**
- drag and drop it in your project libs folder


MngAds SDK needs:

- [Google-play-services_lib]
- [SmartAdServer-Android-SDK-5.0.1.jar]
- [mngperf-android-sdk.jar]
- [AudienceNetwork.jar]
- [afAdSdk.jar]
- [Android-support-v4.jar]

## Sample Application

Included is a [MngAds sample app] to use as example and for help on MngAds integration. This basic application allows users to test our differents formats.

## Start Integrating

### Initializing the SDK

You have to init the SDK in your application class
```Android
//
#import com.mngads.MNGAdsFactory;
...
public class DemoApp extends Application{
@Override
	public void onCreate() {
		super.onCreate();
		MNGAdsFactory.initialize(this,"YOUR_APP_ID");
	}
}
```
#### Timeout
The time given to the ad view to download the ad data. After this time, the dispacher stops the ad server running (with failure) and move to the next.

the default timeout is 1s.
```Android
public class MainActivity extends Activity{
    private MNGAdsFactory mngAdsBannerAdsFactory;
...	
// init banner factory
    mngAdsBannerAdsFactory = new MNGAdsFactory(this);
    mngBannerAdsFactory.setTimeOut(3);
```
#### isBusy
Before making a request you have to check that factory not busy (handling old request).

Ads factory is busy means that it has not finished the previous request yet.

isBusy will be setted to true when factory start handling request.

isBusy will be setted to false when factory finish handling request.
##### example:
```Android
	if (!mngAdsBannerAdsFactory.isBusy()) {
		Log.d(TAG, "Ads Factory is not busy");
		mngAdsBannerAdsFactory.createBanner(new MNGFrame(320, 50));
	} else {
		Log.d(TAG, "Ads Factory is busy");
	}
```

### Banner
#####Init factory

To create a banner you have to init an object with type MNGAdsSDKFactory and set the bannerListener and the context.

```Android
public class MainActivity extends Activity implements MNGBannerListener{
...
    private MNGAdsFactory mngAdsBannerAdsFactory;
@Override
    protected void onCreate(Bundle savedInstanceState) {
...
// init banner factory
    mngAdsBannerAdsFactory = new MNGAdsFactory(this);
// set banner listener
    mngAdsBannerAdsFactory.setBannerListener(this);

```
You have also to set placementId (minimum one time)

```Android
    mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request
To make a request you have to call 'createBanner'. this method return a bool value (canHandleRequest) 

```Android
if(mngAdsBannerAdsFactory.createBanner(new MNGFrame(320, 50))){
    //Wait callBack from listener
}else{
    //adsFactory can not handle your request
}
```

#####Handle callBack from BannerListener
adsAdapter.bannerDidLoad(View adView): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.
```Android
	@Override
	public void bannerDidLoad(View adView) {
		Log.d(TAG, "your banner is ready")
		adLayout.removeAllViews();
		adLayout.addView(adView);
	}
```

adsAdapter.bannerDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```Android
	@Override
	public void bannerDidFail(Exception adsException) {
		Log.e(TAG, "banner did fail :" + adsException.toString());
	}
```

### Interstitial
#####Init factory

To create a interstitial you have to init an object with type MNGAdsSDKFactory and set the interstitalListener and the context.

```Android
public class MainActivity extends Activity implements MNGInterstitialListener{
...
    private MNGAdsFactory mngAdsInterstitialAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
// init intertitial factory
	mngAdsInterstitialAdsFactory = new MNGAdsFactory(this);

// set intertitial listener
	mngAdsInterstitialAdsFactory.setInterstitialListener(this);
```
#####Make a request 
To make a request you have to call 'createInterstitial()'. this method return a bool value (canHandleRequest).

```Android
    if (!mngAdsInterstitialAdsFactory.isBusy()) {
	mngAdsInterstitialAdsFactory.createInterstitial();
	}
```
#####Handle callBack from InterstitialListener
adsAdapter.InterstitialDidLoad(): will be called by the SDK when your Interstitial is ready.
```Android
@Override
	public void interstitialDidLoad() {
		Log.d(TAG, "interstitial did load");
	}
```

adsAdapter.interstitialDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```Android
@Override
	public void interstitialDidFail(Exception adsException) {
		Log.e(TAG, "interstitial did fail :" + adsException.toString());
	}
```
adsAdapter.InterstitialDisappear(): will be called when intertisialView did disappear. now you can update your UI for example.

```Android
@Override
	public void interstitialDisappear() {
		Log.d(TAG, "interstitial disappear")
	}
```

### Native Ads
Native ads give you the control to design the perfect ad units for your app. With our Native Ad API, you can determine the look and feel, size and location of your ads. Because you decide how the ads are formatted, ads can fit seamlessly in your application.
#####Init factory

To create a nativeAd  you have to init an object with type MNGAdsSDKFactory and set the nativeListener.

```Android
public class MainActivity extends Activity implements MNGNativeListener{
...
   private MNGAdsFactory mngAdsNativeAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
	// init native factory
		mngAdsNativeAdsFactory = new MNGAdsFactory(this);

	// set native listener
		mngAdsNativeAdsFactory.setNativeListener(this);

```
You have also to set placementId (minimum one time)

```Android
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request
To make a request you have to call 'createNative()'. this method return a bool value (canHandleRequest) 

```Android
if(mngAdsNativeAdsFactory.createNative()){
//Wait callBack from native listener
}else{
//adsFactory can not handle your request
}
```

#####Handle callBack from NativeListener
adsAdapter.nativeObjectDidLoad(): will be called by the SDK when your nativeObject is ready. now you can create your own view.
```Android
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
		Log.d(TAG, "native Object did load ");
	}

```

adsAdapter.nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```Android
@Override
	public void nativeObjectDidFail(Exception adsException) {
		Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
	}

```
#### Preferences Object
Preferences object is an optional parameter that allow you select ads by user info.
informations that you can set are:

- age : age of user
- location : user location
- language : language of user
- gender : gender of user

```Android
#import com.mngads.util.MNGPreference;
#import com.mngads.util.MNGGender;
...
        myLocation = new Location("I");
		myLocation.setLatitude(35.757866);
		myLocation.setLongitude(10.810547);
		mngPreference = new MNGPreference();
		mngPreference.setLocation(myLocation);
		mngPreference.setAge(28);
		mngPreference.setGender(MNGGender.MNGGenderFemale);
		mngPreference.setLanguage("fr");

```
`Note`: this [link] can help you to get device location.
####Memory managment
When you have finished your ads plant you must free the memory.

```Android
@Override
	protected void onDestroy() {
		mngAdsBannerAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactory.releaseMemory();
		mngAdsNativeAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactoryOverlay.releaseMemory();
		super.onDestroy();
	}
```
####MAndroidManifest.xml
To make ad request we need to add the following permission to MAndroidManifest.xml file
```Android

...
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" >
    </uses-permission>
    <uses-permission android:name="android.permission.INTERNET" >
    </uses-permission>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" >

   
    ...
    <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
    ...
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
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" >
        </activity>
        <activity
            android:name="com.google.android.gms.ads.AdActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    <activity
            android:name="com.facebook.ads.InterstitialAdActivity"
            android:configChanges="keyboardHidden|orientation" />
            <!-- Apps targeting api v13 and higher should add '|screenSize' to the InterstitialAdActivity configChanges to support video                  rotation -->
    ...
  
 ```

[link]:https://developer.android.com/training/location/retrieve-current.html
[Smart ads server]:http://help.smartadserver.com/fr/Default.htm#../../../../specifications/Content/MobileSpecifications/Apps.htm
[Mng-perf]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/mngperf-android-sdk.jar?at=master
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mng-ads.jar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/mng-ads.jar?at=master
[MngAds sample app]:https://bitbucket.org/mngcorp/mngads-demo-android/src
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
[Change Log]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/change-log
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/AudienceNetwork.jar?at=master
[mngperf-android-sdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/mngperf-android-sdk.jar?at=master
[afAdSdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/afAdSdk.jar?at=master
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/MngAdsDemo/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/29b7e153ea309f2dc430c879d1484a1cf1f29e84/google-play-services_lib/?at=master