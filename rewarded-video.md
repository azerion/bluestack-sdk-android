# MAdvertiseRewardedVideoAd for Android

[TOC]

**MAdvertiseRewardedVideoAd** that will serve to deliver rewarded video ads which are a full screen experience where users opt-in to view a video ad in exchange for something of value, such as virtual currency, in-app items, exclusive content, and more. The ad experience is 15-30 second non-skippable and contains an end card with a call to action. Upon completion of the full video, you will receive a callback to grant the suggested reward to the user.

##Init RewardedVideo

In order to use the rewarded video feature you have to instantiate the MNGRewardedVideo class and then you can add the MNGRewardedVideoListener. 

```java

...
import com.mngads.MNGRewardedVideo;
import com.mngads.listener.MNGRewardedVideoListener;
...

public class MainActivity extends Activity implements MNGRewardedVideoListener{
...
private MNGRewardedVideo mngRewardedVideo;
@Override
protected void onCreate(Bundle savedInstanceState) {
...
// init rewarded video
mngRewardedVideo = new MNGRewardedVideo(this);

// set a rewarded video listener
mngRewardedVideo.setRewardedVideoListener(this);
```
You have to add at least one placement

```java
mngRewardedVideo.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

#####Loading a reward video 
 Calling the 'loadRewardedVideo()' will result in making a request and having a callback in one of the methods of the rewarded video listener.

```java
mngRewardedVideo.loadRewardedVideo()
```
#####Handle callBacks

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
After loading the rewarded video you can request it to be displayed and check it's result as following
```java
...

boolean validDisplayAction = mRewardedVideo.showRewardedVideo()

if (validDisplayAction){
    Log.d(TAG, "rewarded video will be displayed");
}
...
```