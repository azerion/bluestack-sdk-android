# Android DFP Adaptor

This guide is intended for publishers who want to use the Google Mobile Ads SDK to load and display ads from MNG Ads via mediation. It covers how to add MNG Ads to an ad unit's mediation configuration and how to integrate the MNG Ads SDK and adapter into an Android app.

### Supported ad formats
- Banners
- Interstitials
- Native Ads

### Requirements
- Android SDK 4.4 (API level 19) or later
- Google Play services 17.2.0 or later


## 1. Define a custom event

- Create an Ad Network (optional)
![screenshot-admanager.google.com-2019.10.02-22_36_16 (1).jpg](https://bitbucket.org/repo/GyRXRR/images/2101314984-screenshot-admanager.google.com-2019.10.02-22_36_16%20%281%29.jpg)

1. use Madvertise Ad-Network name
2. Choose Appsfire network
3. Allow mediation

- On your Google Ad Manager UI, create a custom event 

![screenshot-admanager.google.com-2019.10.02-22_32_42.jpg](https://bitbucket.org/repo/GyRXRR/images/3231118223-screenshot-admanager.google.com-2019.10.02-22_32_42.jpg)

![screenshot-admanager.google.com-2019.10.02-22_33_13.jpg](https://bitbucket.org/repo/GyRXRR/images/1642703664-screenshot-admanager.google.com-2019.10.02-22_33_13.jpg)

![l.png](https://bitbucket.org/repo/GyRXRR/images/3601965291-l.png)

![screenshot-admanager.google.com-2019.10.02-22_36_16.jpg](https://bitbucket.org/repo/GyRXRR/images/4019010383-screenshot-admanager.google.com-2019.10.02-22_36_16.jpg)


- Set the following class name for :
 * **Banner :** *Custom Name* : com.madvertise.MadvertiseCustomEventBanner and *Parameter* : /YOUR APP ID/PLACEMENT ID BANNER
 
 
 * **Interstitial :** *Custom Name* : com.madvertise.MadvertiseCustomEventInterstitial and *Parameter* : /YOUR APP ID/PLACEMENT ID INTERSTITIAL

 
 * **Native :** *Custom Name* : com.madvertise.MadvertiseCustomEventNativead and *Parameter* : /YOUR APP ID/PLACEMENT ID NATIVE
 


## 2. Integrate MNG in your application project

Add the mngads Mopub adapter [mngads-dfp-adapter-1.0.0.aar] and MNG SDK [mngads-sdk-x.aar Android SDK]  to the libs folder of your application project.



## 3. Initialize your ads

### Interstitials and Banners
You may now use MNG DFP Adaptor to show interstitials and banners ads the same way it's described in the [DFP Documentation]. 
The adapter code and the setup you did on your Google Ad Manager UI will allow MNG Ads to deliver ads.

### Native Ads 
// TBD

[set up sdk section]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/Home#markdown-header-set-up-the-sdk
[mngads-dfp-adapter-1.0.0.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MopubDemo/app/libs/mngads-mopub-adapter.aar?at=master&fileviewer=file-view-default
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/mngads-sdk-2.7.aar?at=master
[DFP Documentation]:https://developers.google.com/ad-manager/mobile-ads-sdk/android/quick-start