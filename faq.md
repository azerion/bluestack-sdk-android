# MngAds FAQ #

This document answers the following frequently asked questions:

[TOC]
# Implementation #
## If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. 

If your app uses Proguard, you must edit your Proguard settings to avoid stripping Google Play out of your app. Edit your project’s proguard-project.txt file to add the following:


```
#!android

//mngads
-keep class com.mngads.** { *; }
-keep class com.retency.** { *; }
-keep class com.flurry.** { *; }
-keep class com.google.android.gms.** { *;}
-keep class com.facebook.** { *; }
-keep class com.smartadserver.** { *; }
-keep class com.liverail.** { *; }
-keep class com.amazon.** { *; }
-keep class io.presage.** { *; }

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
-keep class com.flurry.** { *; }

//Flurry
-dontwarn com.flurry.**
-keepattributes *Annotation*,EnclosingMethod,Signature
-keepclasseswithmembers class * {
    public <init>(android.content.Context, android.util.AttributeSet, int);
}

# Google Play Services library
-keep class * extends java.util.ListResourceBundle {
    protected Object[][] getContents();
}

#If you are using the Google Mobile Ads SDK, add the following:
# Preserve GMS ads classes
-keep class com.google.android.gms.** { *;
}
-dontwarn com.google.android.gms.**

//liverail
 # Third party adapters (e.g. AdColony, GoogleIMA) are initialized using reflection
  -keep class com.liverail.adapters.** {*;}

//Ogury
Pro Tips
Use Proguard
If you use Proguard, you need to add these lines in your configuration

-keep class sun.misc.Unsafe { *; }

-keep class shared_presage.** { *; }
-keep class io.presage.** { *; }
-keepclassmembers class io.presage.** {
 *;
}

-keepattributes *Annotation*
-keepattributes JavascriptInterface
-keepclassmembers class * {
    @android.webkit.JavascriptInterface <methods>;
}

-keepclassmembers class * implements java.io.Serializable {
    static final long serialVersionUID;
    private static final java.io.ObjectStreamField[] serialPersistentFields;
    private void writeObject(java.io.ObjectOutputStream);
    private void readObject(java.io.ObjectInputStream);
    java.lang.Object writeReplace();
    java.lang.Object readResolve();
}
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