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
You have also to set placementId (minimum one time)

```java
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
##### Make a request for native ad
To make a request you have to call 'createNative()'. this method return a bool value (canHandleRequest) 

```java
    if(mngAdsNativeAdsFactory.createNative()){
        //Wait callBack from native listener
    }else{
        //adsFactory can not handle your request
    }
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

###**Main Image**

 - 1200x627px image, 
 - Wide aspect ratio main image.
 - asset name : **nativeObject.getAdCoverImageUrl()**
 
 
###**Icon Image**

 - 128x128 max
 - asset name : **nativeObject.getAdIconUrl()**
 
 
###**Ad Title**

 - 50 maximum character length string of ad headline
 - Provide enough space to display the entire length of the Ad Title
 - asset name : **nativeObject.getTitle()**
 
 
###**Ad Text**

 - 150 maximum character length string of ad text
 - Provide enough space to display the entire length of the Ad Text
 - asset name : **nativeObject.getBody()**
 
###**CTA Text**

 - Text for a button
 - 12 characters maximum
 - asset name : **nativeObject.getCallToAction()**
 
 
###**Sponsored Marker**

 - Badge view (an icon)
 - change according ad network
 - must be inserted on top right
 - this is automatically added to the TOP-RIGHT corner of your native ad layout.
 
###**Distinguishable Ad**

 - “Ad” (can be localized)
 - Badge that says “AD” and is at least 15x15px (can be localized)
 - change according ad network
 - must be inserted on top left
 - asset name : **ativeObject.getBadge()**


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

// Get the URL of the icon image for the app
// FYI this method return NO_URL_FOUND = "http://" if no cover image found
 String iconUrl=nativeObject.getAdIconUrl();

// Get ahe URL of the cover image for the app
// FYI this method return NO_URL_FOUND = "http://" if no cover image found
 String coverImageUrl=nativeObject.getAdCoverImageUrl();


// Register your custom ad view to automatically report impressions and clicks, and react to clicks by opening the app in the store. This is mandatory
public void registerViewForInteraction (MAdvertiseNativeContainer rootView, View monitoredView);
```
## Native Ad Implementation

![nativeAd-min.png](https://bitbucket.org/repo/GyRXRR/images/2587222597-nativeAd-min.png)


## Video
You can also integrate video ads into your Native Ad experience. To enable video you must complete the following steps:
 - Have the latest SDK version
 - You have to call setMediaContainer(viewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result

```java
@Override
  public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
    ...
    String title=nativeObject.getTitle();
    String body=nativeObject.getBody();
    String callToAction=nativeObject.getCallToAction();
    String price=nativeObject.getPriceText();
    Bitmap badge=nativeObject.getBadge();
    
    String iconUrl=nativeObject.getAdIconUrl();
   // String coverImageUrl=nativeObject.getAdCoverImageUrl();
   //  there is no need to use coverurl
   nativeObject.setMediaContainer(mediaViewGroup);
   
    //to handle impressions and user interactions you have to register your MAdvertiseNativeContainer as your root layout container and your callToActionView view to handle the clicks as following
nativeObject.registerViewForInteraction(nativeAdContainerView, nativeAdCallToActionView);
   ...
}
```
![MNGNativeVideoAd2.png](https://bitbucket.org/repo/GyRXRR/images/1851406635-MNGNativeVideoAd2.png)


## registerViewForInteraction
The registerViewForInteraction method handles all the user interactions with your custom layout (clicks, impressions ...), it accepts two arguments: 
The first is the MAdvertiseNativeContainer that should be your custom layout's root view.
The second is the callToAction View that handles the click event of your ad.

Note: The MAdvertiseNativeContainer is a custom ViewGroup that extends FrameLayout so you can use it as it is or you can put your layout inside of it which is the method we recommend.


## cache

Ad metadata that you receive can be cached and re-used for up to 3 hours. If you plan to use the metadata after this time period, make a call to load a new ad.


## Assets download

We provide method to download assets.
```java
@Override
  public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
    ...
   
    ImageView nativeAdIcon = (ImageView) adView.findViewById(R.id.nativeAdIcon);
    //this will download and display icon
    nativeObject.downloadAssetsForType(MAdvertiseAssetsType.MAdvertiseAssetsIcon,nativeAdIcon);

    ImageView nativeAdCover = (ImageView) adView.findViewById(R.id.nativeAdCover);
    //this will download and display cover image
    nativeObject.downloadAssetsForType(MAdvertiseAssetsType.MAdvertiseAssetsCover,nativeAdCover);

   ...
}
```
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


## click - registerViewForInteraction

It's **HIGHLY** recommended to only register ONE and ONLY one view for interaction , because some of the AdNetworks only accept one view and if you try to assign more than one then probably none of the views you assign will be responsive.