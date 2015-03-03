# MngAds FAQ #

This document answers the following frequently asked questions:

[TOC]
# Implementation #
## If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. 

If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. Edit your project’s proguard-project.txt file to add the following:


```
#!android

-keep class * extends java.util.ListResourceBundle {
    protected Object[][] getContents();
}
 
-keep public class com.google.android.gms.common.internal.safeparcel.SafeParcelable {
    public static final *** NULL;
}
 
-keepnames @com.google.android.gms.common.annotation.KeepName class *
-keepclassmembernames class * {
    @com.google.android.gms.common.annotation.KeepName *;
}
 
-keepnames class * implements android.os.Parcelable {
    public static final ** CREATOR;
}
-keepclassmembers class com.smartadserver.android.library.** {
@android.webkit.JavascriptInterface <methods>;
}
-keep class com.facebook.** { *; }
-keepattributes Signature
```

## What types of ad units are available? ##
There are three ad units available to use in your app:

 - Standard banner ads
 - Interstitial ads
 - Native ad API

## How many placement IDs should I create? ##
You need to create a different placement ID for any of the different ad formats (banner, interstitial and native) and each unique path that you implement within your app. 
If you use native ads in feed and plan to show several units as the user scrolls, then you should use the same placement ID for all the native ad units.
## What are "Native Ads ##
Native ads allow you to customize the look and feel of ads to match that of your app. Native ads work by receiving the metadata for ads through MngAds.



# Publisher Application Process #
# Support #