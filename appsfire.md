![MNG-Ads-1.png](https://bitbucket.org/repo/aen579/images/3739691856-MNG-Ads-1.png) Android for
![4193248577-af.png](https://bitbucket.org/repo/aen579/images/2031262448-4193248577-af.png) only


[TOC]

# Introduction

MNG Ads can be used for appsfire nativeAds only.

 - http://appsfire.com/

The Monetization features of Appsfire SDK allows you to display ads in your application:
 
 - Interstitial ads, A full-screen native ad unit for iPhone & iPad, we call it the [Sushi].
 - An in-stream native ad unit which allows you to deeply integrate our ads in your application's design, we call it [Sashimi]. 

## Start Integrating appsfire

### Install

Add the [mng-ads.jar Android SDK] to the libs folder of your app as well

### Banner

```java
...
import com.mngads.sdk.nativead.MNGHimonoAd;
import com.mngads.sdk.listener.MNGHimonoAdListener;
import com.mngads.sdk.util.MNGAdSize;
...

public class MyActivity extends Activity implements MNGHimonoAdListener {
...

// init banner view
MNGHimonoAd mHimonoAd;

mHimonoAd = new MNGHimonoAd (this, MNGAdSize.getMNGAdsHeight50Banner());
mHimonoAd.setHimonoListener(this);
```

##### Ad size MNGAdSize

```java
MNGAdSize.getMNGAdsHeight50Banner()              // screen width x 50 banner
MNGAdSize.getMNGAdsHeight50Banner(int width_dp)  // width_dp x 50 banner
MNGAdSize.getMNGAdsHeight90Banner();             // screen width x 90 banner
MNGAdSize.getMNGAdsHeight90Banner(int width_dp)  // width_dp x 90 banner
MNGAdSize.getMNGAdsSizeHeight250Rectangle();     // 300 x 250 square banner
```

##### Make a request
To make a request you must call loadAd

```java
mHimonoAd.loadAd("YOUR_PUBLISHER_ID");
```

##### Handle callBack from MNGHimonoAdListener
```java
@Override
public void himonoBannerViewDidLoadAd (MNGHimonoAd ad) {
   Log.d(TAG, "himono: himonoBannerViewDidLoadAd");

   // Insert banner in your app's 'myAdContainerLayout' for instance
   FrameLayout.LayoutParams params;
   params = new FrameLayout.LayoutParams(FrameLayout.LayoutParams.MATCH_PARENT, FrameLayout.LayoutParams.WRAP_CONTENT, Gravity.CENTER_HORIZONTAL | Gravity.BOTTOM);
   myAdContainerLayout.addView(ad, 0, params);
}

@Override
public void himonoBannerViewDidFailToLoadAd (MNGHimonoAd ad, Exception ex) {
   Log.d(TAG, "himono: himonoBannerViewDidFailToLoadAd");
}

@Override
public void himonoBannerViewDidRecordClick (MNGHimonoAd ad) {
   Log.d(TAG, "himono: himonoBannerViewDidRecordClick");
}
```

### Interstitial

```java
...
import com.mngads.sdk.nativead.MNGDisplayableNativeAd;
import com.mngads.sdk.listener.MNGNativeAdListener;
import com.mngads.sdk.nativead.MNGSushiAd;
import com.mngads.sdk.listener.MNGSushiAdListener;
...

// init interstitial

MNGDisplayableNativeAd mInterstitial;

mInterstitial = new MNGDisplayableNativeAd (this, "YOUR_PUBLISHER_ID");
mInterstitial.setNativeAdListener(createNativeInterstitialListener());    
```

##### Make a request 
To make a request you have to call loadAd 

```java
mInterstitial.loadAd();
```

##### Handle callBack from MNGNativeAdListener
```java
private MNGNativeAdListener createNativeInterstitialListener() {
   return new MNGNativeAdListener() {
      @Override
      public void onAdLoaded(MNGNativeAd mngNativeAd) {
         Log.d(TAG, "interstitial: onAdLoaded");
      }

      @Override
      public void onError(MNGNativeAd mngNativeAd, Exception e) {
         Log.d(TAG, "interstitial: onError " + e.toString(), e);
      }

      @Override
      public void onAdClicked(MNGNativeAd ad) {
         // For native ads only, not relevant to interstitials
      }
   };
}
```

##### Displaying interstitial
```java
MNGSushiAd mSushiAd;

if (mInterstitial.isAdLoaded()) {
   mSushiAd = mInterstitial.getSushiAd();
   sushiAd.setSushiAdListener(new createSushiAdListener());
   sushiAd.showAd();
}
```

##### Handle callBack from MNGSushiAdListener
```java

private MNGSushiAdListener createSushiAdListener() {
   return new MNGSushiAdListener() {
      @Override
      public void onInterstitialDisplayed(MNGSushiAd mngSushiAd) {
         Log.d(TAG, "interstitial displayed ");
      }

      @Override
      public void onInterstitialDismissed(MNGSushiAd mngSushiAd) {
         Log.d(TAG, "interstitial dismissed ");

         if (mSushiAd != null) {
            mSushiAd.destroy();
            mSushiAd = null;
         }
      }

      @Override
      public void onAdClicked(MNGSushiAd mngSushiAd) {
         Log.d(TAG, "interstitial ad clicked ");
      }
   };
}
```

### Getting native ads metadata

```java
...
import com.mngads.sdk.nativead.MNGNativeAd;
...
MNGNativeAd mNativeAd;

mNativeAd = new MNGNativeAd (this, "YOUR_PUBLISHER_ID");
mNativeAd.setNativeAdListener(createNativeAdListener());    
```
##### Make a request 
To make a request you have to call loadAd 

```
mNativeAd.loadAd();
```

##### Handle callBack from MNGNativeAdDelegate
```java
private MNGNativeAdListener createNativeAdListener() {
   return new MNGNativeAdListener() {
      @Override
      public void onAdLoaded(MNGNativeAd mngNativeAd) {
         Log.d(TAG, "nativeAd: onAdLoaded");

         // You can now pull information from the nativeAd
         Log.d(TAG, "nativeAd: app name: " + nativeAd.getTitle());
         // etc

         // Once you create a view, "myNativeAdView", to display your native ad, you can register it for impressions and click management
         nativeAd.registerViewForInteraction(myNativeAdView);
      }

      @Override
      public void onError(MNGNativeAd mngNativeAd, Exception e) {
         Log.d(TAG, "nativeAd: onError " + e.toString(), e);
      }

      @Override
      public void onAdClicked(MNGNativeAd ad) {
          // Called if you linked your view with registerViewForInteraction and the ad is clicked
      }
   };
}

```
See [Native Ads guidelines]




## Mopub

It is also possible to use the Mopub SDK and Mopub mediation to serve Appsfire ads using the mngads-server SDK.

Preliminary steps:

- Add the [mngads-server Mopub adapter] (mngads-adserver-mopub-adapter.jar) to the libs folder of your application project, 
- Add the [mng-ads.jar Android SDK] to the libs folder of your app as well
- If building with Android studio, add the libs to gradle, for instance:

    compile files('libs/mngads-adserver-sdk.jar')
    compile files('libs/mngads-adserver-mopub-adapter.jar')

    to the dependencies{} section of your app's build.gradle

- On your mopub dashboard, create a custom network for instance called MNGAppsfireSushi and set the following class name for interstitials:
com.mopub.mobileads.MNGSushiInterstitial

And for native ads:
com.mopub.nativeads.MNGNative

- On your mopub dashboard, create new banner inventory for a custom network and add the following class name for banners:
com.mopub.mobileads.MNGHimonoBanner

You do not need to set any other custom data on the dashboard.

- Initialize the publisher ID's for the MNG Appsfire placements

```java
import com.mopub.mobileads.MNGSushiInterstitial;
import com.mopub.mobileads.MNGHimonoBanner;
import com.mopub.nativeads.MNGNative;
...

// If you use interstitials
MNGSushiInterstitial.setPublisherId("MY_INTER_PUBLISHER_ID");

// If you use banners
MNGHimonoBanner.setPublisherId("MY_BANNER_PUBLISHER_ID");

// If you use native ads
MNGNative.setPublisherId("MY_NATIVEAD_PUBLISHER_ID");
```
- Use Mopub as usual

You may now use MoPubInterstitial, MoPubView and MoPubAdAdapter to show interstitials, banners and native ads as usual. The adapter code and the setup you did on your Mopub dashboard will
allow MNG Appsfire ads to be mediated and served.


## Admob Mediation (certified)

You may also use the Admob SDK and [Admob mediation] to serve Appsfire ads using the mngads-server SDK.

Preliminary steps:

 - Add the mngads-server Admob adapter to your application project :
      - [src/com/appsfire/mediation/AdmobAdapter.java]
      - [src/com/appsfire/mediation/AppsfireNetworkExtras.java]
      - [src/com/appsfire/mediation/AppsfireServerParameters.java]
 
 - Add [mng-ads.jar Android SDK] to the libs folder of your app as well
 - If building with Android studio, add the lib to gradle, for instance:

   
```
#!java

 compile files('libs/mngads-adserver-sdk.jar')
```


    to the `dependencies{}` section of your app's build.gradle

 - Create your Android app in the Monetize tab of the Admob dashboard if that wasn't done already, and create an interstitial ad unit for your app.

 - On your Admob dashboard, for the interstitial ad unit, add a new ad source, select Appsfire from the list of networks. Enter 1 for the SDK token and secret key; they aren't used by MNGAds
anymore but still need to be set up. 

 - Initialize the publisher ID's for the MNG Appsfire placements

```java

import com.appsfire.mediation.AdmobAdapter;
...

AdmobAdapter.setPublisherId("MY_INTER_PUBLISHER_ID");
```
 - Use Admob as usual

You may now use InterstitialAd to show interstitials as usual. The adapter code and the setup you did on your Admob dashboard will allow MNG Appsfire ads to be mediated and served.

Interstitial example for Admob (not specific to MNG/Appsfire):

```java
// Admob interstitial
private InterstitialAd mInterstitial;

// Load interstitial
// If the mediation is configured as such, this will load an MNG Appsfire ad

mInterstitial = new InterstitialAd(this);
mInterstitial.setAdUnitId(ADMOB_ADUNIT_ID);
mInterstitial.setAdListener(this);
AdRequest adRequest = new AdRequest.Builder().build();
mInterstitial.loadAd(adRequest);

...

// Show
if (mInterstitial.isLoaded()) 
mInterstitial.show();
...
```

[mng-ads.jar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mng-ads-sdk.jar?at=master
[mngads-server Mopub adapter]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/mopub-adapter/?at=master
[Sushi]:http://docs.appsfire.com/sdk/ios/integration-reference/img/doc/sushi.mp4
[Sashimi]:http://docs.appsfire.com/sdk/ios/integration-reference/img/doc/sashimi-extended-light.jpg
[Native Ads guidelines]:./nativead
[src/com/appsfire/mediation/AdmobAdapter.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/admob-adapter/sources/src/com/appsfire/mediation/AdmobAdapter.java?at=master
[src/com/appsfire/mediation/AppsfireNetworkExtras.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/admob-adapter/sources/src/com/appsfire/mediation/AppsfireNetworkExtras.java?at=master
[src/com/appsfire/mediation/AppsfireServerParameters.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/admob-adapter/sources/src/com/appsfire/mediation/AppsfireServerParameters.java?at=master
[Admob mediation]:https://developers.google.com/admob/android/mediation-networks