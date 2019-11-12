# Android DFP Adapter
[TOC]

This guide shows you how to integrate [MNGAds] mediation adapter of Google Mobile Ads SDK with your current Android app and set up additional request parameters.

## Supported ad formats
- Banners
- Interstitials
- Native Ads

## Requirements
- Android SDK 4.4 (API level 19) or later
- Google Play services 17.2.0 or later

## Google Ad Manager UI 

The custom event must be defined in the [Google Ad Manager UI].

### 1. Create a Yield groups

- Create an Ad Network
![screenshot-admanager.google.com-2019.10.02-22_36_16 (1).jpg](https://bitbucket.org/repo/GyRXRR/images/2101314984-screenshot-admanager.google.com-2019.10.02-22_36_16%20%281%29.jpg)

1. Create a Company with **Madvertise Ad-Network** name
2. Choose **Appsfire** network
3. Allow mediation

### 2. Add a Yield Group

1. Choose a name
2. Choose a format (You must create a Yield Group by format)
3. Choose at least one size according format
4. Target a specific placement

![screenshot-admanager.google.com-2019.10.08-23_09_28.jpg](https://bitbucket.org/repo/GyRXRR/images/3042937156-screenshot-admanager.google.com-2019.10.08-23_09_28.jpg)

### 3. Add A Yield Partner and Define a custom event

On your Google Ad Manager UI, create a custom event 
![screenshot-admanager.google.com-2019.10.08-23_09_54.jpg](https://bitbucket.org/repo/GyRXRR/images/2980010623-screenshot-admanager.google.com-2019.10.08-23_09_54.jpg)

1. Select **Madvertise Ad-Network** created on [Step 1]
2. Choose **Custom Event** for Integration type
3. Choose your platform iOS or Android
4. Set the following **Label**, **class Name**  and **Parameter** according your format :


* Banner : Label= **MadvertiseCustomEventBanner**, class Name= **com.madvertise.MadvertiseCustomEventBanner** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_BANNER
* Banner : Label= **MadvertiseCustomEventInterstitial**, class Name= **com.madvertise.MadvertiseCustomEventInterstitial** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_INTER
* Banner : Label= **MadvertiseCustomEventNativead**, class Name= **com.madvertise.MadvertiseCustomEventNativead** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_NATIVEAD
 


## Integrate MNGAds in your application project

### 1. Set Up

* Add our adapter [mngads-dfp-adapter-1.0.2.aar]
* [set up sdk section] MNGAds on your application project.



### 2. Initialize your ads

You can check our [Demo] page.

#### 2.1 Banner and Interstitial

**No additional code is required for integration.** 

You may now use MNG DFP Adaptor to show [Interstitial Ads] and [Banner Ads] the same way it's described in the [DFP Documentation].The adapter code and the setup you did on your Google Ad Manager UI will allow MNG Ads to deliver ads.

#### 2.2 Native Ads
##### Load an Ad
The following code demonstrates how to build an AdLoader that can load unified native ads:

```java
AdLoader adLoader = new AdLoader.Builder(context, "YOUR PLACEMENT ID")
    .forUnifiedNativeAd(new UnifiedNativeAd.OnUnifiedNativeAdLoadedListener() {
        @Override
        public void onUnifiedNativeAdLoaded(UnifiedNativeAd unifiedNativeAd) {
        	// Assumes you have a placeholder FrameLayout in your View layout (with id fl_adplaceholder) where the ad is to be placed.
            FrameLayout frameLayout = findViewById(R.id.fl_adplaceholder);
            // Assumes that your ad layout is in a file call ad_unified.xml in the res/layout folder
            UnifiedNativeAdView adView = (UnifiedNativeAdView) getLayoutInflater().inflate(R.layout.ad_unified, null);
            // This method sets the text, images and the native ad, etc into the ad view.
            populateUnifiedNativeAdView(unifiedNativeAd, adView);
        }
    })
    .withAdListener(new AdListener() {
        @Override
        public void onAdFailedToLoad(int errorCode) {
		// Handle the failure by logging, altering the UI...
        }
    })

.withNativeAdOptions(new NativeAdOptions.Builder().build())
.build();
adLoader.loadAd(request);
```
##### Display a UnifiedNativeAd
Once you have loaded an ad, all that remains is to display it to your users.

```java
private void displayUnifiedNativeAd(ViewGroup parent, UnifiedNativeAd ad) {

    // Locate the text view  

	TextView nativeAdTitle = adView.findViewById(R.id.nativeAdTitle);
	TextView nativeAdContext = adView.findViewById(R.id.nativeAdContext);
	TextView nativeAdCallToAction = adView.findViewById(R.id.nativeAdCallToAction);
	
	 // Set its text
       
	nativeAdTitle.setText(unifiedNativeAd.getHeadline());
	nativeAdContext.setText(unifiedNativeAd.getBody());
	nativeAdCallToAction.setText(unifiedNativeAd.getCallToAction());

	// Register it
	
	adView.setCallToActionView(nativeAdCallToAction);
	adView.setHeadlineView(nativeAdTitle);
	adView.setBodyView(nativeAdContext);
	
	
	// Set Icon and MediaView view, the asset is populated automatically
	
	adView.setIconView(adView.findViewById(R.id.nativeAdIcon));
	adView.setImageView(adView.findViewById(R.id.mediaContainer));
	adView.setStoreView(mMAdvertiseNativeContainer);


    // Register the NativeAdObject.
    adView.setNativeAd(ad);


    // Ensure that the parent view doesn't already contain an ad view.
    parent.removeAllViews();
    // Place the AdView into the parent.
    parent.addView(adView);
}
```

**Note :**
The only difference between the [Native Ads Documentation] and our code these three lines responsible for loading image, video and icon and handling click :

```java
// For loading icon
adView.setIconView(adView.findViewById(R.id.nativeAdIcon));

// For loading image or video
adView.setImageView(adView.findViewById(R.id.mediaContainer));

// For handling click
adView.setStoreView(mMAdvertiseNativeContainer);
```

### 3. Location

You can specify location-targeting information in the ad request as follows:

```java
PublisherAdRequest request = new PublisherAdRequest.Builder()
        .setLocation(location)
        .build();
```


### 4. Custom targeting

If you need to send your custom key-value pairs. You can specify key-value-targeting information in the ad request as follows: 


```java
PublisherAdRequest request = new PublisherAdRequest.Builder()
		.addKeyword("Keyword")
        .addCustomTargeting("key1", "value1")
        .addCustomTargeting("key2", "value2")
        .build();
```

and you must send your custom key-value pairs also using the addCustomEventExtrasBundle() method.

```java
PublisherAdRequest adRequest = new PublisherAdRequest.Builder()
.addCustomEventExtrasBundle(MadvertiseCustomEventInterstitial.class,getExtrasData())
.build();
```
You must pass custom event adapter class name for :

 * **Banner :** MadvertiseCustomEventBanner.class 
 
 * **Interstitial :** MadvertiseCustomEventInterstitial.class
 *  **Native Ads :** MadvertiseCustomEventNativead.class

and a bundle of the extras :

```java
Bundle extras = new Bundle();
extras.putString("customTargeting","key1=value1;key2=value2");
```

[Google Ad Targeting page]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/targeting 
[Banner Ads]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/banner
[Interstitial Ads]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/interstitial
[Native Ads Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/native/advanced
[set up sdk section]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-set-up-the-sdk
[mngads-dfp-adapter-1.0.3.aar]:hhttps://bitbucket.org/mngcorp/mngads-demo-android/downloads/mngads-dfp-adapter-1.0.3.aar
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mngads-sdk-2.7.aar?at=master
[DFP Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start
[Google Ad Manager UI]:https://admanager.google.com/
[MNGAds]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home
[Step 1]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/dfp-adapter-android#markdown-header-1-create-a-yield-groups
[Demo]:https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/DFPFragment.java