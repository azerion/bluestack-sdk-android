# SyncDisplay Ad Integration for Android

[TOC]

## Overview

- Before You Start. Make sure that you have correctly integrated the MNG SDK into your application, integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

- Note : 
	- The Sync Display SDK will not be functional with Android SDK version below 21.
	- The audio recognition will be disable on Android SDK version below 26.


## Step 1. Installation Sync

- In your project's top-level build.gradle file, ensure that our private repository is included:


```java
maven {
	url 'https://api.bitbucket.org/2.0/repositories/sync_tv/maven-sync/src/master'
   credentials 
   			{
           username "guestsync"
           password "ELn3qwzMCWmJcawgHdqM"
           }
   authentication 
   		{
       basic(BasicAuthentication)
       }
     }

```

- Then, in your app-level build.gradle file, declare syncdisplay as a dependency

```java
implementation 'tv.sync:syncdisplay:3.2.0'
```

- To get ads synchronization with tv/radio, you need to add record permission into manifest explicitly

```java
<manifest>
    ...
    <!--Activate audio recognition-->
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <application>
        ...
        <!--Set configChanges to activities where advertising could be display-->
        <activity android:configChanges="orientation|screenSize" />
        ...
    </application>
</manifest>
```

## Step 2. Init MNGAds Factory 

To create a Sync Ad you must init an object with type MNGAdsFactory :

```java
MNGAdsFactory mSyncFactory = new MNGAdsFactory(this);

```
## Step 3. Set Placement ID

You have also to set placement Id :

```java
mSyncFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

## Step 4. Implement the Listener

Next, implement the Sync Ad Listener in your code. 

```java
// set Sync listener
mSyncFactory.setSyncListener(this);
```
The SDK will notify your listener of all possible events listed below :

- syncDisplayDidLoad(View view): will be called by the SDK when your Sync Ads is ready.

```java
@Override
public void syncDisplayDidLoad(View view) {
Log.d(TAG, "Sync did load");
if (this.getActivity() != null) {
            ((ViewGroup) this.getActivity().findViewById(android.R.id.content)).addView(view);
}
}
```

- syncDisplayDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
public void syncDisplayDidFail(Exception adsException) {
Log.e(TAG, "Sync did fail :" + adsException.toString());
}
```

## Step 5. Load a Sync Ad

To start loading an ad, call the load method:

```java
mSyncFactory.loadSync()
```