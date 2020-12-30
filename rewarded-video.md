# Rewarded Video Ad Integration for Android

[TOC]

**MAdvertiseRewardedVideoAd** that will serve to deliver rewarded video ads which are a full screen experience where users opt-in to view a video ad in exchange for something of value, such as virtual currency, in-app items, exclusive content, and more. The ad experience is 15-30 second non-skippable and contains an end card with a call to action. Upon completion of the full video, you will receive a callback to grant the suggested reward to the user.

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

## Integration

### Step 1. Init RewardedVideo class

In order to use the rewarded video feature you have to instantiate the MNGRewardedVideo class and then you can add the MNGRewardedVideoListener. 

```java
MAdvertiseRewardedVideo mRewardedVideo = new MAdvertiseRewardedVideo(this);
```

### Step 2. Set Placement ID

You have also to set placement Id :

```java
mngRewardedVideo.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

### Step 3. Implement the Listener
Next, implement the RewardedVideo Listener in your code. 

```java
// set a rewarded video listener
mngRewardedVideo.setRewardedVideoListener(this);
```

The SDK will notify your Listener of all possible events listed below :

```java
    @Override
    public void onRewardedVideoError(Exception e) {
	    //This is called when an error is occurred while loading the reward video.
    }

    @Override
    public void onRewardedVideoLoaded() {
		//This is called when a rewarded video is loaded and ready to be displayed
    }

    @Override
    public void onRewardedVideoClicked() {
		//This is called when the video is clicked, this can be ignored if the adNetwork doesn't respond to a click event.
    }

    @Override
    public void onRewardedVideoClosed() {
		//This is called when a displayed video is closed.
    }

    @Override
    public void onRewardedVideoAppeared() {
	    //This is called wen a loaded rewarded video appears on the screen.
    }

    @Override
    public void onVideoRewarded(MNGVideoReward mngVideoReward) {
		//At the end of a rewarded video, a reward object is usually returned, although if it did not the object mngVideoReward returned will be null.
    }
```


### Step 4. Loading Rewarded Video ad

Calling the 'loadRewardedVideo()' will result in making a request and having a callback in one of the methods of the rewarded video listener.

```java
mngRewardedVideo.loadRewardedVideo()
```

### Step 5. Display Rewarded Video ad

After loading the rewarded video you can request it to be displayed and check it's result as following :

```java
boolean validDisplayAction = mRewardedVideo.showRewardedVideo()

if (validDisplayAction){
    Log.d(TAG, "rewarded video will be displayed");
}
```

## Troubleshooting

### Check if a Rewarded Video Ad is loaded

Call the following method to check if a Rewarded Video Ad is ready to be displayed :

```java
mRewardedVideo.isRewardedVideoReady()
```


## Example

Here is an example : [RewardedVideoFragment.java](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/RewardedVideoFragment.java)