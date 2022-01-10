# Thumbnail Ad Integration for Android

[TOC]

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application, integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).


## Step 1. Init Thumbnail Factory

To create a Thumbnail Ad you must init an object with type MNGAdsSDKFactory :

```java
MNGAdsFactory mThumbnailFactory = new MNGAdsFactory(this);

```
## Step 2. Set Placement ID

You have also to set placement Id :

```java
mThumbnailFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

## Step 3. Implement the Listener
Next, implement the Thumbnail Ad Listener in your code. 

```java
// set thumbnail listener
mThumbnailFactory.setThumbnailListener(this);
```
The SDK will notify your listener of all possible events listed below :

- thumbnailDidLoad(): will be called by the SDK when your Thumbnail Ads is ready.

```java
@Override
public void thumbnailDidLoad() {
Log.d(TAG, "Thumbnail did load");
}
```

- thumbnailDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
public void thumbnailDidFail(Exception adsException) {
Log.e(TAG, "Thumbnail did fail :" + adsException.toString());
}
```
- thumbnailDidClosed(): will be called when Thumbnail Ads closed by the user. 

```java
@Override
public void thumbnailDidClosed() {
Log.d(TAG, "Thumbnail Closed")
}
```


- thumbnailDidDisplayed(): will be called when Thumbnail Ads has been displayed on the screen.

```java
@Override
public void thumbnailDidClosed() {
Log.d(TAG, "Thumbnail Closed")
}
```


## Step 4. Load a Thumbnail Ad

To start loading an ad, call the load method:

```java
mThumbnailFactory.loadThumbnail()
```

## Step 5. Show a Thumbnail Ad

To display the ad, call the showThumbnail method:


```java
...
@Override
public void thumbnailDidLoad() 
{
	mThumbnailFactory.showThumbnail();
}
```

## Troubleshooting
 
### Customize Thumbnail Ad size

In order to control the thumbnail size, call load method with maxWidth and maxHeight (Both values are in dp) parameters:

```java
mThumbnailFactory.load(maxWidth, maxHeight);
```

The following constraints apply on the values you can pass to these parameters:

- maxWidth and maxHeight must not be greater than the size of the screen.
- maxWidthandmaxHeight must be greater than or equal to 101dp.
- longest side, either maxWidth or maxHeight, must be greater than or equal to
 180dp.


### Check if a Thumbnail Ad is loaded

Call the following method to check if a Thumbnail Ad is ready to be displayed:

```java
mThumbnailFactory.isThumbnailReady()
```

### Set Thumbnail Ad position

To set the thumbnail position, call the show Thumbnail method with gravity and margin parameters:


```java
mThumbnailFactory.showThumbnail(gravity, xMargin, yMargin);
```

The show method takes the following parameters:

- gravity : the corner based on which the thumbnail will be positioned and it can have the following values:
	- MNGPreference.TOP_LEFT
	- MNGPreference.TOP_RIGHT
	- MNGPreference.BOTTOM_LEFT
	- MNGPreference.BOTTOM_RIGHT
- xMargin: distance on the x axis from the gravity corner to thumbnail. Value must be in dp.
- yMargin: distance on the y axis from the gravity corner to thumbnail. Value must be in dp.


### Disposing of Thumbnail Ad 

Once you are done using an Thumbnail Ad, you can call the hideThumbnail(Activity activity) method to release the resources it was using.

```java
mThumbnailFactory.hideThumbnail(activity)
```