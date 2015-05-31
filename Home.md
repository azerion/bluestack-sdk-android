#![MNG-Ads-1.png](https://bitbucket.org/repo/aen579/images/3739691856-MNG-Ads-1.png) for Android

MNG Ads provides functionalities for monetizing your mobile application: from premium sales with reach media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. MngAds SDK is a library that allow you to handle the following Ads servers with the easy way :

- [Smart ads server]
- [Google DFP]
- [Facebook Audience Network]
- [Mng-perf]
- [Appsfire]
- [AppNexus]
- [Retency]

It contains a dispacher that will select an ads server according to the priority and state ([mngAds state diagram]).

## Version
v1.3.1 See [Change Log] and [Upgrade Guide].

## Ad Examples and inspiration

[Design ad units to fit your app]. You can see [Best practice Mngads], an optimized use case for several ad formats on one page.

## Manual Install

- download [mng-ads.jar Android SDK] from our demo project, **you must use version of  Ads servers's librairies in used on demo project.**
- drag and drop it in your project libs folder


MngAds SDK needs:

- [Google-play-services_lib]
- [SmartAdServer-Android-SDK-5.0.3.jar] (>= 5..0.3 for lollipop support)
- [mngperf-android-sdk.jar]
- [AudienceNetwork.jar]
- [afAdSdk.jar]
- [Android-support-v4.jar]
- [AppNexus-sdk]
- [Retency-sqk]

## Sample Application

Included is a [MngAds sample app] to use as example and for help on MngAds integration. This basic application allows users to test our differents formats.

## Start Integrating

### Initializing the SDK

You have to init the SDK in your application class


```
#!java

#import com.mngads.MNGAdsFactory;

public class DemoApp extends Application{
@Override
	public void onCreate() {
		super.onCreate();
		MNGAdsFactory.initialize(this,"YOUR_APP_ID");
	}
}
```

#### Initialize Check

To verify if the SDK is fully initialized you have to call isInitialized():

```
#!java

public class MainActivity extends Activity implements MNGAdsSDKFactoryListener{
   
...	


	if(MNGAdsFactory.isInitialized()){

	    //The SDK is not initialized
            Toast.makeText(this, "MNGAdsFactory is initialized", Toast.LENGTH_SHORT).show();

        }else {
	   
	    //The SDK is initializing
	    //set up a callback	that will be called when is fully initiamized
            MNGAdsFactory.setMNGAdsSDKFactoryListener(this);

            Toast.makeText(this, "MNGAdsFactory is not initialized", Toast.LENGTH_SHORT).show();

        }




   @Override
    public void onMNGAdsSDKFactoryDidFinishInitializing() {

        mHandler.post(new Runnable() {
            @Override
            public void run() {

                Toast.makeText(MainActivity.this, "MNGAds SDK Factory Did Finish Initializing", Toast.LENGTH_SHORT).show();
            }
        });


        Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
    }


```



#### Timeout
The time given to the ad view to download the ad data. After this time, the dispacher stops the ad server running (with failure) and move to the next.

the default timeout is 1s.

```
#!java

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
```
#!java
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

```
#!java
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

```
#!java
    mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request
To make a request you have to call 'createBanner'. this method return a bool value (canHandleRequest) 

```
#!java
if(mngAdsBannerAdsFactory.createBanner(new MNGFrame(320, 50))){
    //Wait callBack from listener
}else{
    //adsFactory can not handle your request
}
```

#####Handle callBack from BannerListener
adsAdapter.bannerDidLoad(View adView): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.
```
#!java
	@Override
	public void bannerDidLoad(View adView) {
		Log.d(TAG, "your banner is ready")
		adLayout.removeAllViews();
		adLayout.addView(adView);
	}
```

adsAdapter.bannerDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```
#!java
	@Override
	public void bannerDidFail(Exception adsException) {
		Log.e(TAG, "banner did fail :" + adsException.toString());
	}
```

### Interstitial
#####Init factory

To create a interstitial you have to init an object with type MNGAdsSDKFactory and set the interstitalListener and the context.

```
#!java
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

```
#!java
    if (mngAdsInterstitialAdsFactory.createInterstitial()) {
	   //Wait callBack from interstitial listener
     }else{
        //adsFactory can not handle your request
    }
```
#####Handle callBack from InterstitialListener
adsAdapter.InterstitialDidLoad(): will be called by the SDK when your Interstitial is ready.
```
#!java
@Override
	public void interstitialDidLoad() {
		Log.d(TAG, "interstitial did load");
	}
```

adsAdapter.interstitialDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```
#!java
@Override
	public void interstitialDidFail(Exception adsException) {
		Log.e(TAG, "interstitial did fail :" + adsException.toString());
	}
```
adsAdapter.InterstitialDisappear(): will be called when intertisialView did disappear. now you can update your UI for example.

```
#!java
@Override
	public void interstitialDisappear() {
		Log.d(TAG, "interstitial disappear")
	}
```

### Interstitial Overlay
#####Init factory

To create a interstitial overlay you have to init an object with type MNGAdsSDKFactory and set the interstitalListener and the context.Note that you must use the same instance for making and handling the request.

```
#!java
public class MainActivity extends Activity implements MNGInterstitialListener{
    ...
    private MNGAdsFactory mngAdsInterstitialOverlayAdsFactory;
        @Override
         protected void onCreate(Bundle savedInstanceState) {
    ...
        // init intertitial factory
    	mngAdsInterstitialOverlayAdsFactory = new MNGAdsFactory(this);

         // set intertitial listener
    	mngAdsInterstitialOverlayAdsFactory.setInterstitialListener(this);
```
#####Make a request 
To make a request you have to call 'createInterstitial()'. this method return a bool value (canHandleRequest).The interstitial will appear every n(capping) request

```
#!java
    if (mngAdsInterstitialOverlayAdsFactory.createInterstitial()) {
	   //Wait callBack from interstitial listener
     }else{
        //adsFactory can not handle your request
    }
```
#####Handle callBack from InterstitialListener
adsAdapter.InterstitialDidLoad(): will be called by the SDK when your Interstitial is ready.
```
#!java
@Override
	public void interstitialDidLoad() {
		Log.d(TAG, "interstitial did load");
	}
```

adsAdapter.interstitialDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```
#!java
@Override
	public void interstitialDidFail(Exception adsException) {
		Log.e(TAG, "interstitial did fail :" + adsException.toString());
	}
```
adsAdapter.InterstitialDisappear(): will be called when intertisialView did disappear. now you can update your UI for example.

```
#!java
@Override
	public void interstitialDisappear() {
		Log.d(TAG, "interstitial disappear")
	}
```



### Native Ads
Native ads give you the control to design the perfect ad units for your app. With our Native Ad API, you can determine the look and feel, size and location of your ads. Because you decide how the ads are formatted, ads can fit seamlessly in your application.
#####Init factory

To create a nativeAd  you have to init an object with type MNGAdsSDKFactory and set the nativeListener.

```
#!java
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

```
#!java
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request for native ad
To make a request you have to call 'createNative()'. this method return a bool value (canHandleRequest) 

```
#!java
    if(mngAdsNativeAdsFactory.createNative()){
        //Wait callBack from native listener
    }else{
        //adsFactory can not handle your request
    }
```
#####Handle callBack from NativeListener
adsAdapter.nativeObjectDidLoad(): will be called by the SDK when your nativeObject is ready. now you can create your own view.
```
#!java
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
		Log.d(TAG, "native Object did load ");
	}

```

adsAdapter.nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```
#!java
@Override
	public void nativeObjectDidFail(Exception adsException) {
		Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
	}

```

### Native Collection Ads  
Native collection ads give you the control to design the perfect ad carousel for your app. 
#####Init factory

To create nativeAd collection you have to init an object with type MNGAdsSDKFactory and set the nativeCollectionListener.

```
#!java
public class MainActivity extends Activity implements MNGNativeCollectionListener{
...
   private MNGAdsFactory mngNativeAdCollectionFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
	// init native factory
		mngNativeAdCollectionFactory = new MNGAdsFactory(this);

	// set native listener
		mngNativeAdCollectionFactory.setNativeListener(this);

```
You have also to set placementId (minimum one time)

```
#!java
  mngNativeAdCollectionFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request for collection of native ad (**carousel**)
To make a request you have to call 'createNativeCollection(int requestedAdNumber)'. this method return a bool value (canHandleRequest) 

```
#!java
    if(mngAdsNativeAdsFactory.createNativeCollection(int requestedAdNumber){
        //Wait callBack from native collection listener
    }else{
        //adsFactory can not handle your request
    }
```
#####Handle callBack from NativeCollectionListener
adsAdapter.nativeAdCollectionDidLoad(): will be called by the SDK when your collection is ready. now you can create your own views.
```
#!java
@Override
	public void nativeAdCollectionDidLoad(ArrayList<MNGNativeObject> nativeObjectCollection) {
		Log.d(TAG, "native collection did load ");
	}

```

adsAdapter.nativeAdCollectionDidFail(Exception adsCollectionException): will be called when the factory fail to return any native object
```
#!java
@Override
	public void nativeAdCollectionDidFail(Exception adsCollectionException) {
		Log.e(TAG, "native collection Did Fail :"+ adsCollectionException.toString());
	}

```
	
#### Preferences Object
Preferences object is an optional parameter that allow you select ads by user info.
informations that you can set are:

- age : age of user
- location : geographical position of the user.
- language : language of user (ISO code)
- gender : gender of user
- keyWord : Use free-form key-values when you want to pass targeting values dynamically into an ad tag based on information you collect from your users. You can also use free-form key-values when there are too many possible values to define in advance. Separator in case of multiple entries is **;**. 


```
#!java
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
 		mngPreference.setKeyword("brand=myBrand;category=sport");
		mngPreference.setLanguage("fr");

```
`Note`: this [link] can help you to get device location.
####Memory managment
When you have finished your ads plant you must free the memory.

```
#!java

@Override
	protected void onDestroy() {
		mngAdsBannerAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactory.releaseMemory();
		mngAdsNativeAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactoryOverlay.releaseMemory();
		super.onDestroy();
	}
```

####Enabling debug mode
To enbale debug mode you need to set debug mode to true :

```
#!java

...

MNGAdsFactory.setDebugModeEnabled(true);

...

```

####MAndroidManifest.xml

To make ad request we need to add the following permission to AndroidManifest.xml file :

```
#!XML

<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    ...


    <!--Grants the SDK permission to access information about Wi-Fi networks. -->
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    <!--Grants the SDK permission to check for a live internet connection. -->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <!--Grants the SDK permission to access the internet. -->
    <uses-permission android:name="android.permission.INTERNET"/>
    <!--Grants the SDK permission to access approximate location based on cell tower. -->
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <!--Grants the SDK permission to access a more accurate location based on GPS. -->
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>	

    ...

  <application
        android:name=".DemoApp"
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.Sherlock"
        android:largeHeap="true" <!-- use this if only you feel that your app might need it  -->  
        >

    ...
    <!--Grants the SDK permission to start mng analytics service -->
    <service android:name="com.mngads.service.MNGAnalyticsService"/>
    ...


    <!--This embeds the version of Google Play services that the app was compiled with.. -->
    <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
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
        
    <!--DFP SDK Ad activity  -->
    <activity
            android:name="com.google.android.gms.ads.AdActivity" android:theme="@android:style/Theme.Translucent"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    <!--Facebook SDK Ad activity  -->
    <activity
            android:name="com.facebook.ads.InterstitialAdActivity"
            android:configChanges="keyboardHidden|orientation" />
            <!-- Apps targeting api v13 and higher should add '|screenSize' to the InterstitialAdActivity configChanges to support  	  video rotation -->


    <!--Retency SDK Ad activitys  -->
    <activity android:name="com.retency.sdk.android.banner.InAppWebView"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />

    <activity android:name="com.retency.sdk.android.video.RichMediaActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:hardwareAccelerated="false" />

    <activity android:name="com.retency.sdk.android.mraid.MraidBrowser"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />



    ...

```

```

[link]:https://developer.android.com/training/location/retrieve-current.html
[Smart ads server]:http://help.smartadserver.com/fr/Default.htm#../../../../specifications/Content/MobileSpecifications/Apps.htm
[Mng-perf]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/mngperf-android-sdk.jar?at=master
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mng-ads.jar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/mng-ads-sdk.jar?at=master
[MngAds sample app]:https://bitbucket.org/mngcorp/mngads-demo-android/src
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
[Change Log]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/change-log
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/AudienceNetwork.jar?at=master
[mngperf-android-sdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/mngperf-android-sdk.jar?at=master
[afAdSdk.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/afAdSdk.jar?at=master
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[SmartAdServer-Android-SDK-5.0.3.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/SmartAdServer-Android-SDK-5.0.4.jar?at=master
[Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/inspiration
[mngAds state diagram]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/diagram
[AppNexus]:http://www.appnexus.com/fr
[AppNexus-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/sdk/?at=master
[Retency]:http://www.retency.com/public/
[Retency-sqk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/retency-sdk.jar?at=master
[Best practice Mngads]:https://bitbucket.org/anypli/mng-ads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.java?at=master
