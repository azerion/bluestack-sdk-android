# Best practice Mngads : optimized use case for several ad formats on one page

When trying to display several ad formats on one page try to synchronize your requests instead of making multiple ones at the some time. By making the requests at the same time you are decreasing your chance of receving an Ad and you are making your app slow .You can check the number of MNGAdsFactory running a request by calling :

```
#!java
    int mNumberOfRunningFactory=MNGAdsFactory.getNumberOfRunningFactory() ;
```

You can see an example on [AdsFragment.java].


[AdsFragment.java]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.java?at=master


# Design Guidelines for MNG Ads

## Banner -  (50px or 90px)
Banner -  (50px or 90px) | Description| 
------------- | ------------- |
![banner50-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/288211594-banner50-mngads-android-min.png) | A banner is a small bar ad that appears at the bottom or top of your content. Usually sized 320 x 50. Only include one ad per page or show one ad at a time if scrolling. In all cases, **the banner width is flexible with a minimum of 320px.**. If you are building your app for iPad  consider using 90px and 50px for iphone.

## Square - Medium rectangle (300 x 250)

Square - Medium rectangle (300 x 250) | Description| 
------------- | ------------- |
 ![banner250-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/4181983461-banner250-mngads-android-min.png)  |Square banner also known as a *medium rectangle* (300 x 250). This format can increase earnings when both text and image ads are enabled. Performs well when embedded within text content or at the end of articles.

## Interstitial
Interstitial | Description| 
------------- | ------------- |
![interstitial-appsfire-mngads-android-min-min.png](https://bitbucket.org/repo/GyRXRR/images/15176750-interstitial-appsfire-mngads-android-min-min.png) | An interstitial is a full screen ad that appears at a natural transition point in your app.

## Native Ad

A native ad is a custom designed ad that fits seamlessly with your app. If done well, ads can blend in naturally with your interface.


content Ad  | carousel Ad | carousel Ad
------------- | ------------- | -------------  | -------------
![nativeAd-1.png](https://bitbucket.org/repo/GyRXRR/images/1430534000-nativeAd-1.png)|![nativeAd-2.png](https://bitbucket.org/repo/GyRXRR/images/2633774569-nativeAd-2.png)|![carousel2-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/771135904-carousel2-mngads-android-min.png)