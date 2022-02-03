# Change log and Upgrading SDK for Android DFP Adapter

## Version 2.4.0
### Release date: February 3rd, 2022

**New features :**

- Added implementation of interstitialDidShown callback of MNGInterstitialListener in **MadvertiseCustomEventInterstitial.class**.

**Updated SDKs :**

- Use new version of BlueStack Mediation SDK (Version : 4.0.3)
- Use new version of Google Ads SDK (Version : 20.4.0)


## Version 2.3.0
### Release date: June 30th, 2020

**New features :**

- Added support of Google SDK v20.0.0 

**Updated SDKs :**

- Use new version of BlueStack Mediation SDK (Version : 3.6.2)
- Use new version of Google Ads SDK (Version : 20.2.0)

## Version 2.2.2
### Release date: September 18th, 2020

**SDK is now delivered through Maven/Bitbucket repository**

```groovy
allprojects {
    repositories {
        google()
        jcenter()
     
    // For All Bluestack SDKs (Mediation, CMP, Location, Adapter)
    maven 
    {
     credentials 
        {
         username "madvertise-maven"
         password "GpdGZ9GE9SK7ByWdM987"
        } 
     url "https://api.bitbucket.org/2.0/repositories/mngcorp/deploy-maven-bluestack/src/master"
     authentication 
     	{
        basic(BasicAuthentication)
    	}
     }
	}

    }
}
```

## Version 2.2.0 (Release date: August 12th, 2020) 


### Update Location method :  

 
Replace the following code from  :

```groovy
PublisherAdRequest request = new PublisherAdRequest.Builder()
        .setLocation(location)
        .build();
            
```
With the following code :

1- Create a bundle of the extras :

```java
Bundle extras = new Bundle();
extras.putString("consentFlag","CONSENT_FLAG");
```

The CONSENT_FLAG value (corresponds to a string : "0","1","2" or "3").

- "0" = Not allow to send location.
- "1" = When you managed location according to consent value.
- "2" or "3" = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

2- Add the extras to the addCustomEventExtrasBundle() method as follows: 

```java
PublisherAdRequest adRequest = new PublisherAdRequest.Builder()
.addCustomEventExtrasBundle("Madvertise_Custom_Event",extras)
.build();
```

The Madvertise_Custom_Event value corresponds to custom event adapter class name : 

 * **MadvertiseCustomEventBanner.class** for Banner Ads  
 * **MadvertiseCustomEventInterstitial.class** for Interstitial Ads   
 * **MadvertiseCustomEventNativead.class** for Native Ads  
            

### Update SDKs :  

In your app's build.gradle, don't forget to update your dependencies as following:

```java
//MNG Ads SDK  
implementation(name: 'mngads-sdk-3.2.0', ext: 'aar')

//Google Ads SDK
implementation 'com.google.android.gms:play-services-ads:19.2.0'
```