### MAdvertiseBeacon

Get Ebeacon technology to propose to the advertisers to target the users inside the point of sale. 
- An installation base of 12,500 ebeacons ready to track the users.
- An exclusive format in Push notification to the users inside a tabacco shop, press shop, pharmay or mall.

### Setup

**download and extract following files and place them in the /libs folder in your project**

- [nl.qbusict:cupboard:2.1.4]
- [de.greenrobot:eventbus:2.4.0]
- [com.squareup.retrofit2:converter-jackson:2.0.0]
- [b4s-android-sdk]
- [b4s-android-sdk-playservices830]

### Initializing Beacons

You have to init becon in your application class
MAdvertiseBeaconAdapter.initBeacons(this) should be called before MNGAdsFactory.initialize(this,"YOUR_APP_ID");


```java
public class DemoApp extends Application{

@Override
public void onCreate() {
super.onCreate();
MAdvertiseBeaconAdapter.initBeacons(this);
MNGAdsFactory.initialize(this,"YOUR_APP_ID");
}
}
```
you have to edit your build.gradle file
```java
buildTypes {

packagingOptions {
exclude 'META-INF/ASL2.0'
exclude 'META-INF/LICENSE'
exclude 'META-INF/NOTICE'
}

}



dependencies {

compile 'nl.qbusict:cupboard:2.1.4'
compile 'de.greenrobot:eventbus:2.4.0'
compile 'com.squareup.retrofit2:converter-jackson:2.0.0'
compile (name:'b4s-android-sdk', ext:'aar')
compile (name:'b4s-android-sdk-playservices830', ext:'aar')

}
```
and you need to declare your flat file repository.
```
allprojects {
repositories {
jcenter()
flatDir{
dirs 'libs'
}
}

}
```


[nl.qbusict:cupboard:2.1.4]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[de.greenrobot:eventbus:2.4.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[com.squareup.retrofit2:converter-jackson:2.0.0]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[b4s-android-sdk-playservices830]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master