# BlueStack Android SDK FAQ 

This document answers the following frequently asked questions:


## If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. 

If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. Edit your project’s proguard-project.txt file to add the following: [https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/proguard-rules.pro?at=master&fileviewer=file-view-default] (https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/proguard-rules.pro?at=master&fileviewer=file-view-default)

## How many placement IDs should I create?
You need to create a different placement ID for any of the different ad formats (banner, interstitial and native) and each unique path that you implement within your app. 
If you use native ads in feed and plan to show several units as the user scrolls, then you should use the same placement ID for all the native ad units.

## Interstitial did load callback without display

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

## Fatal signal 11 (SIGSEGV) gson

Do not serialize Location object (like transforming it into a string using gson library), this may lead to a fatal runtime error when that instance is reused.


## Optimized use case for several ad formats on one page

When trying to display several ad formats on one page try to synchronize your requests instead of making multiple ones at the some time. By making the requests at the same time you are decreasing your chance of receving an Ad and you are making your app slow .You can check the number of MNGAdsFactory running a request by calling :


```java
    int mNumberOfRunningFactory=MNGAdsFactory.getNumberOfRunningFactory() ;
```

You can see an example on [AdsFragment.java].



[AdsFragment.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/AdsFragment.java