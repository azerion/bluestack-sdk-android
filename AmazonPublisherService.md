#AmazonPublisherService


* ***Manual  installation*** : 


1. Go to [DTBAndroidSDK-7.4.3.aar](https://bitbucket.org/mngcorp/mngads-demo-android/downloads/DTBAndroidSDK-7.4.3.aar)
2. replace
```groovy
implementation files('libs/amazon-ads-5.9.0.jar')
```

by

```groovy
implementation(name: 'DTBAndroidSDK-7.4.3', ext: 'aar')
```