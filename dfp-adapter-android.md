# Android DFP Adapter
[TOC]

This guide shows you how to integrate [MNGAds] mediation adapter of Google Mobile Ads SDK with your current Android app and set up additional request parameters.

## Supported ad formats
- Banners
- Interstitials
- Native Ads
- Rewarded Ads

## Requirements
- Android SDK 4.4 (API level 19) or later
- Google Play services 20.6.0 or later

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
![2022-04-20_15-10.png](https://bitbucket.org/repo/GyRXRR/images/3594004058-2022-04-20_15-10.png)

1. Select **Madvertise Ad-Network** created on [Step 1]
2. Choose **Custom Event** for Integration type
3. Choose your platform iOS or Android
4. Set the following **Label**, **class Name**  and **Parameter** according your format :


* Banner : Label= **GADBlueStackMediationAdapter**, class Name= **com.madvertise.GADBlueStackMediationAdapter** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_BANNER
* Interstitial : Label= **GADBlueStackMediationAdapter**, class Name= **com.madvertise.GADBlueStackMediationAdapter** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_INTER
* Native Ad : Label= **GADBlueStackMediationAdapter**, class Name= **com.madvertise.GADBlueStackMediationAdapter** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_NATIVEAD
* Rewarded Ad : Label= **GADBlueStackMediationAdapter**, class Name= **com.madvertise.GADBlueStackMediationAdapter** and Parameter= /YOUR_APP_ID/PLACEMENT_ID_REWARDEDAD
 


## Integrate MNGAds in your application project

### 1. Set Up 
#### a. Our Adapter

In the main build.gradle of your project, you must declare the Bluestack repository: 

```groovy
allprojects {
    repositories {
        google()
        jcenter()
     
    // For All Bluestack SDKs (Mediation, CMP, Location, Adapter)
    maven 
    {
     credentials 
        {
         username "madvertise-maven"
         password "GpdGZ9GE9SK7ByWdM987"
        } 
     url "https://api.bitbucket.org/2.0/repositories/mngcorp/deploy-maven-bluestack/src/master"
     authentication 
     	{
        basic(BasicAuthentication)
    	}
     }
	}

    }
}
```


In the build.gradle of to your application module, you can now import the Bluestack Google Adapter SDK by declaring it in the dependencies section:

```groovy
dependencies {

implementation 'com.madvertise:bluestack-gam-adapter:4.1.0'

}
```

#### b. Bluestack Mediation

Show [Set Up Sdk Section] Bluestack Mediation on your application project.


### 2. Initialize your ads

You can check our [Demo] page.

#### 2.1 Banner and Interstitial

**No additional code is required for integration.** 

You may now use MNG DFP Adapter to show [Interstitial Ads] and [Banner Ads] the same way it's described in the [DFP Documentation].The adapter code and the setup you did on your Google Ad Manager UI will allow MNG Ads to deliver ads.

#### 2.2 Native Ads


1) Assumes that your ad layout is in a file call **ad_unit_dfp.xml** for exemple in the res/layout folder.

2) Assumes you have a MAdvertiseNativeContainer in your View layout where the ad is to be placed.

```java
    <com.mngads.views.MAdvertiseNativeContainer
            android:id="@+id/native_container"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

```

3) The following code demonstrates how to build an AdLoader that can load native ads:

```java
AdLoader adLoader = new AdLoader.Builder(context, "YOUR PLACEMENT ID") 
                    .forNativeAd(nativeAd -> {
                      					
  					// This method sets the text, images and the native ad, etc into the ad view.
                    
                        NativeAdView mAdView = (NativeAdView) getLayoutInflater()
                                .inflate(R.layout.ad_native, null);
                        displayNativeAd(nativeAd, mAdView);
         
                             
                    })
                    .withAdListener(new AdListener() {
                        @Override
                        public void onAdFailedToLoad(@NotNull LoadAdError errorCode) {
                          	
                        // Handle the failure by logging, altering the UI...

                        }
                    })
                    .withNativeAdOptions(adOptions)
                    .build();

            AdManagerAdRequest.Builder adRequestBuilder = new AdManagerAdRequest.Builder();
            adRequestBuilder.addNetworkExtrasBundle(GADBlueStackMediationAdapter.class, getExtrasData());
            adLoader.loadAd(adRequestBuilder.build());


```
4) Once you have loaded an ad, all that remains is to display it to your users.

```java
private void displayNativeAd(NativeAd nativeAd, NativeAdView nativeAdView) {

	/* Display Texts Ad */ 
		// Locate the text view  
        TextView nativeAdTitle = nativeAdView.findViewById(R.id.nativeAdTitle);
        TextView nativeAdContext = nativeAdView.findViewById(R.id.nativeAdContext);
        TextView nativeAdCallToAction = nativeAdView.findViewById(R.id.nativeAdCallToAction);
	
		 // Set its text
        nativeAdTitle.setText(nativeAd.getHeadline());
        nativeAdContext.setText(nativeAd.getBody());
        nativeAdCallToAction.setText(nativeAd.getCallToAction());
        
		// Register it
	    nativeAdView.setCallToActionView(nativeAdCallToAction);
        nativeAdView.setHeadlineView(nativeAdTitle);
        nativeAdView.setBodyView(nativeAdContext);
	
	
	/* Display Icon Ad */ 
	
        if(nativeAd.getIcon()!=null)
        {
            if (nativeAd.getIcon().getUri() != null &&  !nativeAd.getIcon().getUri().toString().isEmpty()) {
                Glide.with(this).load(nativeAd.getIcon().getUri())
                        .into((ImageView) nativeAdView.findViewById(R.id.nativeAdIcon));
            }
            else
            {
                nativeAdView.setIconView(nativeAdView.findViewById(R.id.nativeAdIcon));
            }

        }
        else
        {
            nativeAdView.setIconView(nativeAdView.findViewById(R.id.nativeAdIcon));
        }
        
	/* Display Media Ad */
        
        if(nativeAd.getImages()!=null)
        {
            if (nativeAd.getImages().size() > 0 && nativeAd.getImages().get(0) != null ) {
                Glide.with(this).load(nativeAd.getImages().get(0).getUri())
                        .into((ImageView) nativeAdView.findViewById(R.id.nativeAdImage));
            }
            else
            {
                nativeAdView.setImageView(nativeAdView.findViewById(R.id.mediaContainer));
            }
        }
        else
        {
            nativeAdView.setImageView(nativeAdView.findViewById(R.id.mediaContainer));
        }
        
        
    // Register the NativeAdObject.
    nativeAdView.setStoreView(mMAdvertiseNativeContainer);
    nativeAdView.setNativeAd(nativeAd);

    // Ensure that the parent view doesn't already contain an ad view and place the AdView into the parent.
    frameLayout.removeAllViews();
    frameLayout.addView(nativeAdView);
}
```

#### 2.3 Rewarded Ads

1) The following code demonstrates how to load a rewarded ad:

```java

AdManagerAdRequest.Builder adRequestBuilder = new AdManagerAdRequest.Builder();
            adRequestBuilder.addNetworkExtrasBundle(GADBlueStackMediationAdapter.class, getExtrasData());
            
RewardedAd.load(context, DFP_REWARDED_AD_UNIT,
                adRequestBuilder.build(), new RewardedAdLoadCallback() {
    
@Override                
void onAdLoaded(RewardedAd rewarded) {
  rewarded.fullScreenContentCallback = new FullScreenContentCallback(){
  
@Override
void onAdFailedToShowFullScreenContent(AdError adError) {
   // Handle the failure by logging, altering the UI...
 }
                        }
                    };
@Override
void onAdFailedToLoad(LoadAdError error) {
// Handle the failure by logging, altering the UI...
 }
                }
            );


```

2) Once you have loaded an ad, all that remains is to display it to your users.

```java
private void displayRewardedAd(){
	mRewardedAd.show(activity, new OnUserEarnedRewardListener(){
	@Override
	void onUserEarnedReward(RewardItem var1){
	...
	}
	});
}
```

### 3. Custom targeting / Keywords

If you need to send your custom key-value pairs. You can specify key-value-targeting and keywords information in the ad request as follows: 


```java
AdManagerAdRequest request = new AdManagerAdRequest.Builder()
		.addKeyword("Keyword")
        .addCustomTargeting("key1", "value1")
        .addCustomTargeting("key2", "value2")
        .build();
```

and you must send your **custom key-value pairs** also as follows: 

1- Create a bundle of the extras :

```java
Bundle extras = new Bundle();
extras.putString("customTargeting","key1=value1;key2=value2");
extras.putString("keywords","key1=value1;key2=value2");
```

2- Add the extras to the addNetworkExtrasBundle() method as follows: 

```java
AdManagerAdRequest adRequest = new AdManagerAdRequest.Builder();
adRequest.addNetworkExtrasBundle(GADBlueStackMediationAdapter.class,extras)
.build();
```

The GADBlueStackMediationAdapter value corresponds to custom event adapter class name. 

 


[Google Ad Targeting page]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/targeting 
[Banner Ads]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/banner
[Interstitial Ads]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/interstitial
[Native Ads Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/native/advanced
[Set Up Sdk Section]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/setup
[mngads-dfp-adapter-x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/mngads-dfp-adapter-2.4.0.aar
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/
[DFP Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start
[Google Ad Manager UI]:https://admanager.google.com/
[MNGAds]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home
[Step 1]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/dfp-adapter-android#markdown-header-1-create-a-yield-groups
[Demo]:https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/DFPFragment.java