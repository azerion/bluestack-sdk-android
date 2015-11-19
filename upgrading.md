# upgrading SDK

**You need to keep all Ad Network jars up to date.**
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