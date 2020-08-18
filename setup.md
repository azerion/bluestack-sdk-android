# MAdvertise CMP

This documentation will go through all the steps required to integrate MAdvertiseCMP on Android platform.


## Prerequisites

Before You Start, MAdvertiseCMP requires minimum : 

- CompileSdkVersion at least 29.
- **Android Studio 4.0 or higher**.
- Android 4.4 (API level 19) or higher (But it work only in Android 7.0 (API level 24) or higher).
- Since Version 30 and later, it's required that your project migrates from Android Support Libraries to Jetpack Libraries ([Android X]).

## Integration Guide

### Step 1: Import the MAdvertiseCMP SDK

Add the following line to your app's build.gradle, and make sure the latest SDK is used :

```java
dependencies {
implementation(name: 'madvertisecmp-X.0.0', ext: 'aar')
}
```

**You can find the file here :** [madvertisecmp-X.0.0.aar](https://bitbucket.org/mngcorp/mngads-demo-android/src/master/MngAdsDemo/app/libs/)

### Step 2: Enable support for the new language APIs of Java 1.8 

Add the following line to your app's build.gradle :

```java
android {
  defaultConfig {
    // Required when setting minSdkVersion to 20 or lower
    multiDexEnabled true
  }

  compileOptions {
    // Flag to enable support for the new language APIs
    coreLibraryDesugaringEnabled true
    // Sets Java compatibility to Java 8
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
  }
}

dependencies {
 coreLibraryDesugaring 'com.android.tools:desugar_jdk_libs:1.0.10'
}
```



### Step 3: Prepare the configuration file

**Introduction**

Through this file, you can:

- **Defining Strings :** You can edit the content of text to allow the same field to display different content based on the language of the user.

- **Customizing Appearance :** You can change global properties to alter the look and feel of the default instance interface (Functionality is not affected).


For more details on how to prepare the file, you can find it in this link : [MAdvertiseCMP - Configuration File](https://bitbucket.org/anypli/madvertisecmp-android/src/V34/cmp_configuration.md).

**Integration**

- The file should be added to your **main/res/raw** folder.

- The configuration files for the following languages are present in the [main/res/raw] of the demo:
	- German
	- Italian
	- French
	- English

- Here's an example of how you can use the configuration files depending on the language :

```java
int configRes;
switch (Locale.getDefault().getISO3Language()) {
                case "fra":
                    configRes = R.raw.madvertise_config_fr;
                    break;
                case "ita":
                    configRes = R.raw.madvertise_config_it;
                    break;
                case "deu":
                    configRes = R.raw.madvertise_config_de;
                    break;
                default:
                    configRes = R.raw.madvertise_config_en;
                    break;
 }
    

```


### Step 4: Initialize the configuration file

You have to init the configuration in your application class :

```java
ConsentToolConfiguration consentToolConfiguration = new ConsentToolConfiguration(R.raw.madvertise_config_fr);
```

You can customize appearance :

*Background :*

To change the default background of the consent tool (optional) you'll have to specify the resource id of your background, it can be either a color or a drawable, using the configuration tool method with this signature

```java
public ConsentToolConfiguration setHomeBackgroundRes(int homeBackgroundRes)
```

*Size :*

To change the default size of the consent tool (optional) you'll have to add the width and height of the desired tool using the configuration tool method with this signature

```java
public ConsentToolConfiguration setConsentToolSize(int pxWidth, int pxHeight)
```


### Step 5: Initialize the MAdvertiseCMP SDK


You have to init the SDK in your application class :

```java
ConsentManager.sharedInstance.configure(this,YOUR_APP_ID, new ConsentToolConfiguration(configRes),YOUR_PUBLISHER_CC);
```

The configure method takes the following parameters:

- the Application context.
- the App Id of your application.
- the Consent Tool Configuration object.
- the publisherCC value (corresponds to the country code (Two-letter) of the country in which the publisher's business entity is established like "FR", "DE", "IT"...).


*Integration example :*

Here's an example of how to do that in ```onCreate``` on an application subclass:

```java
public class YourApp extends Application {

  @Override  
  public void onCreate() {
    super.onCreate();
    
ConsentManager.sharedInstance.configure(this,1234567,  new ConsentToolConfiguration(configRes),"FR");
    
  }
}
```

**Enforce a specific language :**

You can enforce your preferred language for the cmp with these init :

```java
ConsentManager.sharedInstance.configure(this,YOUR_APP_ID,YOUR_PREFERRED_LANG, new ConsentToolConfiguration(configRes),YOUR_PUBLISHER_CC);
```

- the language you want to show CMP with it((Two-letter) like "fr","en","it"....) **(Optional)**

*Integration example :*

Here's an example of how to do that in ```onCreate``` on an application subclass:

```java
public class YourApp extends Application {

  @Override  
  public void onCreate() {
    super.onCreate();
    
ConsentManager.sharedInstance.configure(this,1234567, "fr", new ConsentToolConfiguration(configRes),"FR");
    
  }
}
```



## Advanced Topics

### Fullscreen Page

You can use a fullscreen page instead of a Popup, you need to the following method to your ConsentToolConfiguration :


```java
setConsentToolSize(ConsentToolConfiguration.MATCH_PARENT,ConsentToolConfiguration.MATCH_PARENT);
```


Here's an example:

```java
public class YourApp extends Application {

  @Override
  public void onCreate() {
    super.onCreate();
    ConsentManager.sharedInstance.configure(this, YOUR_APP_ID , Locale.getDefault(), 
    new ConsentToolConfiguration(R.raw.madvertise_config)
                .setConsentToolSize(ConsentToolConfiguration.MATCH_PARENT,ConsentToolConfiguration.MATCH_PARENT),"FR");
  }
}
```
___

### Check the consent tool is shown


To check whether the consent tool is shown, you can use the method : 

```java
ConsentManager.sharedInstance.isConsentToolShown()
```


Here's an example:

```java
if (!ConsentManager.sharedInstance.isConsentToolShown()){
    startActivity(new Intent(this, HomeActivity.class))
}
```

___

### Check the availability of user consent


This listener is called when the user provides his consent by clicking the accept or the save button.

```java
     ConsentManager.sharedInstance.setOnConsentProvidedListener(() -> {
            //TODO: Action that you need to do after closing the consent tool.
        });
```
---

### Check if user close CMP Popup with close button


To check if user close CMP Popup with close button, you can use the method :

```java
ConsentManager.sharedInstance.isConsentToolClosed()
```

Here's an example:

```java
if (!ConsentManager.sharedInstance.isConsentToolClosed()){
   .....
}
```


---

### Collect External Purposes IDs

**Option 1 : **

To collect external purposes IDs, you can use the method :

```java
ConsentManager.sharedInstance.getExternalPurposesIDs(context)
```

Here's an example:

```java
Log.e(TAG,ConsentManager.sharedInstance.getExternalPurposesIDs(mContext))
```

You will get something like this: : TAG: [3,4,5]

**Option 2 : **

You can get it directly through SharedPreferences with tag **IABTCF_PublisherConsent**.

---

### Manually Displayed


Once the consent manager is ready the consent tool will be shown automatically, if you want it to be manually displayed :

1) Add a listener to your consent manager **before adding your configurations**.

```java
//Before initializing the cmp
ConsentManager.sharedInstance.setConsentManagerListener(this);
```

2) This listener requires to implement an callback : 

```java
@Override
public void onShowConsentToolRequest() {
   
}

``` 

3) Now, you will be able to show the consent tool by calling showLocationConsentTool method as follows:

```java
@Override
public void onShowConsentToolRequest(Consent consentString) {
ConsentManager.sharedInstance.showLocationConsentTool();   
}
```

Here's an example:

```java

public class YourApp extends Application {

  @Override
  public void onCreate() {
    super.onCreate();
ConsentManager.sharedInstance.setConsentManagerListener(this);
ConsentManager.sharedInstance.configure(this, YOUR_APP_ID , Locale.getDefault(), 
    new ConsentToolConfiguration(R.raw.madvertise_config),"FR");
  }
}

// Callback when Consent Tool is ready to show
@Override
public void onShowConsentToolRequest() {
ConsentManager.sharedInstance.showLocationConsentTool();

// Callback when Consent Tool is closed
@Override
public void onConsentToolClosed() {

}

``` 

[Android X]:https://developer.android.com/jetpack/androidx/migrate
[main/res/raw]:https://bitbucket.org/mngcorp/madvertise-gdpr-cmp-android/src/master/MAdvertiseCmpDemo/src/main/res/raw/