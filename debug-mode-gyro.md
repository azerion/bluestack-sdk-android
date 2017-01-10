# Debug Mode with Gyroscope Sensor


[TOC]

## Requirement

 - Require mng-ads.jar >= 2.3.3
 - An Android phone with Gyroscope Sensor


## 1. Enable Debug Mode
To enbale debug mode you need to set debug mode to true :

```
#!java
...
    MNGAdsFactory.setDebugModeEnabled(true);
...
```

Or see with Madvertise team in order to allow Debug Mode server side from Madvertise Console.

![screenshot-console.mng-ads.com 2017-01-06 09-38-10.png](https://bitbucket.org/repo/aen579/images/1429524612-screenshot-console.mng-ads.com%202017-01-06%2009-38-10.png)


## 2. Debug Madvertise Mediation SDK

You'll now be able to shake your phone while in your app to bring up Madvertise Debug menu.

![debug-menu.png](https://bitbucket.org/repo/GyRXRR/images/2129476937-debug-menu.png)

### 2.1 Madvertise Mediation Settings

This page check status of mediation in order to avoid librairies oversight, you can check version of each librairy too.

On following example, all mediation librairies have been added excepted presage (Ogury).

![mediation-settings.png](https://bitbucket.org/repo/GyRXRR/images/2114839361-mediation-settings.png)


### 2.2 Debug placements

On shaking, you can see the past 3 requests ( Madvertise Mediation) and check waterfall status. You can check [Preference Object] result (if location or keywords are shared with our SDK)

|      |    |
| --------|---------|
| 
![debug-placement-min.jpg](https://bitbucket.org/repo/aen579/images/495917987-debug-placement-min.jpg)  | ![debug-placement2.PNG](https://bitbucket.org/repo/aen579/images/843601529-debug-placement2.PNG)   |




[Manual Install]:https://bitbucket.org/mngcorp/mngads-demo-ios/wiki/Home#markdown-header-manual-install
[through pod "MNGAds"]:https://bitbucket.org/mngcorp/mngads-demo-ios/wiki/Using%20CocoaPods
[Preference Object]:https://bitbucket.org/mngcorp/mngads-demo-ios/wiki/Home#markdown-header-preferences-object