# Native ads
[TOC]

MNG supports native ads, that allow you to retrieve the metadata of ad campaigns and present the ads yourself, within the context of your app, using your own art style. You are fully responsible
for rendering the ad views using the information we supply. Native ads however offer methods to help you register impressions and clicks on your custom view.

## Requesting a native ad

##### Init factory

To create a nativeAd  you have to init an object with type MNGAdsSDKFactory and set the nativeListener.

```
#!java
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

```
#!java
  mngAdsNativeAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```
##### Make a request for native ad
To make a request you have to call 'createNative()'. this method return a bool value (canHandleRequest) 

```
#!java
    if(mngAdsNativeAdsFactory.createNative()){
        //Wait callBack from native listener
    }else{
        //adsFactory can not handle your request
    }
```
##### Handle callBack from NativeListener
adsAdapter.nativeObjectDidLoad(): will be called by the SDK when your nativeObject is ready. now you can create your own view.
```
#!java
@Override
	public void nativeObjectDidLoad(MNGNativeObject nativeObject) {
		Log.d(TAG, "native Object did load ");
	}

```

adsAdapter.nativeObjectDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.
```
#!java
@Override
	public void nativeObjectDidFail(Exception adsException) {
		Log.e(TAG, "nativeObject Did Fail :" + adsException.toString());
	}

```

## Native Ad Assets

Once a native ad is loaded, you may retrieve its metadata with the following methods:


```
#!java

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
 String iconUrl=nativeObject.getAdIconUrl();

// Get ahe URL of the cover image for the app
 String coverImageUrl=nativeObject.getAdCoverImageUrl();

// Register your custom ad view to automatically report impressions and clicks, and react to clicks by opening the app in the store. This is mandatory
public void registerViewForInteraction (View monitoredView);
```
## Native Ad Implementation
![img_native_new.png](https://bitbucket.org/repo/GyRXRR/images/1198580967-img_native_new.png)


## Video (>= v2.0)
You can also integrate video ads into your Native Ad experience. To enable video you must complete the following steps:
 - Have SDK version 2.0 or later
 -  You have to call setMediaContainer(viewGroup) then the sdk will handle the rendering process ( displaying)  the image cover or the media video inside the view group that depends on the ad network result

```
#!java
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
    
    //to handle impression and user interaction you have to call 
    nativeObject.registerViewForInteraction(nativeAdCallToActionView);
   ...
}
```
![MNGNativeVideoAd2.png](https://bitbucket.org/repo/GyRXRR/images/1851406635-MNGNativeVideoAd2.png)


## registerViewForInteraction  (>=v2.5)

To avoid case where native DFP adapter fails to register view for interaction , MNG ads limits the type of view passed to **registerViewForInteraction** method (it only accept Button , TextView , ImageView). 

>Note : If you want the whole native ad clickable you can use a transparent button above the native content as a workaround .
