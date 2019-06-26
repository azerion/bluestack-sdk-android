#Amazon APS 

##Installation


1. Download https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/libs/DTBAndroidSDK-7.4.3.aar

2.  update your dependencies as following :

replace
```groovy
implementation files('libs/amazon-ads-5.9.0.jar')
```

by

```groovy
implementation(name: 'DTBAndroidSDK-7.4.3', ext: 'aar')
```