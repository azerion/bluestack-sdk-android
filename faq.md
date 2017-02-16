# MngAds FAQ #

This document answers the following frequently asked questions:

[TOC]
# Implementation #
## If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. 

If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. Edit your project’s proguard-project.txt file to add the following:

 - https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/proguard-rules.pro?at=master&fileviewer=file-view-default

## What types of ad units are available? ##
There are three ad units available to use in your app:

 - Standard banner ads
 - Interstitial ads
 - Native ad API

## How many placement IDs should I create? ##
You need to create a different placement ID for any of the different ad formats (banner, interstitial and native) and each unique path that you implement within your app. 
If you use native ads in feed and plan to show several units as the user scrolls, then you should use the same placement ID for all the native ad units.
## What are "Native Ads ##
Native ads allow you to customize the look and feel of ads to match that of your app. Native ads work by receiving the metadata for ads through MngAds.


##  interstitial did load callback without display

**You must use an instance per activity.**

Some AdNetworks show their interstitials on top of an Activity layout and then disappear. Therefore, you must instantiate **once MNGAdsFactory by activity** (used for display the interstitial). If you want to build an interstitials manager for your app to handle all interstitials requests, you should make sure to instantiate MNGAdsFactory with the activity that will make the request.

##android:noHistory

http://developer.android.com/guide/topics/manifest/activity-element.html#nohist

android:noHistory
Whether or not the activity should be removed from the activity stack and finished (its finish() method called) when the user navigates away from it and it's no longer visible on screen .

Therefore, do not use

```java
android:noHistory="true"
```