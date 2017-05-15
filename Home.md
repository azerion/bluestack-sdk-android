![mad_AdNetworkMediation_rgb_small.png](https://bitbucket.org/repo/GyRXRR/images/3981639300-mad_AdNetworkMediation_rgb_small.png) for Android

[TOC]


MNG Ads provides functionalities for monetizing your mobile application: from premium sales with rich media, video and innovative formats, it facilitates inserting native mobile ads as well all standard display formats. MngAds SDK is a library that allow you to handle the following Ads servers with the easy way :

- [Smart ads server]
- [Google DFP]
- [Facebook Audience Network]
- [Amazon]
- [Flurry]
- [Retency]
- [Ogury] Note : An API Key will be assigned to your application by mngads support team for Ogury library.


It contains a dispacher that will select an ads server according to the priority and state ([mngAds state diagram]).

## Version
See [Change Log] and [Upgrade Guide].

NOTE :MNG Ads requires minimum Android API level 11

## Ad Examples and inspiration

You can see [Best practice Mngads and Design ad units to fit your app], an optimized use case for several ad formats on one page.

## Set up the SDK

### Using Gradle

If using Gradle,Add this to Module-level /app/build.gradle before dependencies
```groovy
repositories {
	mavenCentral() 
}
```

 include JCenter/Maven repository and add the following lines to your app's build.gradle, and make sure the latest SDK is used:

- Google-play-services_lib (com.google.android.gms:play-services:10.2.0) (**mandatory**)
- AudienceNetwork (com.facebook.android:audience-network-sdk:4.21.1) (**recommended**)
- Support-v4 (com.android.support:support-v4:23.+ or http://developer.android.com/intl/ko/tools/support-library/setup.html#choosing) (**mandatory**)
- Amazon (com.amazon.android:mobile-ads:5.8.1.1) (**recommended**)
- com.flurry.android:analytics:7.0.0 and com.flurry.android:ads:7.0.0 (**recommended**)

**See our [build.gradle] sample**


 **download and extract following files and place them in the /libs folder in your project**
 
 - [mng-ads.jar Android SDK] (**mandatory**)
 - [SmartAdServer-Android-SDK.jar] (**mandatory**)
 - [Retency-sdk] (**recommended**)
 - [Presage-lib.jar] (**recommended**)

 - [nl.qbusict:cupboard:2.1.4] (for beacon)
 - [de.greenrobot:eventbus:2.4.0] (for beacon)
 - [com.squareup.retrofit2:converter-jackson:2.0.0] (for beacon)
 - [b4s-android-sdk] (for beacon)
 - [b4s-android-sdk-playservices830] (for beacon)
 
```groovy
dependencies { 
dependencies {
    compile files('libs/SmartAdServer-Android-SDK-6.6.5.jar')
    compile files('libs/retency-sdk.jar')
    compile files('libs/mng-ads-sdk.jar')
    compile files('libs/presage-lib-2.0.7-obfuscated.jar')
}
```
### Manual installation

If using Intellij IDEA or Eclipse, download and extract [mng-ads.jar Android SDK] from our demo project and

- download [mng-ads.jar Android SDK] from our demo project
- drag and drop it in your libs/ folder

**MngAds SDK requires following librairies (you must use version in used on demo project): **



- [SmartAdServer-Android-SDK.jar] (**recommended**)
- [AudienceNetwork.jar] (**recommended**)
- [Android-support-v4.jar] (**mandatory**)
- [Google-play-services_lib]: (com.google.android.gms:play-services:10.2.0) (**mandatory**)
- [Amazon.jar] (**recommended**)
- [flurryAds.jar] and [flurryAnalytics.jar] (**recommended**)
- [Retency-sdk] (**recommended**)
- [Presage-lib.jar] (**recommended**)


- [nl.qbusict:cupboard:2.1.4] (for beacon)
- [de.greenrobot:eventbus:2.4.0] (for beacon)
- [com.squareup.retrofit2:converter-jackson:2.0.0] (for beacon)
- [b4s-android-sdk] (for beacon)
- [b4s-android-sdk-playservices830] (for beacon)



### If your app uses Proguard

[see Proguard rules on our faq]

## Sample Application

Included is a [MngAds sample app] to use as example and for help on MngAds integration. This basic application allows users to test our differents formats.

## Start Integrating

### Initializing the SDK

You have to init the SDK in your application class


```java
...
import com.mngads.MNGAdsFactory;
...
public class DemoApp extends Application{

    @Override
	public void onCreate() {
		super.onCreate();
		MNGAdsFactory.initialize(this,"YOUR_APP_ID");
	}
}
```
### MAdvertiseBeacon

Get Ebeacon technology to propose to the advertisers to target the users inside the point of sale. 
- An installation base of 12,500 ebeacons ready to track the users.
- An exclusive format in Push notification to the users inside a tabacco shop, press shop, pharmay or mall.

### Initializing Beacons

You have to init becon in your application class
MAdvertiseBeaconAdapter.initBeacons(this) should be called before         MNGAdsFactory.initialize(this,"YOUR_APP_ID");


```java
public class DemoApp extends Application{

@Override
    public void onCreate() {
        super.onCreate();
        MAdvertiseBeaconAdapter.initBeacons(this);
        MNGAdsFactory.initialize(this,"YOUR_APP_ID");
}
}
```
you have to update your manifest.xml
```xml

<manifest xmlns:android="http://schemas.android.com/apk/res/android"

 <uses-sdk tools:overrideLibrary="com.ezeeworld.b4s.android.sdk.playservices"/>
    <uses-feature
        android:name="android.hardware.bluetooth_le"
        android:required="true" />
    <uses-permission android:name="android.permission.BLUETOOTH" />
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />

```
and you have to edit your build.gradle file
```java
 buildTypes {

  packagingOptions {
            exclude 'META-INF/ASL2.0'
            exclude 'META-INF/LICENSE'
            exclude 'META-INF/NOTICE'
        }

 }
 
 
 
 dependencies {

  compile 'nl.qbusict:cupboard:2.1.4'
  compile 'de.greenrobot:eventbus:2.4.0'
  compile 'com.squareup.retrofit2:converter-jackson:2.0.0'
  compile (name:'b4s-android-sdk', ext:'aar')
  compile (name:'b4s-android-sdk-playservices830', ext:'aar')

}
```
and you need to declare your flat file repository.
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
### Initialize Check

To verify if the SDK is fully initialized you have to call isInitialized():

```java
...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGAdsSDKFactoryListener;
...
public class MainActivity extends Activity implements MNGAdsSDKFactoryListener{
...	
	if(MNGAdsFactory.isInitialized()){
	    //The SDK is initialized
            Toast.makeText(this, "MNGAdsFactory is initialized", Toast.LENGTH_SHORT).show();

    }else {
	   
	    //The SDK is initializing
	    //set up a callback	that will be called when is fully initialized
            MNGAdsFactory.setMNGAdsSDKFactoryListener(this);

            Toast.makeText(this, "MNGAdsFactory is not initialized", Toast.LENGTH_SHORT).show();

    }
  ...
  
  ...
   @Override
    public void onMNGAdsSDKFactoryDidFinishInitializing() {

       
           Toast.makeText(MainActivity.this, "MNGAds SDK Factory Did Finish Initializing", Toast.LENGTH_SHORT).show();
        	
           Log.d(TAG, "MNGAds SDK Factory Did Finish Initializing");
    }

...

```

`Note`: onMNGAdsSDKFactoryDidFinishInitializing(): this method is called at any time when the initialize(...) method of MNG gets called

### Timeout
The time given to the ad view to download the ad data. After this time, the dispacher stops the ad server running (with failure) and move to the next.

the default timeout is 1s.

```java
...
import com.mngads.MNGAdsFactory;
...

public class MainActivity extends Activity{

    private MNGAdsFactory mngAdsBannerAdsFactory;
...	
// init banner factory
    mngAdsBannerAdsFactory = new MNGAdsFactory(this);
    mngBannerAdsFactory.setTimeOut(3);
...
```

### isBusy
Before making a request if you want to check that factory not busy (handling old request).

Ads factory is busy means that it has not finished the previous request yet.

isBusy will be setted to true when factory start handling request.

isBusy will be setted to false when factory finish handling request.
**example**:
```java
	if (!mngAdsBannerAdsFactory.isBusy()) {
	
		Log.d(TAG, "Ads Factory is not busy");
		
		mngAdsBannerAdsFactory.loadBanner(new MNGFrame(320, 50));
	} else {
		Log.d(TAG, "Ads Factory is busy");
	}
```

### Banner
#### Init factory

To create a banner you have to init an object with type MNGAdsSDKFactory and set the bannerListener and the context.

```java
...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGBannerListener;
import com.mngads.util.MNGFrame;
...

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

```java
    mngAdsBannerAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#### Make a request
To make a request you have to call 'loadBanner'. It is a void methode, This is a void method, result will be returned in the callback.

```java
    private MNGFrame mFrame;
    mFrame = getResources().getBoolean(R.bool.is_tablet) ? MNGAdSize.MNG_DYNAMIC_LEADERBOARD : MNGAdSize.MNG_DYNAMIC_BANNER;
mngAdsBannerAdsFactory.loadBanner(mFrame)
	
```

####Handle callBack from BannerListener
**v1.5.1 or above**
bannerDidLoad(View adView) changed to bannerDidLoad(View adView,int preferredHeightDP).
bannerDidLoad(View adView,int preferredHeightDP): will be called by the SDK when your bannerView is ready. now you can add your bannerView to your view.
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

bannerDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```java
	@Override
	public void bannerDidFail(Exception adsException) {
		Log.e(TAG, "banner did fail :" + adsException.toString());
	}
```
**v1.5.1 or above** 
bannerResize(MNGFrame frame) : will be called when the banner has changed size
```java
	 @Override
    public void bannerResize(MNGFrame frame) {
    ...
        // it's preferable to adjust the ad container view size to match the returned Ad size for a better display
        Log.d(TAG, "Banner did resize w dp " + frame.getWidth() + " h dp " + frame.getHeight());
    ...
    }
```
### MNGAdSize
Mng ads provides variant pre-defined sizes ( example below).
```java

public final static MNGFrame MNG_BANNER = new MNGFrame(320, 50);
	public final static MNGFrame MNG_DYNAMIC_BANNER = new MNGFrame(MNGConstants.UNDEFINED_WIDTH, 50);
	public final static MNGFrame MNG_LARGE_BANNER = new MNGFrame(320, 100);
	public final static MNGFrame MNG_FULL_BANNER = new MNGFrame(468, 60);
	public final static MNGFrame MNG_LEADERBOARD = new MNGFrame(728, 90);
	public final static MNGFrame MNG_DYNAMIC_LEADERBOARD = new MNGFrame(MNGConstants.UNDEFINED_WIDTH, 90);
	public final static MNGFrame MNG_MEDIUM_RECTANGLE = new MNGFrame(300, 250);
```
Example:

```java

    MNGFrame mFrame;

    if (isSquare) 
	{
         mFrame=MNGAdSize.MNG_MEDIUM_RECTANGLE;
	}
	else
	{
                mFrame = getResources().getBoolean(R.bool.is_tablet) ?  MNGAdSize.MNG_DYNAMIC_LEADERBOARD: MNGAdSize.MNG_DYNAMIC_BANNER;
	}
	mngAdsBannerAdsFactory.loadBanner(mFrame);
```



### Infeed
#### Init factory

To create an **In-Feed** Ad format ( the ads that show up in the middle of the stream as you scroll through your content Parallax or Video) you must init an object with type MNGAdsSDKFactory and set the infeedListener, context.

```java
...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGInfeedListener;
import com.mngads.util.MNGFrame;
...

public class MainActivity extends Activity implements MNGInfeedListener{
...
    private MNGAdsFactory mngAdsInfeedAdsFactory;
@Override
    protected void onCreate(Bundle savedInstanceState) {
...
// init infeed factory
    mngAdsInfeedAdsFactory = new MNGAdsFactory(this);
// set infeed listener
    mngAdsInfeedAdsFactory.setInfeedListener(this);

```
You have also to set placementId (minimum one time)

```java
    mngAdsInfeedAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#### Make a request
To make a request you have to call 'loadInfeed'. This is a void method, result will be returned in the callback. 

```java
mngAdsInfeedAdsFactory.loadInfeed(new MNGFrame(300, 250))
    
```

####Handle callBack from InfeedListener

infeedDidLoad(View infeedView): will be called by the SDK when your infeedView is ready. now you can add your infeedView to your view.
```java
	@Override
    public void infeedDidLoad(View infeedView) {
		Log.d(TAG, "your infeed view is ready")
		...
		adLayout.addView(infeedView);
	}
```

infeedDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```java
	@Override
	public void infeedDidFail(Exception adsException) {
		Log.e(TAG, "infeed did fail :" + adsException.toString());
	}
```

### Interstitial
#####Init factory

To create a interstitial you must init an object with type MNGAdsSDKFactory and set the interstitalListener and the context (Activity)  [more details about instance on our FAQ].

```java

...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGInterstitialListener;
...

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
You have also to set placementId (minimum one time)

```java
    mngAdsInterstitialAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

#####Make a request 
To make a request you must call 'loadInterstitial()'. This is a void method, result will be returned in the callback.

```java
    mngAdsInterstitialAdsFactory.loadInterstitial()
```
#####Handle callBack from InterstitialListener
InterstitialDidLoad(): will be called by the SDK when your Interstitial is ready.
```java
@Override
	public void interstitialDidLoad() {
		Log.d(TAG, "interstitial did load");
	}
```

interstitialDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```java
@Override
	public void interstitialDidFail(Exception adsException) {
		Log.e(TAG, "interstitial did fail :" + adsException.toString());
	}
```
InterstitialDisappear(): will be called when intertisialView did disappear. now you can update your UI for example.

```java
@Override
	public void interstitialDisappear() {
		Log.d(TAG, "interstitial disappear")
	}
```

#####Disable auto-displaying
With v2.0.8 and above, you can disable auto-displaying.
```java
...
    mngAdsInterstitialAdsFactory.loadInterstitial(false);
...

```
To check if the interstitial is ready to be show, you must call isInterstitialReady() and displayInterstitial() in order to display the ads (in case of success).
```java
...
    if (mngAdsInterstitialAdsFactory.isInterstitialReady()) {
    
        mngAdsInterstitialAdsFactory.displayInterstitial();
    } else {
        Log.d(TAG, "Interstitial not ready ");
    }
...
```
######info 
To try out auto-displaying disabled on demo, you can check interstitial page. Others interstitials (background returns, overlay) run with auto-displaying.

Ogury ad network returns interstitial only with autoDisplay true.

###Show Interstitial after return from background

You can see [Interstitial Guideline] and our demo app with following files

 - [ApplicationManager.java]
 - [BaseActivity.java]

### Native Ads
Native ads give you the control to design the perfect ad units for your app. With our Native Ad API, you can determine the look and feel, size and location of your ads. Because you decide how the ads are formatted, ads can fit seamlessly in your application.
#####Init factory

To create a nativeAd  you have to init an object with type MNGAdsSDKFactory and set the nativeListener.

```java
...
import com.mngads.MNGAdsFactory;
import com.mngads.MNGNativeObject;
import com.mngads.listener.MNGNativeListener;
...
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
```java
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
#####Make a request for native ad
To make a request you have to call 'loadNative()'. This is a void method, result will be returned in the callback.

```java
    mngAdsNativeAdsFactory.loadNative()
```
#####Handle callBack from NativeListener
nativeObjectDidLoad()  will be called by the SDK when your nativeObject is ready. now you can create your own view.
```java
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
		Log.d(TAG, "native Object did load ");
	}

```

nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```java
@Override
	public void nativeObjectDidFail(Exception adsException) {
		Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
	}

```
#####Build Native Ad UI
MNGNativeObject have all required metadata to build your customized native UI.
```java
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

#####Customize Native Ad Badge 
You can use a custom badge for the native ad.

```java
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
   ...
        Bitmap badge=nativeObject.getBadge(getActivity(),"String to be displayed in the badge");
   ...
}
```


##### v2.0 or above
You can also integrate video ads into your Native Ad experience. To enable video you must complete the following steps:

- Have SDK version 2.0 or later
- You have to call setMediaContainer(viewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result
 
```java
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
```java
...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGClickListener;
...
public class MainActivity extends Activity implements MNGClickListener{
...
   private MNGAdsFactory mngAdsAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
    // init MNG factory
        mngAdsAdsFactory = new MNGAdsFactory(this);

    // set click listener
        mngAdsAdsFactory.setClickListener(this);
}

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
...
import com.mngads.MNGAdsFactory;
import com.mngads.listener.MNGRefreshListener;
...
public class MainActivity extends Activity implements MNGClickListener{
...
   private MNGAdsFactory mngAdsAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
    // init MNG factory
        mngAdsAdsFactory = new MNGAdsFactory(this);

    // set refresh listener
        mngAdsAdsFactory.setRefreshListener(this);
}

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

- age : age of user
- location : geographical position of the user.
- language : language of user (ISO code)
- gender : gender of user
- keyWord : Use free-form key-values when you want to pass targeting values dynamically into an ad tag based on information you collect from your users. You can also use free-form key-values when there are too many possible values to define in advance. Separator in case of multiple entries is **;**. 
- content url : URL for content related to your app (url must be a string which length not exceed 512 caracters). 

```java
import com.mngads.util.MNGPreference;
import com.mngads.util.MNGGender;
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
		mngPreference.setContentUrl("put your content url here")

```
`Note`: this [link] can help you to get device location.
### Exceptions
|Exception|Error code|Message|Meaning|
| --- | --- | --- | --- |
|MAdvertiseWrongPlacementIdException|WRONG_PLACEMENT_ERROR = 0   |    Wrong placement | You have set a wrong placement |
|MAdvertiseInternetException|NO_INTERNET_ERROR = 1   |    No Internet | There is no internet connection at the moment      |
|MAdvertiseSDKUninitializedException|SDK_UNINITIALIZED_ERROR = 2   |    MNGAds is not initialized | The sdk is not initialized, you have to call  MNGAdsFactory.initialize(context,"your app id");      |
|MAdvertiseRequestCappedException|CAPPED_REQUEST_ERROR = 3  |    Your request has been capped | Your request is capped, If you are in doubt, check your capping value related to the placement|
|MAdvertiseLockedPlacementException|LOCKED_PLACEMENT_ERROR = 4   |   This placement is locked by an other factory | An other factory has loaded an interstitial using this placement, and its no yet displayed     |
|MAdvertiseBusyFactoryException|BUSY_FACTORY_ERROR = 5   |    Your factory is busy| Your factory is busy by an other request at the moment     |
|MAdvertiseNoAdException|NO_AD_ERROR = 7   |    No Ad found | Therese no ad to dilver at the moment     |
|MAdvertiseInterstitialCoolDownException|INTERSTITIAL_COOLDOWN_ERROR = 8   |   Time between last interstitalDisappear and loadInterstital Must be more than 5s |We have defined a minimum time between interstitalDisappear and loadInterstital, this interval is set to 5 second       |
|MAdvertiseAlreadyShownInterstitialException|INTERSTITIAL_ALREADY_SHOWN_ERROR = 9   |   Other Interstitial is shown | We tolerate only one interstitial to be shown at time   |
|MAdvertiseTimeOutException|TIME_OUT_ERROR = 10   |  no ad to deliver before time out | Therese no ad to deliver before the specified time out  |

#### Handle Exception
If you want to check which exception was invoked, in the didFail callback you have to cast the exception to MAdvertiseException and then use getErrorCode() to get exception code.
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
### Memory managment
When you have finished your ads plant you must free the memory.

```java
@Override
	protected void onDestroy() {
		mngAdsBannerAdsFactory.releaseMemory();
		mngAdsInfeedAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactory.releaseMemory();
		mngAdsNativeAdsFactory.releaseMemory();
		mngAdsInterstitialAdsFactoryOverlay.releaseMemory();
		super.onDestroy();
	}
```

### Enabling debug mode
To enbale debug mode you need to set debug mode to true :

```java
...
    MNGAdsFactory.setDebugModeEnabled(true);
...
```

### Configure your Manifest

To make ad request we need to add the following permission to AndroidManifest.xml file :

```xml

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
    <!--Grants the SDK permission to create windows using the type TYPE_SYSTEM_ALERT, shown on top of all other apps.-->
    <!--this permission is required for Debug Mode with Gyroscope Sensor.-->
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
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
   <service
            android:name="io.presage.PresageService"
            android:enabled="true"
            android:exported="true"
            android:process=":remote">
            <intent-filter>
                <action android:name="io.presage.PresageService.PIVOT" />
            </intent-filter>
        </service>
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
### Styles
If you have styles.xml inside res/values folder, copy the following lines inside else, create styles.xml inside res/values folder with these lines inside:
```xml
<style name="Presage.Theme.Transparent" parent="android:Theme">
    <item name="android:windowIsTranslucent">true</item>
    <item name="android:windowBackground">@android:color/transparent</item>
    <item name="android:windowContentOverlay">@null</item>
    <item name="android:windowNoTitle">true</item>
    <item name="android:backgroundDimEnabled">false</item>
</style>
```
### Ogury integration
Ogury integration is different from others Ad network .

Ogury ad network returns interstitial only with autoDisplay true.


 * Step 1 : Contact mngads support to get presage API key.
 
 * Step 2 : Add presage-lib.jar to your libs folder
 *
 * Step 3 : Copy the following lines in your AndroidManifest.xml inside <application> tag.Don't forget your API Key: presage_key.

```xml
<!-- PRESAGE LIBRARY -->
<meta-data android:name="presage_key" android:value="presage_key"/>

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
 <service
    android:name="io.presage.PresageService"
    android:enabled="true"
    android:exported="true"
    android:process=":remote">
        <intent-filter>
            <action android:name="io.presage.PresageService.PIVOT" />
        </intent-filter>
 </service>
        
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
 * Step 4 : Add the following permissions that will be grouped together
Placed just before the opening <application> tag:

```xml
Default internet permissions
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

* Step 5 : If you have styles.xml inside res/values folder, copy the following lines inside else, create styles.xml inside res/values folder with these lines inside:

```xml
<style name="Presage.Theme.Transparent" parent="android:Theme">
    <item name="android:windowIsTranslucent">true</item>
    <item name="android:windowBackground">@android:color/transparent</item>
    <item name="android:windowContentOverlay">@null</item>
    <item name="android:windowNoTitle">true</item>
    <item name="android:backgroundDimEnabled">false</item>
</style>
```
* Step 6 : If you use okhhtp in your project or in an other dependency, try to add these lines in your build.gradle to avoid build error :
```java
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
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsRequiredJars/AudienceNetwork.jar?at=master&fileviewer=file-view-default
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[SmartAdServer-Android-SDK.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/
[mngAds state diagram]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/diagram
[Retency]:http://www.retency.com/public/
[Retency-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/retency-sdk.jar?at=master
[Amazon]:https://developer.amazon.com/public/resources/development-tools/sdk
[Amazon.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Flurry]:https://developer.yahoo.com/flurry/
[FlurryAds.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[FlurryAnalytics.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Best practice Mngads and Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[AndroidMultidex]:http://developer.android.com/intl/ko/tools/building/multidex.html
[Ogury]:http://www.ogury.co/
[presage-lib.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/presage-lib-1.8.1.jar?at=master&fileviewer=file-view-default
[Native Ads guidelines]:./nativead
[ApplicationManager.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/utils/ApplicationManager.java?at=master&fileviewer=file-view-default
[BaseActivity.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/BaseActivity.java?at=master&fileviewer=file-view-default
[Interstitial Guideline]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial-guideline
[see Proguard rules on our faq]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-if-your-app-uses-proguard-you-must-edit-your-proguard-settings-to-avoid-stripping-google-play-out-of-your-app
[more details about instance on our FAQ]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-interstitial-did-load-callback-without-display
[nl.qbusict:cupboard:2.1.4]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[de.greenrobot:eventbus:2.4.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[com.squareup.retrofit2:converter-jackson:2.0.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk-playservices830]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[build.gradle]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/build.gradle?at=master&fileviewer=file-view-default