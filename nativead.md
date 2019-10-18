# Native ads
[TOC]

MNG supports native ads, that allow you to retrieve the metadata of ad campaigns and present the ads yourself, within the context of your app, using your own art style. You are fully responsible
for rendering the ad views using the information we supply. Native ads however offer methods to help you register impressions and clicks on your custom view that has **MAdvertiseNativeContaineras it's root layout** . 

## Requesting a native ad

##### Init factory

To create a nativeAd  you have to init an object with type MNGAdsSDKFactory and set the nativeListener.

```java
public class MainActivity extends Activity implements MNGNativeListener{
...
   private MNGAdsFactory mngAdsNativeAdsFactory;
@Override
     protected void onCreate(Bundle savedInstanceState) {
...
  // init native factory
    mngAdsNativeAdsFactory = new MNGAdsFactory(this);

  // set native listener
    mngAdsNativeAdsFactory.setNativeListener(this);

```
##### Set Placement ID

You have also to set placementId (minimum one time)

```java
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
##### Make a request for native ad
To make a request you have to call 'loadNative()'. This is a void method, result will be returned in the callback.


```java
mngAdsNativeAdsFactory.loadNative()
```
##### Handle callBack from NativeListener
adsAdapter.nativeObjectDidLoad(): will be called by the SDK when your nativeObject is ready. now you can create your own view.

```java
@Override
  public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
    Log.d(TAG, "native Object did load ");
  }

```

adsAdapter.nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

```java
@Override
  public void nativeObjectDidFail(Exception adsException) {
    Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
  }

```

## Native Ad Assets

Once a native ad is loaded, you may retrieve its metadata with the following methods:

 
### **Ad Title**

 - 50 maximum character length string of ad headline
 - Provide enough space to display the entire length of the Ad Title
 - asset name : **nativeObject.getTitle()**
 
 
### **Ad Text**

 - 150 maximum character length string of ad text
 - Provide enough space to display the entire length of the Ad Text
 - asset name : **nativeObject.getBody()**
 
### **CTA Text**

 - Text for a button
 - 12 characters maximum
 - asset name : **nativeObject.getCallToAction()**
 
 
### **Sponsored Marker**

 - Badge view (an icon)
 - change according ad network
 - must be inserted on top right
 - this is automatically added to the TOP-RIGHT corner of your native ad layout.
 
### **Distinguishable Ad**

 - “Ad” (can be localized)
 - Badge that says “AD” and is at least 15x15px (can be localized)
 - change according ad network
 - must be inserted on top left
 - asset name : **ativeObject.getBadge()**

 
## Build Native Ad UI

MNGNativeObject have all required metadata to build your customized native UI. Your native ad layout should have MAdvertiseNativeContainer as it's root viewGroup container.



```java

// Get the app name
String title=nativeObject.getTitle();

// Get the app description (tagline)
String body=nativeObject.getBody();

// Get the app social context
String socialContext=nativeObject.getSocialContext()

// Get the "Ad" badge bitmap. You must show this bitmap on your ad view to denote an ad
Bitmap badge=nativeObject.getBadge();

// Check whether the app PriceType MNGPriceTypeFree,MNGPriceTypePayable or MNGPriceTypeUnknown
MNGPriceType pricetype=nativeObject.getPriceType()

// Get the app purchase price
String price=nativeObject.getPriceText();

// Get the localized text to print on the call to action button, such as "DOWNLOAD , LEARNE MORE ..."
String callToAction=nativeObject.getCallToAction();

// Register your custom ad view to automatically report impressions and clicks, and to display icon, image cover or the media video 
// This is mandatory
nativeObject.registerViewForInteraction(nativeAdContainerView,mediaViewGroup,iconImageView,nativeAdCallToActionView);

```
![2587222597-nativeAd-min-min (1).png](https://bitbucket.org/repo/GyRXRR/images/165955247-2587222597-nativeAd-min-min%20%281%29.png)


## RegisterViewForInteraction
The registerViewForInteraction method :

- Handles all the user interactions with your custom layout (clicks, impressions ...)

- Display icon, image cover or the media video 


It accepts four arguments: 

- The first is the MAdvertiseNativeContainer that should be your custom layout's root view.
- The second is the media Container, the sdk will handle the rendering process ( displaying) the image cover or the media video inside the view group that depends on the ad network result.
- The third is the image View for NativeAd's ad Icon
- The fourth is the callToAction View that handles the click event of your ad.

Note: The MAdvertiseNativeContainer is a custom ViewGroup that extends FrameLayout so you can use it as it is or you can put your layout inside of it which is the method we recommend.


## Cache

Ad metadata that you receive can be cached and re-used for up to 3 hours. If you plan to use the metadata after this time period, make a call to load a new ad.


## Customize Native Ad AdChoice

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

## Hide Icon or Image Cover
Put null to hide icon (instead of iconImageView) or image cover (instead of mediaViewGroup).

```java
@Override
    public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
   ...
//to handle impressions, user interactions and to display icon, image cover or the media video 

nativeObject.registerViewForInteraction(nativeAdContainerView,null,null,nativeAdCallToActionView);
   ...
}
```

## Customize Native Ad Badge

You can use a custom badge for the native ad.

```java
@Override
    public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
   ...
        Bitmap badge=nativeObject.getBadge(getActivity(),"String to be displayed in the badge");
   ...
}
```


## Click - registerViewForInteraction

It's **HIGHLY** recommended to only register ONE and ONLY one view for interaction , because some of the AdNetworks only accept one view and if you try to assign more than one then probably none of the views you assign will be responsive.