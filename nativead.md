# Native ads Integration for Android

[TOC]

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).

A native ad is a custom designed ad that fits seamlessly with your app. If done well, ads can blend in naturally with your interface.

## Step 1. Init nativeAd factory

To create a nativeAd you have to init an object with type MNGAdsSDKFactory.

```java
MNGAdsFactory mngAdsNativeAdsFactory = new MNGAdsFactory(this);

```

## Step 2. Set Placement ID

You have also to set placement Id :

```java
mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

## Step 3. Implement the Listener

Next, implement the Native ads Listener in your code. 

```java 
mngAdsNativeAdsFactory.setNativeListener
```

The SDK will notify your Listener of all possible events listed below :

- nativeObjectDidLoad(): will be called by the SDK when your nativeObject is ready. now you can create your own view.

```java
@Override
  public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
    Log.d(TAG, "native Object did load ");
  }

```

- nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
  public void nativeObjectDidFail(Exception adsException) {
    Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
  }

```


## Step 4. Loading Native ad

To make a request you have to call 'loadNative()'. This is a void method, result will be returned in the callback.

```java
mngAdsNativeAdsFactory.loadNative()
``` 


## Step 5. Rendering the native ad


### Build Native Ad UI

Once a native ad is loaded, you may retrieve its metadata with the following methods:


```java

// Get the app name
String title=nativeObject.getTitle();

// Get the app description (tagline)
String body=nativeObject.getBody();

// Get the "Ad" badge bitmap. You must show this bitmap on your ad view to denote an ad
Bitmap badge=nativeObject.getBadge();

// Get the localized text to print on the call to action button, such as "DOWNLOAD , LEARNE MORE ..."
String callToAction=nativeObject.getCallToAction();

```

 
##### **Ad Title**

 - 50 maximum character length string of ad headline
 - Provide enough space to display the entire length of the Ad Title
 - asset name : **nativeObject.getTitle()**
 
 
##### **Ad Text**

 - 150 maximum character length string of ad text
 - Provide enough space to display the entire length of the Ad Text
 - asset name : **nativeObject.getBody()**
 
##### **CTA Text**

 - Text for a button
 - 12 characters maximum
 - asset name : **nativeObject.getCallToAction()**
 
 
##### **Sponsored Marker**

 - Badge view (an icon)
 - change according ad network
 - must be inserted on top right
 - this is automatically added to the TOP-RIGHT corner of your native ad layout.
 
##### **Distinguishable Ad**

 - “Ad” (can be localized)
 - Badge that says “AD” and is at least 15x15px (can be localized)
 - change according ad network
 - must be inserted on top left
 - asset name : **nativeObject.getBadge()**

### Registering views used to render the ad 

MNGNativeObject have all required metadata to build your customized native UI. Your native ad layout should have MAdvertiseNativeContainer as it's root viewGroup container.


```java
// Register your custom ad view to automatically report impressions and clicks, and to display icon, image cover or the media video 
// This is mandatory
nativeObject.registerViewForInteraction(nativeAdContainerView,mediaViewGroup,iconImageView,nativeAdCallToActionView);

``` 

The registerViewForInteraction method :

- Handles all the user interactions with your custom layout (clicks, impressions ...)

- Display icon, image cover or the media video 


It accepts four arguments: 

- The first is the MAdvertiseNativeContainer that should be your custom layout's root view.
- The second is the media Container, the sdk will handle the rendering process ( displaying) the image cover or the media video inside the view group that depends on the ad network result.
- The third is the image View for NativeAd's ad Icon
- The fourth is the callToAction View that handles the click event of your ad.


**Note :**The MAdvertiseNativeContainer is a custom ViewGroup that extends FrameLayout so you can use it as it is or you can put your layout inside of it which is the method we recommend.

![2587222597-nativeAd-min-min (1).png](https://bitbucket.org/repo/GyRXRR/images/165955247-2587222597-nativeAd-min-min%20%281%29.png)


## Troubleshooting

### Hide Icon or Image Cover

Put **null** to hide icon (instead of iconImageView) or image cover (instead of mediaViewGroup). 

```java
nativeObject.registerViewForInteraction(nativeAdContainerView,null,null,nativeAdCallToActionView);
```

### Customize Native Ad Badge Text

You can use a custom badge Text for the native ad.

```java
nativeObject.getBadge(getActivity(),"String to be displayed in the badge");
}
```

### Cache

Ad metadata that you receive can be cached and re-used for up to 3 hours. If you plan to use the metadata after this time period, make a call to load a new ad.

### Memory managment

When you have finished your ads plant you must free the memory.

```java
@Override
protected void onDestroy() {
mngAdsNativeAdsFactory.releaseMemory();
super.onDestroy();
}
```

### isBusy

Before making a request if you want to check that factory is not busy (Ads factory is busy means that it has not finished the previous request yet).

isBusy will be set to :

- **true :** when factory starts handling request.

- **false :** when factory finishes handling request.

**Example**:

```java
if (!mngAdsNativeAdsFactory.isBusy()) {

Log.d(TAG, "Ads Factory is not busy");
mngAdsNativeAdsFactory.loadInterstitial(false);
} else {
Log.d(TAG, "Ads Factory is busy");
}
```

### Customize Native Ad AdChoice

The adChoice is automatically added to the top right corner of your native ad layout but you can change that position by using the MNGPreference.setAdChoicePosition(int position) before loading your ad.
The position argument can be one of these:

```java
TOP_RIGHT
TOP_LEFT
BOTTOM_RIGHT
BOTTOM_LEFT
```
For example:

```java
mngPreferences.setAdChoicePosition(MNGPreferences.TOP_LEFT);
mngAdsNativeAdsFactory.loadNative(mngPreference)
```


###  Click - registerViewForInteraction

It's **HIGHLY** recommended to only register ONE and ONLY one view for interaction , because some of the AdNetworks only accept one view and if you try to assign more than one then probably none of the views you assign will be responsive.

### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked

```java
// set click listener
mngAdsNativeAdsFactory.setClickListener(this);


...
@Override
public void onAdClicked() {
Log.d(TAG, "Ad Clicked");
}
...
```


### Ad refresh listener
You can also implement MNG refresh listener callback to detect when an Ad refreshed

```java
// set refresh listener
mngAdsNativeAdsFactory.setRefreshListener(this);

...
@Override
public void onRefreshSucceed() {
Log.d(TAG, "refresh succeed");
}

@Override
public void onRefreshFailed(Exception e) {
Log.d(TAG, "refresh failed");
}
...
```


### Preferences Object
Preferences object is an optional parameter that allow you select ads by user info.
informations that you can set are:

- **Age :**  age of user
- **Location :**  geographical position of the user.
- **Language :** : language of user (ISO code)
- **Gender :**  gender of user
- **KeyWord :**  Use free-form key-values when you want to pass targeting values dynamically into an ad tag based on information you collect from your users. You can also use free-form key-values when there are too many possible values to define in advance. Separator in case of multiple entries is **;**.
- **Content URL :**  URL for content related to your app (url must be a string which length not exceed 512 caracters).

```java

Location  myLocation = new Location("I");
myLocation.setLatitude(35.757866);
myLocation.setLongitude(10.810547);

mngPreference = new MNGPreference();
mngPreference.setLocation(location,CONSENT_FLAG,context);
mngPreference.setAge(28);
mngPreference.setGender(MNGGender.MNGGenderFemale);
mngPreference.setKeyword("brand=myBrand;category=sport");
mngPreference.setLanguage("fr");
mngPreference.setContentUrl("put your content url here")


mngAdsNativeAdsFactory.loadNative(mngPreference);

```
**Note :** 

- This [link] can help you to get device location.

- Do not serialize Location object (like transforming it into a string using gson library), this may lead to a fatal runtime error when that instance is reused.

- The setLocation method takes the following parameters:

	- the Location instance.
	- the CONSENT_FLAG value (corresponds to a int : 0,1,2 or 3).
		- 0 = Not allow to send location.
		- 1 = When you managed location according to consent value.
		- 2 and 3 = Allow the SDK to managed location directly in accordance with the consent value use TCF v1 or TCF v2, see with the madvertise team it depends on your implementation.

	- the Context instance.

### Exceptions
|Exception|Error code|Message|Meaning|
| --- | --- | --- | --- |
|MAdvertiseWrongPlacementIdException|WRONG_PLACEMENT_ERROR = 0   |    Wrong placement | You have set a wrong placement |
|MAdvertiseInternetException|NO_INTERNET_ERROR = 1   |    No Internet | There is no internet connection at the moment      |
|MAdvertiseSDKUninitializedException|SDK_UNINITIALIZED_ERROR = 2   |    MNGAds is not initialized | The sdk is not initialized, you have to call  MNGAdsFactory.initialize(context,"your app id");      |
|MAdvertiseRequestCappedException|CAPPED_REQUEST_ERROR = 3  |    Your request has been capped | Your request is capped, If you are in doubt, check your capping value related to the placement|
|MAdvertiseBusyFactoryException|BUSY_FACTORY_ERROR = 5   |    Your factory is busy| Your factory is busy by an other request at the moment     |
|MAdvertiseNoAdException|NO_AD_ERROR = 7   |    No Ad found | Therese no ad to dilver at the moment     |
|MAdvertiseTimeOutException|TIME_OUT_ERROR = 10   |  no ad to deliver before time out | Therese no ad to deliver before the specified time out  |

**Handle Exception :** If you want to check which exception was invoked, in the didFail callback you have to cast the exception to MAdvertiseException and then use getErrorCode() to get exception code.
Also you can get exception message by calling getMessage().
In the example below we use interstitialDidFail, even you can use this logic in all our didFail callBack(bannerDidFail, infeedDidFail,nativeAdCollectionDidFail and nativeObjectDidFail)

```java
@Override
public void interstitialDidFail(Exception e) {

MAdvertiseException adException=(MAdvertiseException)e;

switch (adException.getErrorCode())
{
case MAdvertiseException.BUSY_FACTORY_ERROR :
case MAdvertiseException.INTERSTITIAL_ALREADY_SHOWN_ERROR :
.
.
.

}
Log.e(TAG, "Interstitial did fail : " + adException.getMessage()+" error code "+adException.getErrorCode());
}
```

# Example

 - https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/NativeAdFragment.java
 - https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/NativeListFragment.java

content Ad  | carousel Ad | carousel Ad
------------- | ------------- | -------------  | -------------
![nativeAd-1.png](https://bitbucket.org/repo/GyRXRR/images/1430534000-nativeAd-1.png)|![nativeAd-2.png](https://bitbucket.org/repo/GyRXRR/images/2633774569-nativeAd-2.png)|![carousel2-mngads-android-min.png](https://bitbucket.org/repo/GyRXRR/images/771135904-carousel2-mngads-android-min.png)