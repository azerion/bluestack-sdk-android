# Interstitial Integration for Android

[TOC]

## Overview
Before You Start. Make sure that you have correctly integrated the MNG SDK into your application. Integration is outlined [here](https://bitbucket.org/mngcorp/mobile.mng-ads.com-mngperf/wiki/setup).


## Step 1. Init Interstitial factory

To create a interstitial you must init an object with type MNGAdsSDKFactory :

* **Java**

```java
MNGAdsFactory mngAdsInterstitialAdsFactory = new MNGAdsFactory(this);

```

* **Kotlin**

```java
val mngAdsInterstitialAdsFactory = MNGAdsFactory(this)

```

## Step 2. Set Placement ID

You have also to set placement Id :

* **Java**

```java
mngAdsInterstitialAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID");
```

* **Kotlin**

```java
mngAdsInterstitialAdsFactory.setPlacementId("/YOUR_APP_ID/PLACEMENT_ID")
```

## Step 3. Implement the Listener
Next, implement the Interstitial Listener in your code. 

* **Java**

```java
// set intertitial listener
mngAdsInterstitialAdsFactory.setInterstitialListener(this);
```

* **Kotlin**

```java
// set intertitial listener
mngAdsInterstitialAdsFactory.setInterstitialListener(this)
```

The SDK will notify your Listener of all possible events listed below :

- InterstitialDidLoad(): will be called by the SDK when your Interstitial is ready.

* **Java**

```java
@Override
public void interstitialDidLoad() {
Log.d(TAG, "interstitial did load");
}
```

* **Kotlin**

```java
override fun interstitialDidLoad() {
Log.d(TAG, "interstitial did load")
}
```

- interstitialDidFail(Exception adsException): will be called when all ads servers fail. it will return the error of last called ads server.

* **Java**

```java
@Override
public void interstitialDidFail(Exception adsException) {
Log.e(TAG, "interstitial did fail :" + adsException.toString());
}
```

* **Kotlin**

```java
override fun interstitialDidFail(adsException: Exception) {
Log.e(TAG, "interstitial did fail :" + adsException.toString())
}
```

- InterstitialDisappear(): will be called when interstitial was dismissed.

* **Java**

```java
@Override
public void interstitialDisappear() {
Log.d(TAG, "interstitial disappear");
}
```

* **Kotlin**

```java
override fun interstitialDisappear() {
Log.d(TAG, "interstitial disappear")
}
```

- interstitialDidShown(): will be called when interstitial was shown.

* **Java**

```java
@Override
public void interstitialDidShown() {
Log.d(TAG, "interstitial Did Shown");
}
```

* **Kotlin**

```java
override fun interstitialDidShown() {
Log.d(TAG, "interstitial Did Shown")
}
```

## Step 4. Load Interstitial Ad

### Auto Displaying

To request and display an interstitial ad, call the following method: 

* **Java**

```java
mngAdsInterstitialAdsFactory.loadInterstitial();
```

* **Kotlin**

```java
mngAdsInterstitialAdsFactory.loadInterstitial()
```

### Disable Auto Displaying

To request **without displaying** an interstitial ad, call the following method: 

* **Java**

```java
mngAdsInterstitialAdsFactory.loadInterstitial(false);

```

* **Kotlin**

```java
mngAdsInterstitialAdsFactory.loadInterstitial(false)

```

To check if the interstitial is ready to be show, you must call isInterstitialReady() and displayInterstitial() in order to display the ads (in case of success) :

* **Java**

```java
...
if (mngAdsInterstitialAdsFactory.isInterstitialReady()) {
mngAdsInterstitialAdsFactory.displayInterstitial();
} else {
Log.d(TAG, "Interstitial not ready ");
}
...
```

* **Kotlin**

```java
...
if (mngAdsInterstitialAdsFactory.isInterstitialReady()) {
mngAdsInterstitialAdsFactory.displayInterstitial()
} else {
Log.d(TAG, "Interstitial not ready")
}
...
```

**Note:**

 - To try out auto-displaying disabled on demo, you can check interstitial page. Others interstitials (background returns, overlay) run with auto-displaying.
 
- To avoid stacking up two interstitial Ad MNG added lock system :

   - MNG Ads Factory will ignore any interstitial request while there is a pending request or there is interstitial shown at that moment.

 - MNG Ads Factory will ignore any interstitial request if interstitial was just closed and there is a new interstitial request before 5s delay.


## Troubleshooting
 
### Memory managment
When you have finished your ads plant you must free the memory.

* **Java**

```java
@Override
protected void onDestroy() {
mngAdsInterstitialAdsFactory.releaseMemory();
super.onDestroy();
}
```

* **Kotlin**

```java
override fun onDestroy() {
mngAdsInterstitialAdsFactory.releaseMemory()
super.onDestroy()
}
```

### isBusy

Before making a request if you want to check that factory is not busy (Ads factory is busy means that it has not finished the previous request yet).

isBusy will be set to :

- **true :** when factory starts handling request.

- **false :** when factory finishes handling request.

**Example**:

* **Java**

```java
if (!mngAdsInterstitialAdsFactory.isBusy()) {

Log.d(TAG, "Ads Factory is not busy");
mngAdsInterstitialAdsFactory.loadInterstitial(false);
} else {
Log.d(TAG, "Ads Factory is busy");
}
```

* **Kotlin**

```java
if (!mngAdsInterstitialAdsFactory.isBusy()) {
Log.d(TAG, "Ads Factory is not busy")
mngAdsInterstitialAdsFactory.loadInterstitial(false)
} else {
Log.d(TAG, "Ads Factory is busy")
}
```

### Ad click listener
You can then implement MNG AdListener callback to detect when an Ad is clicked

* **Java**

```java
// set click listener
mngAdsInterstitialAdsFactory.setClickListener(this);

...
@Override
public void onAdClicked() {
Log.d(TAG, "Ad Clicked");
}
...
```

* **Kotlin**

```java
// set click listener
mngAdsInterstitialAdsFactory.setClickListener(this)

...
override fun onAdClicked() {
Log.d(TAG, "Ad Clicked")
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

* **Java**

```java

Location  myLocation = new Location("I");
myLocation.setLatitude(35.757866);
myLocation.setLongitude(10.810547);

MNGPreference mngPreference = new MNGPreference();
mngPreference.setLocation(location,CONSENT_FLAG,context);
mngPreference.setAge(28);
mngPreference.setGender(MNGGender.MNGGenderFemale);
mngPreference.setKeyword("brand=myBrand;category=sport");
mngPreference.setContentUrl("put your content url here")


mngAdsInterstitialAdsFactory.loadInterstitial(mngPreference,false);

```

* **Kotlin**

```java

val myLocation = Location("I")
myLocation.setLatitude(35.757866)
myLocation.setLongitude(10.810547)

val mngPreference = MNGPreference()
mngPreference.setLocation(location,CONSENT_FLAG,context)
mngPreference.setAge(28)
mngPreference.setGender(MNGGender.MNGGenderFemale)
mngPreference.setKeyword("brand=myBrand;category=sport")
mngPreference.setContentUrl("put your content url here")


mngAdsInterstitialAdsFactory.loadInterstitial(mngPreference,false)

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
|MAdvertiseLockedPlacementException|LOCKED_PLACEMENT_ERROR = 4   |   This placement is locked by an other factory | An other factory has loaded an interstitial using this placement, and its no yet displayed     |
|MAdvertiseBusyFactoryException|BUSY_FACTORY_ERROR = 5   |    Your factory is busy| Your factory is busy by an other request at the moment     |
|MAdvertiseNoAdException|NO_AD_ERROR = 7   |    No Ad found | Therese no ad to dilver at the moment     |
|MAdvertiseInterstitialCoolDownException|INTERSTITIAL_COOLDOWN_ERROR = 8   |   Time between last interstitalDisappear and loadInterstital Must be more than 5s |We have defined a minimum time between interstitalDisappear and loadInterstital, this interval is set to 5 second       |
|MAdvertiseAlreadyShownInterstitialException|INTERSTITIAL_ALREADY_SHOWN_ERROR = 9   |   Other Interstitial is shown | We tolerate only one interstitial to be shown at time   |
|MAdvertiseTimeOutException|TIME_OUT_ERROR = 10   |  no ad to deliver before time out | Therese no ad to deliver before the specified time out  |


**Handle Exception :**
If you want to check which exception was invoked, in the didFail callback you have to cast the exception to MAdvertiseException and then use getErrorCode() to get exception code.
Also you can get exception message by calling getMessage().
In the example below we use interstitialDidFail, even you can use this logic in all our didFail callBack(bannerDidFail, infeedDidFail,nativeAdCollectionDidFail and nativeObjectDidFail)

* **Java**

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

* **Kotlin**

```java
override fun interstitialDidFail(e: Exception) {

val adException: MAdvertiseException = e as MAdvertiseException

when (adException.errorCode){
MAdvertiseException.BUSY_FACTORY_ERROR -> {...}
MAdvertiseException.INTERSTITIAL_ALREADY_SHOWN_ERROR -> {...}
.
.
.

}
Log.e(TAG, "Interstitial did fail : ${adException.message} error code: ${adException.errorCode}")
}
```

## Show Interstitial after return from background

Unlike iOS with applicationdidenterbackgroundwith, on Android we don’t have the option to directly detect whether the app is in  background. But There are few workarounds. 

   - If your application has only one activity , you can make interstitial request from the [onStart()] method .This will enable you to make a request when the app starts and every time the app goes through [onStop()] method. Even though the [onStart()] method will be called after an interstitial is closed the create intertitial will be ignored due to the 5s delay lock.

   - If your application has more than one activity then you have to handle things differently. The solution used in mngads demo depends on tracking every [onStart()] and [onStop()] of the application by the singleton (ApplicationManager). The key of the solution is the understanding that if we have Activity_1 and Activity_2, and we call Activity_2 from Activity_1, then Activity_2's [onStart()] will be called before Activity_1 [onStop()]. You must use a BaseActivity to override [onStart()]and [onStop()] or you can use [ActivityLifecycleCallbacks] API 14 , in order to increment/decrement a variable used for counting.

* **Java**

```
#!java

public class BaseActivity extends AppCompatActivity implements ApplicationManager.ForegroundListener, MNGInterstitialListener, MNGAdsSDKFactoryListener, MNGClickListener {

    private ApplicationManager applicationManager;
    private MNGAdsFactory mngAdsInterstitialFactory;
    private MNGPreference mngPreference;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        TAG = getClass().getSimpleName();

        applicationManager = ApplicationManager.getInstance();

        initializeMNGFactory();

    }
....


 @Override
    protected void onStart() {

        Log.d(TAG, "onStart");

        super.onStart();

        applicationManager.onActivityStarted(this, this);
    }

    @Override
    protected void onStop() {

        Log.d(TAG, "onStop");

        applicationManager.onActivityStopped(this, this);

        super.onStop();

    }

....
```

* **Kotlin**

```
#!kotlin

class BaseActivity: AppCompatActivity(), ApplicationManager.ForegroundListener, MNGInterstitialListener, MNGAdsSDKFactoryListener, MNGClickListener {

	private val TAG = BaseActivity::class.java.simpleName
    private lateinit var applicationManager: ApplicationManager
    private lateinit var mngAdsInterstitialFactory: MNGAdsFactory
    private lateinit var mngPreference: MNGPreference


    protected override fun onCreate(savedInstanceState: Bundle) {
        super.onCreate(savedInstanceState)
        applicationManager = ApplicationManager.getInstance()

        initializeMNGFactory()

    }
....


    protected override fun onStart() {
        super.onStart()
        Log.d(TAG, "onStart")
        applicationManager.onActivityStarted(this, this)
    }

    
    protected override fun onStop() {
        Log.d(TAG, "onStop")
        applicationManager.onActivityStopped(this, this)
        super.onStop()
    }

....
```

  With this Solution, you will end up with two cases when applicationManager.onActivityStopped(activity,forgroundListener) is called:
*  stateCounter > 0 : There is a transition between activities .
*  stateCounter = 0 : There is a transition to background.  
    *  Now we can change the variable to wasInBackground to true and call onBecameBackground Listener (There is no need to this listener for mngads but to follow the app state for debuging ) 
    *  Since the app is in Background in this case the next [onStart()] the will  be back to foreground.
    *  There other cases we have to take into account for example : orientation change. During orientation change, [onStop()] of the old instance of the activity is called before [onStart()] of the new instance. For this onActivityStopped accepts activity as a first parameter to ignore this case by checking [isChangingConfigurations()]

Even though the onBecameForeground listener will be called after an interstitial is closed the create interstitial will be ignored due to the 5s delay lock.
    
>Note : This workaround covers most of the scenarios but you need to handle more specific cases in your application.

* **Java**

```
#!java
package com.example.mngadsdemo.utils;

import android.app.Activity;
import android.util.Log;

public class ApplicationManager {

    public static final String TAG = ApplicationManager.class.getSimpleName();

    public interface ForegroundListener {

        public void onBecameForeground();

        public void onBecameBackground();

    }

    private static ApplicationManager instance;
    private int stateCounter;
    private boolean wasInBackground;


    public static ApplicationManager getInstance() {
        if (instance == null) {
            instance = new ApplicationManager();
        }
        return instance;
    }


    public boolean isForeground() {
        return !isBackground();
    }

    public boolean isBackground() {
        return stateCounter == 0;
    }


    public void onActivityStarted(Activity activity, ForegroundListener listener) {

        stateCounter++;

        if (wasInBackground) {

            wasInBackground = false;

            Log.i(TAG, "went foreground");

            try {

                listener.onBecameForeground();

            } catch (Exception ex) {

                Log.e(TAG, "Listener threw exception!", ex);
            }

        } else {

            Log.d(TAG, "still foreground");

        }
    }

    public void onActivityStopped(Activity activity, ForegroundListener listener) {

        stateCounter--;

        if (!activity.isChangingConfigurations()) {

            if (isBackground()) {

                wasInBackground = true;

                Log.i(TAG, "went background");

                try {

                    listener.onBecameBackground();

                } catch (Exception ex) {

                    Log.e(TAG, "Listener threw exception!", ex);
                }
            } else {

                Log.d(TAG, "still foreground");

            }

        } else {

            Log.d(TAG, "isChangingConfigurations");

        }
    }

}


```

* **Kotlin**

```
#!kotlin
package com.example.mngadsdemo.utils

import android.app.Activity
import android.util.Log

class ApplicationManager {

    val TAG = ApplicationManager::class.java.simpleName

    interface ForegroundListener {

        fun onBecameForeground()

        fun onBecameBackground()

    }

    private var instance: ApplicationManager? = null
    private var stateCounter: Int = 0
    private var wasInBackground = true

  companion object {
    fun getInstance(): ApplicationManager {
        if (instance == null) {
            instance = ApplicationManager()
        }
        return instance
    }
   }


    fun isForeground(): Boolean {
        return !isBackground()
    }

    fun isBackground(): Boolean {
        return stateCounter == 0
    }


   fun onActivityStarted(activity: Activity, listener: ForegroundListener) {

        stateCounter++

        if (wasInBackground) {

            wasInBackground = false

            Log.i(TAG, "went foreground")

            try {

                listener.onBecameForeground()

            } catch (ex: Exception) {
                Log.e(TAG, "Listener threw exception!", ex)
            }

        } else {
            Log.d(TAG, "still foreground")
        }
    }

    fun onActivityStopped(activity: Activity, listener: ForegroundListener) {

        stateCounter--

        if (!activity.isChangingConfigurations()) {

            if (isBackground()) {

                wasInBackground = true

                Log.i(TAG, "went background")

                try {

                    listener.onBecameBackground()

                } catch (ex: Exception) {

                    Log.e(TAG, "Listener threw exception!", ex)
                }
            } else {
                Log.d(TAG, "still foreground")
            }

        } else {
            Log.d(TAG, "isChangingConfigurations")
        }
    }

}


```

You can see our demo app with following files

- [ApplicationManager.kt]
- [BaseActivity.kt]

# Example

 - https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/fragment/InterstitialFragment.kt
 - https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/SplashActivity.kt




[onStart()]:http://developer.android.com/reference/android/app/Activity.html
[onStop()]:http://developer.android.com/reference/android/app/Activity.html
[ActivityLifecycleCallbacks]:http://developer.android.com/reference/android/app/Application.ActivityLifecycleCallbacks.html
[isChangingConfigurations()]:http://developer.android.com/reference/android/app/Activity.html#isChangingConfigurations()
[AdsFragment.kt]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.kt?at=master
[omsdk-x.x.x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[link]:https://developer.android.com/training/location/retrieve-current.html
[SmartAdServer]:http://documentation.smartadserver.com/displaySDK
[Appsfire]:http://docs.appsfire.com/sdk/android/integration-reference/Introduction
[Google DFP]:https://developers.google.com/mobile-ads-sdk/download#download
[Facebook Audience Network]:https://developers.facebook.com/docs/android?locale=fr_FR
[mngads-sdk-x.aar Android SDK]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[MngAds sample app]:https://bitbucket.org/mngcorp/mngads-demo-android/src
[Help Center]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq
[Change Log]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/change-log
[Upgrade Guide]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/upgrading
[AudienceNetwork.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsRequiredJars/AudienceNetwork.jar?at=master&fileviewer=file-view-default
[Android-support-v4.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/android-support-v4.jar?at=master
[Google-play-services_lib]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/google-play-services_lib/?at=master
[mngAds state diagram]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/diagram
[Amazon]:https://developer.amazon.com/public/resources/development-tools/sdk
[Amazon.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[DTBAndroidSDK-x.x.x.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Flurry]:https://developer.yahoo.com/flurry/
[FlurryAds.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[FlurryAnalytics.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Best practice Mngads and Design ad units to fit your app]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/guidelines
[AndroidMultidex]:http://developer.android.com/intl/ko/tools/building/multidex.html
[Ogury]:http://www.ogury.co/
[ogury-x.x.x.jar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[Native Ads guidelines]:./nativead
[ApplicationManager.kt]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/utils/ApplicationManager.kt?at=master&fileviewer=file-view-default
[BaseActivity.kt]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/src/main/java/com/example/mngadsdemo/BaseActivity.kt?at=master&fileviewer=file-view-default
[Interstitial Guideline]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/interstitial-guideline
[see Proguard rules on our faq]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-if-your-app-uses-proguard-you-must-edit-your-proguard-settings-to-avoid-stripping-google-play-out-of-your-app
[more details about instance on our FAQ]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/faq#markdown-header-interstitial-did-load-callback-without-display
[umooveVx.aar]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/libs/?at=master
[build.gradle]:https://bitbucket.org/mngcorp/mngads-demo-android/src/HEAD/MngAdsDemo/app/build.gradle?at=master&fileviewer=file-view-default
[Mopub Marketplace]:https://www.mopub.com/
[AdColony]:https://www.adcolony.com/