# Rewarded Video Ad Integration for Android

[TOC]

**MAdvertiseRewardedVideoAd** that will serve to deliver rewarded video ads which are a full screen experience where users opt-in to view a video ad in exchange for something of value, such as virtual currency, in-app items, exclusive content, and more. The ad experience is 15-30 second non-skippable and contains an end card with a call to action. Upon completion of the full video, you will receive a callback to grant the suggested reward to the user.

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

## Integration

### Step 1. Init RewardedVideo class

In order to use the rewarded video feature you have to instantiate the MNGRewardedVideo class and then you can add the MNGRewardedVideoListener. 

**Java :**

```java
MAdvertiseRewardedVideo rewardedVideo = new MAdvertiseRewardedVideo(this);
```

**Kotlin :**

```kotlin
MAdvertiseRewardedVideo rewardedVideo = MAdvertiseRewardedVideo(this)
```

### Step 2. Set Placement ID

You have also to set placement Id :

**Java :**

```java
rewardedVideo.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

**Kotlin :**

```kotlin
rewardedVideo.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID")
```

### Step 3. Implement the Listener
Next, implement the RewardedVideo Listener in your code. 

**Java :**

```java
// set a rewarded video listener
rewardedVideo.setRewardedVideoListener(this);
```

**Kotlin :**

```kotlin
// set a rewarded video listener
rewardedVideo.setRewardedVideoListener(this)
```

The SDK will notify your Listener of all possible events listed below :

**Java :**

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
   public void onRewardedVideoCompleted(MAdvertiseVideoReward videoReward) {
    
        Log.d(TAG, "onRewardedVideoCompleted");
        progressBar.setVisibility(View.GONE);

        if (videoReward != null) {

            Log.d(TAG, "onVideoRewarded, type: " + videoReward.getType() + " , amount: " + videoReward.getAmount());

            mLog.setText("Video rewarded\nType: " + videoReward.getType() + "\namount: " + videoReward.getAmount());

        } else {

            Log.d(TAG, "onVideoRewarded with no reward object");

            mLog.setText("Video reward event");
        }

    }
```

**Kotlin :**

```kotlin
    override fun onRewardedVideoError(e: Exception) {
	    //This is called when an error is occurred while loading the reward video.
    }

    override fun onRewardedVideoLoaded() {
		//This is called when a rewarded video is loaded and ready to be displayed
    }

    override fun onRewardedVideoClicked() {
		//This is called when the video is clicked, this can be ignored if the adNetwork doesn't respond to a click event.
    }

    override fun onRewardedVideoClosed() {
		//This is called when a displayed video is closed.
    }

    override fun onRewardedVideoAppeared() {
	    //This is called wen a loaded rewarded video appears on the screen.
    }

    override fun onRewardedVideoCompleted(videoReward: MAdvertiseVideoReward?) {
    
        Log.d(TAG, "onRewardedVideoCompleted")
        progressBar.visibility = View.GONE

        videoReward?.let {
            Log.d(
                TAG,
                "onVideoRewarded, type: ${videoReward.type}, amount: ${videoReward.amount}"
            )
            rewardedVideoLog.text =
                ("Video rewarded \n Type: " + videoReward.type + " \n amount: " + videoReward.amount).trimIndent()
        } ?: run {
            Log.d(TAG, "onVideoRewarded with no reward object")
            rewardedVideoLog.text = "Video reward event"
        }

    }
```

### Step 4. Loading Rewarded Video ad

Calling the 'loadRewardedVideo()' will result in making a request and having a callback in one of the methods of the rewarded video listener.

**Java :**

```java
rewardedVideo.loadRewardedVideo();
```

**Kotlin :**

```kotlin
rewardedVideo.loadRewardedVideo()
```

### Step 5. Display Rewarded Video ad

After loading the rewarded video you can request it to be displayed and check it's result as following :

**Java :**

```java
boolean validDisplayAction = rewardedVideo.showRewardedVideo();

if (validDisplayAction){
    Log.d(TAG, "rewarded video will be displayed");
}
```

**Kotlin :**

```kotlin
boolean validDisplayAction = rewardedVideo.showRewardedVideo()

if (validDisplayAction){
    Log.d(TAG, "rewarded video will be displayed")
}
```

## Troubleshooting

### Check if a Rewarded Video Ad is loaded

Call the following method to check if a Rewarded Video Ad is ready to be displayed :

**Java :**

```java
rewardedVideo.isRewardedVideoReady();
```

**Kotlin :**

```kotlin
rewardedVideo.isRewardedVideoReady()
```

### Preferences Object
Preferences object is an optional parameter that allow you select ads by user info.
informations that you can set are:

- **Location :**  geographical position of the user.
- **KeyWord :**  Use free-form key-values when you want to pass targeting values dynamically into an ad tag based on information you collect from your users. You can also use free-form key-values when there are too many possible values to define in advance. Separator in case of multiple entries is **;**.
- **Content URL :**  URL for content related to your app (url must be a string which length not exceed 512 caracters).

**Java :**

```java

Location  myLocation = new Location("I");
myLocation.setLatitude(35.757866);
myLocation.setLongitude(10.810547);

mngPreference = new MNGPreference();
mngPreference.setLocation(location, CONSENT_FLAG, context);
mngPreference.setKeyword("brand=myBrand;category=sport");
mngPreference.setContentUrl("put your content url here");

mRewardedVideo.loadRewardedVideo(mngPreference);

```

**Kotlin :**

```kotlin

Location  myLocation = Location("I")
myLocation.latitude = 35.757866
myLocation.longitude = 10.810547

mngPreference = MNGPreference()
mngPreference.setLocation(location, CONSENT_FLAG, context)
mngPreference.setKeyword("brand=myBrand;category=sport")
mngPreference.setContentUrl("put your content url here")

mRewardedVideo.loadRewardedVideo(mngPreference)

```
**Note :** 

- The setLocation method takes the following parameters:

	- the Location instance.
	- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3).
		- 0 = Not allow to send location.
		- 1 = When you managed location according to consent value.
		- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

	- the Context instance.



## Example

Here is an example : [RewardedVideoFragment.kt](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/RewardedVideoFragment.kt)