# Interstitial Guideline

To avoid stacking up two interstitial Ad MNG added lock system :

   - MNG Ads Factory will ignore any interstitial request while there is a pending request or there is interstitial shown at that moment.

 - MNG Ads Factory will ignore any interstitial request if interstitial was just closed and there is a new interstitial request before 5s delay.

## Show Interstitial after return from background

Unlike iOS with applicationdidenterbackgroundwith, on Android we don’t have the option to directly detect whether the app is in  background. But There are few workarounds. 

   - If your application has only one activity , you can make interstitial request from the [onStart()] method .This will enable you to make a request when the app starts and every time the app goes through [onStop()] method. Even though the [onStart()] method will be called after an interstitial is closed the create intertitial will be ignored due to the 5s delay lock.

   - If your application has more than one activity then you have to handle things differently. The solution used in mngads demo depends on tracking every [onStart()] and [onStop()] of the application by the singleton (ApplicationManager). The key of the solution is the understanding that if we have Activity_1 and Activity_2, and we call Activity_2 from Activity_1, then Activity_2's [onStart()] will be called before Activity_1 [onStop()]. You must use a BaseActivity to override [onStart()]and [onStop()] or you can use [ActivityLifecycleCallbacks] API 14 , in order to increment/decrement a variable used for counting.

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
  With this Solution, you will end up with two cases when applicationManager.onActivityStopped(activity,forgroundListener) is called:
*  stateCounter > 0 : There is a transition between activities .
*  stateCounter ==0 : There is a transition to background.  
    *  Now we can change the variable to wasInBackground to true and call onBecameBackground Listener (There is no need to this listener for mngads but to follow the app state for debuging ) 
    *  Since the app is in Background in this case the next [onStart()] the will  be back to foreground.
    *  There other cases we have to take into account for example : orientation change. During orientation change, [onStop()] of the old instance of the activity is called before [onStart()] of the new instance. For this onActivityStopped accepts activity as a first parameter to ignore this case by checking [isChangingConfigurations()]

Even though the onBecameForeground listener will be called after an interstitial is closed the create interstitial will be ignored due to the 5s delay lock.
    
>Note : This workaround covers most of the scenarios but you need to handle more specific cases in your application.


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
   
   


[onStart()]:http://developer.android.com/reference/android/app/Activity.html
[onStop()]:http://developer.android.com/reference/android/app/Activity.html
[ActivityLifecycleCallbacks]:http://developer.android.com/reference/android/app/Application.ActivityLifecycleCallbacks.html
[isChangingConfigurations()]:http://developer.android.com/reference/android/app/Activity.html#isChangingConfigurations()
