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


![screenshot-admanager.google.com-2019.10.02-22_32_42.jpg](https://bitbucket.org/repo/GyRXRR/images/3231118223-screenshot-admanager.google.com-2019.10.02-22_32_42.jpg)

### 2. Define a custom event

On your Google Ad Manager UI, create a custom event 

![screenshot-admanager.google.com-2019.10.02-22_33_13.jpg](https://bitbucket.org/repo/GyRXRR/images/1642703664-screenshot-admanager.google.com-2019.10.02-22_33_13.jpg)

![screenshot-admanager.google.com-2019.10.02-22_36_16.jpg](https://bitbucket.org/repo/GyRXRR/images/4019010383-screenshot-admanager.google.com-2019.10.02-22_36_16.jpg)

![l.png](https://bitbucket.org/repo/GyRXRR/images/3601965291-l.png)


- Set the following class name for :
 * **Banner :** *Custom Name* : com.madvertise.MadvertiseCustomEventBanner and *Parameter* : /YOUR APP ID/PLACEMENT ID BANNER
 
 
 * **Interstitial :** *Custom Name* : com.madvertise.MadvertiseCustomEventInterstitial and *Parameter* : /YOUR APP ID/PLACEMENT ID INTERSTITIAL

 
 * **Native :** *Custom Name* : com.madvertise.MadvertiseCustomEventNativead and *Parameter* : /YOUR APP ID/PLACEMENT ID NATIVE
 


## Integrate MNGAds in your application project

### 1. Set Up

* Add our adapter [mngads-dfp-adapter-1.0.0.aar]
* [set up sdk section] MNGAds on your application project.



### 2. Initialize your ads

#### Interstitials and Banners
You may now use MNG DFP Adaptor to show interstitials and banners ads the same way it's described in the [DFP Documentation]. 
The adapter code and the setup you did on your Google Ad Manager UI will allow MNG Ads to deliver ads.

#### Native Ads 
// TBD

[set up sdk section]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-set-up-the-sdk
[mngads-dfp-adapter-1.0.0.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/downloads/mngads-dfp-adapter-1.0.0.aar
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mngads-sdk-2.7.aar?at=master
[DFP Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start
[Google Ad Manager UI]:https://admanager.google.com/
[MNGAds]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home