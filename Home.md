![MNG-Ads-1.png](https://bitbucket.org/repo/aen579/images/3739691856-MNG-Ads-1.png) for Android

[TOC]


MNG Ads provides functionalities for monetizing your mobile application: from premium sales with rich media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. MngAds SDK is a library that allow you to handle the following Ads servers with the easy way :

- [Smart ads server]
- [Google DFP]
- [Facebook Audience Network]
- [Amazon]
- [Liverail]
- [Flurry]
- [Retency]
- [Ogury] Note : An API Key will be assigned to your application by mngads support team for Ogury library.


It contains a dispacher that will select an ads server according to the priority and state ([mngAds state diagram]).

## Version
See [Change Log] and [Upgrade Guide].

NOTE :MNG Ads requires minimum Android API level 11

## Ad Examples and inspiration

You can see [Best practice Mngads and Design ad units to fit your app], an optimized use case for several ad formats on one page.

## Manual Install

- download [mng-ads.jar Android SDK] from our demo project, **you must use version of  Ads servers's librairies in used on demo project.**
- drag and drop it in your project libs folder


MngAds SDK requeire:

- Google-play-services_lib (com.google.android.gms:play-services:8.4.0)
- [SmartAdServer-Android-SDK.jar]
- [AudienceNetwork.jar]
- com.android.support:support-v4:23.+
- [Retency-sdk]
- [Amazon.jar]
- [Liverail.jar]
- [FlurryAds.jar] and [FlurryAnalytics.jar]
- [Presage-lib.jar]

Gradle:
  * The available librairies via Maven are : 

    - Google-Play-Services
    - Android-Support
    - AudienceNetwork


You must add ( drag and drop ) the other librairies in your project libs folder.
 
  Add this to Module-level /app/build.gradle before dependencies
```
#!groovy
repositories {
	mavenCentral() 
}
```
  Add the compile dependency in the build.gradle file:
```
#!groovy
dependencies { 

  //Google Play Services
  compile 'com.google.android.gms:play-services:8.4.0'
  // or you can use compile 'com.google.android.gms:play-services-ads:8.4.0'
  
  //Android support v4
 compile 'com.android.support:support-v4:23.+'
 
 // Audience Network 
  compile 'com.facebook.android:audience-network-sdk:4.9.0'
}
```


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

### Initialize Check

To verify if the SDK is fully initialized you have to call isInitialized():

```
#!java

public class MainActivity extends Activity implements MNGAdsSDKFactoryListener{
   
...	


	if(MNGAdsFactory.isInitialized()){

	    //The SDK is initialized
            Toast.makeText(this, "MNGAdsFactory is initialized", Toast.LENGTH_SHORT).show();

        }else {
	   
	    //The SDK is initializing
	    //set up a callback	that will be called when is fully initiamized
            MNGAdsFactory.setMNGAdsSDKFactoryListener(this);

            Toast.makeText(this, "MNGAdsFactory is not initialized", Toast.LENGTH_SHORT).show();

        }




   @Override
    public void onMNGAdsSDKFactoryDidFinishInitializing() {

       
           Toast.makeText(MainActivity.this, "MNGAds SDK Factory Did Finish Initializing", Toast.LENGTH_SHORT).show();
        	
           Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
    }


```

`Note`: onMNGAdsSDKFactoryDidFinishInitializing(): this method is called at any time when the initialize(...) method of MNG gets called



### Timeout
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

### isBusy
Before making a request you have to check that factory not busy (handling old request).

Ads factory is busy means that it has not finished the previous request yet.

isBusy will be setted to true when factory start handling request.

isBusy will be setted to false when factory finish handling request.
**example**:
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
#### Init factory

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
#### Make a request
To make a request you have to call 'createBanner'. this method return a bool value (canHandleRequest) 

```
#!java
if(mngAdsBannerAdsFactory.createBanner(new MNGFrame(320, 50))){
    //Wait callBack from listener
}else{
    //adsFactory can not handle your request
}
```

####Handle callBack from BannerListener
**v1.5.1 or above**
adsAdapter.bannerDidLoad(View adView) changed to adsAdapter.bannerDidLoad(View adView,int preferredHeightDP).
adsAdapter.bannerDidLoad(View adView,int preferredHeightDP): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.
```
#!java
	@Override
	 public void bannerDidLoad(View adView ,int preferredHeightDP);
		Log.d(TAG, "your banner is ready")
		...
		// it's preferable to adjust the ad container view size to match the returned Ad size for a better display
		...
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
**v1.5.1 or above** 
adsAdapter.bannerResize(MNGFrame frame) : will be called when the banner has changed size
```
#!java
	 @Override
    public void bannerResize(MNGFrame frame) {
    ...
        // it's preferable to adjust the ad container view size to match the returned Ad size for a better display
        Log.d(TAG, "Banner did resize w dp " + frame.getWidth() + " h dp " + frame.getHeight());
    ...
    }
```

### Interstitial
#####Init factory

To create a interstitial you must init an object with type MNGAdsSDKFactory and set the interstitalListener and the context.

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
To make a request you must call 'createInterstitial()'. this method return a bool value (canHandleRequest).

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

To create an interstitial overlay you must init an object with type MNGAdsSDKFactory and set the interstitalListener and the context.Note that you must use the same instance for making and handling the request.

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
To make a request you must call 'createInterstitial()'. this method return a bool value (canHandleRequest).The interstitial will appear every n(capping) request

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

###Show Interstitial after return from background

You can see [Interstitial Guideline] and our demo app with following files

 - [ApplicationManager.java]
 - [BaseActivity.java]

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
#####Build Native Ad UI
MNGNativeObject have all required metadata to build your customized native UI.
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
    String coverImageUrl=nativeObject.getAdCoverImageUrl();
    
    //to handle impression and user interaction you have to call 
    nativeObject.registerViewForInteraction(nativeAdCallToActionView);
   ...
}
```

##### v2.0 or above
You can also integrate video ads into your Native Ad experience. To enable video you must complete the following steps:

- Have SDK version 2.0 or later
- You have to call setMediaContainer(viewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result
 
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

See [Native Ads guidelines]


### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked
```
#!java
public class MainActivity extends Activity implements MNGClickListener{
...
   private MNGAdsFactory mngAdsAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
    // init MNG factory
        mngAdsAdsFactory = new MNGAdsFactory(this);

    // set click listener
        mngAdsNativeAdsFactory.setClickListener(this);
}

...
    @Override
    public void onAdClicked() {

        Log.d(TAG, "Ad Clicked");

    }
...
```
### Preferences Object
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
### Memory managment
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

### Enabling debug mode
To enbale debug mode you need to set debug mode to true :

```
#!java

...

MNGAdsFactory.setDebugModeEnabled(true);

...

```

### MAndroidManifest.xml

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
    <!-- External storage is used for pre-caching features if available -->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
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
        android:name=".DemoApp"
        android:allowBackup="true"
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
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
        <activity
            android:name="com.retency.sdk.android.video.RichMediaActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:hardwareAccelerated="false" />

        <activity
            android:name="com.retency.sdk.android.mraid.MraidBrowser"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />

        <!--Amazon SDK Ad activity  -->
        <activity
            android:name="com.amazon.device.ads.AdActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"/>

        <!--Flurry SDK Ad activity  -->
        <activity
            android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
        
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
### Ogury integration
Ogury interation is different from others Ad network .

 * Step 1 : Contact mngads support to get presage API key.
 * Step 2 : Add presage-lib.jar to your libs folder
 * Step 3 : Copy the following lines in your AndroidManifest.xml inside <application> tag.Don't forget your API Key: presage_key.

```
#!XML
<!-- PRESAGE LIBRARY -->
<meta-data android:name="presage_key" android:value="presage_key"/>
<service android:name="io.presage.services.PresageServiceImp"/>
<activity android:name="io.presage.activities.PresageActivity" 
  android:label="@string/app_name" 
  android:theme="@style/Presage.Theme.Transparent" 
  android:configChanges="keyboard|keyboardHidden|orientation|screenSize" 
  android:hardwareAccelerated="true" >
    <intent-filter>
      <action android:name="io.presage.intent.action.LAUNCH_WEBVIEW" />
        <category android:name="android.intent.category.DEFAULT" />
    </intent-filter>
</activity>
<receiver android:name="io.presage.receivers.BootReceiver">
    <intent-filter>
        <action android:name="android.intent.action.BOOT_COMPLETED"/>
        <action android:name="android.intent.action.DATE_CHANGED"/>
        <action android:name="io.presage.receivers.BootReceiver.RESTART_SERVICE"/>
    </intent-filter>
</receiver>
```
 * Step 4 : Add the following permissions that will be grouped together
Placed just before the opening <application> tag:

```
#!XML
Default internet and boot permissions
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
Tracking permissions
<uses-permission android:name="com.android.browser.permission.READ_HISTORY_BOOKMARKS" />
<uses-permission android:name="com.android.browser.permission.WRITE_HISTORY_BOOKMARKS" />
Shortcut permissions
<uses-permission android:name="com.android.launcher.permission.INSTALL_SHORTCUT" />
<uses-permission android:name="com.android.launcher.permission.UNINSTALL_SHORTCUT" />

```

* Step 5 : If you have styles.xml inside res/values folder, copy the following lines inside else, create styles.xml inside res/values folder with these lines inside:

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
### Troubleshooting

 * android:noHistory="true" : This may remove your acivity when interstitial Ad is displayed
 * Android multidex issue [AndroidMultidex]

[link]:https://developer.android.com/training/location/retrieve-current.html
[Smart ads server]:http://help.smartadserver.com/fr/Default.htm#../../../../specifications/Content/MobileSpecifications/Apps.htm
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
[Amazon.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[Liverail.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[FlurryAds.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[FlurryAnalytics.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[Best practice Mngads and Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[AndroidMultidex]:http://developer.android.com/intl/ko/tools/building/multidex.html
[Ogury]:http://www.ogury.co/
[presage-lib.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[Native Ads guidelines]:./nativead
[ApplicationManager.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/utils/ApplicationManager.java?at=master&fileviewer=file-view-default
[BaseActivity.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/BaseActivity.java?at=master&fileviewer=file-view-default
[Interstitial Guideline]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial-guideline