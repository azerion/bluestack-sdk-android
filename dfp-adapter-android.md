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

* Add our adapter [mngads-dfp-adapter-1.0.0.aar]
* [set up sdk section] MNGAds on your application project.



### 2. Initialize your ads

#### Init Preference

You may now use MNG DFP Adaptor to show interstitials and banners ads the same way it's described in the [DFP Documentation]. 
The adapter code and the setup you did on your Google Ad Manager UI will allow MNG Ads to deliver ads.

##### *Targeting*
If you need to send your preferences (Age, Location, Keyword, Content URL) use the addCustomEventExtrasBundle() method.

```java
PublisherAdRequest adRequest = new PublisherAdRequest.Builder()
.addCustomEventExtrasBundle(MadvertiseCustomEventInterstitial.class,getExtrasData())
.build();
```
You must pass custom event adapter class name for :

 * **Banner :** MadvertiseCustomEventBanner.class 
 
 * **Interstitial :** MadvertiseCustomEventInterstitial.class

and a bundle of the extras :

```java
Bundle extras = new Bundle();
Location location = Utils.getCurrentLocation(getActivity());
if (location != null) {
extras.putDouble("LATITUDE", location.getLatitude());
 extras.putDouble("LONGITUDE", location.getLongitude());
 }
extras.putInt("AGE", 25);
extras.putString("KEYWORD", Constants.MNGADS_KEYWORD);
extras.putString("CONTENT_URL", Constants.MNGADS_CONTENT_URL);
```

[set up sdk section]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-set-up-the-sdk
[mngads-dfp-adapter-1.0.0.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/mngads-dfp-adapter-1.0.0.aar
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mngads-sdk-2.7.aar?at=master
[DFP Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start
[Google Ad Manager UI]:https://admanager.google.com/
[MNGAds]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home
[Step 1]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/dfp-adapter-android#markdown-header-1-create-a-yield-groups