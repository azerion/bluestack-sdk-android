# upgrading SDK

**You need to keep all Ad Network jars up to date.**
## Upgrading to 2.0

MNG Ads requires minimum Android API level 10

### Librairies
#### Removed
The following librairies are not required any more for the sdk
* afAdSdk.jar
* mngperf-android-sdk.jar
* AppNexus-sdk
#### Added
The following librairies are required for the sdk
* amazon-ads.jar
* FlurryAds.jar and FlurryAnalytics.jar
* liverail-admanager.jar

Don't forget to update the other librairies google-play-services_lib , AudienceNetwork.jar , SmartAdServer-Android-SDK.jar And Retency.

### AndroidManifest.xml
#### Removed

```
#!xml

<application
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
    ...
```
#### Added

```
#!xml
<manifest
...
 <!-- External storage is used for pre-caching features if available -->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
...

 <application
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
          
        <!--Amazon SDK Ad activity  -->
        <activity
            android:name="com.amazon.device.ads.AdActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"/>

        <!--Flurry SDK Ad activity  -->
        <activity
            android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>
    ...
```

 ### Implementation
You can also integrate video ads into your Native Ad experience by calling setMediaContainer(mediaViewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result
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
## Upgrading to 1.5.1
The following method have been changed. int preferredHeightDP is now available to more easily resize banners.

```
#!java
 /**
     * Notifies the Listener that the creative from the banner ad had been
     * loaded.
     * @param adView 
     * @param Ad preferredHeightDP this value is in dp
     */
    public void bannerDidLoad(View adView ,int preferredHeightDP);
```
instead of
```
#!java
   /**
     * Notifies the Listener that the creative from the banner ad had been
     * loaded.
     * @param adView 
     */
    public void bannerDidLoad(View adView);
```
The following methode was added to the banner listener
```
#!java
   /**
     * Notifies the listener that the creative from the banner ad had been
     * resized.
     * @param frame Ad frame size width  dp , height dp
     */
    public void bannerResize(MNGFrame frame);
```
##### Note : it's preferable to adjust the ad container view size to match the returned Ad size for a better display.

## Upgrading to 1.3.1

 - You must add [retency-sdk]
 - Update AndroidManifest.xml

```
#!XML
    ...
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    ...
    <!--Grants the SDK permission to start mng analytics service -->
    <service android:name="com.mngads.service.MNGAnalyticsService"/>
    ...
    <!--Retency SDK Ad activitys  -->
    <activity android:name="com.retency.sdk.android.banner.InAppWebView"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|u Mode|screenSize|smallestScreenSize" />
    <activity android:name="com.retency.sdk.android.video.RichMediaActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
            android:hardwareAccelerated="false" />
    <activity android:name="com.retency.sdk.android.mraid.MraidBrowser"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" />
    ...
```

## Upgrading to 1.2.5

You must add **AppNexus-sdk** 

## Upgrading from 1.1 to 1.2

New method for carousel can be used, see [Ad Examples]

To make a request you have to call 'createNativeCollection(int requestedAdNumber)'. this method return a bool value (canHandleRequest) 

```
#!java
if(mngAdsNativeAdsFactory.createNativeCollection(int requestedAdNumber){
//Wait callBack from native listener
}else{
//adsFactory can not handle your request
}
```

## Upgrading from 1.0 to 1.1

No special steps are required to upgrade to v1.1.



[Ad Examples]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/inspiration
[Retency-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/libs/retency-sdk.jar?at=master