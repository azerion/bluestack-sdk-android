# Native ads

MNG supports native ads, that allow you to retrieve the metadata of ad campaigns and present the ads yourself, within the context of your app, using your own art style. You are fully responsible
for rendering the ad views using the information we supply. Native ads however offer methods to help you register impressions and clicks on your custom view.

##1. Requesting a native ad

MNGNativeAd mNativeAd;

...

mNativeAd = new MNGNativeAd (this, "my_publisher_id");

Please check with MNG in order to receive the publisher ID for your native ads.


##2. Listening for native ad events

You can set a listener on the newly created MNGNativeAd in order to know when the ad is loaded or if an error occurred:

```
#!java


mNative.setNativeAdListener(new MNGNativeAdListener() {
   @Override
   public void onAdLoaded(MNGNativeAd mngNativeAd) {
      // Native ad metadata loaded..
   }

   @Override
   public void onError(MNGNativeAd mngNativeAd, Exception e) {
      // Error loading native ad..
   }
};
```


You may also poll for ad readiness using mNativeAd.isAdLoaded();

##3. Retrieving the ad metadata

Once a native ad is loaded, you may retrieve its metadata with the following methods:


```
#!java

// Get the app name
public String getTitle();

// Get the app description (tagline)
public String getDescription();

// Get the app category
public String getCategory();

// Get the "Ad" badge bitmap. You must show this bitmap on your ad view to denote an ad
public Bitmap getBadge();

// Check whether the app is free (true) or to be purchased (false)
public boolean isFree();

// Get the app purchase price, if the app isn't free
public String getPrice ();

// Get the localized text to print on the call to action button, such as "DOWNLOAD"
public String getCallToActionButtonText ();

// Get the URL of the icon image for the app
public String getIconURL();

// Get an array of screenshot URLs for the app
public String[] getScreenshotURLs();

// Get the number of users that supplied a rating for the app
public int getUserRatingCount();

// Get the average rating for the app, from 0.0 to 5.0 stars
public double getAverageUserRating();

// Register your custom ad view to automatically report impressions and clicks, and react to clicks by opening the app in the store. This is mandatory
public void registerViewForInteraction (View monitoredView);
```


## Conclusion

Please check your native ads implementation with MNG before releasing your app using the ads to the store, so we can make sure that all elements are present, and that impressions and clicks
are correctly reporting.