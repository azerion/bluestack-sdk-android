# Retency SDK

[TOC]

This documentation will go through all the steps required to integrate Retency SDK on Android platform.


## Prerequisites

Before You Start, Retency requires minimum : 

- CompileSdkVersion at least 29.
- Android Studio 4.0 or higher.
- Android 4.4 (API level 19).
- Since Version 2.0 and later, it's required that your project migrates from Android Support Libraries to Jetpack Libraries ([Android X]).

## Integration Guide

### Step 1: Import the Retency SDK

In the main build.gradle of your project, you must declare the mAdvertise repository: 


```groovy

allprojects {
	repositories {
		google()
		jcenter()
		

    maven 
    {
     credentials 
        {
         username "madvertise-maven"
         password "GpdGZ9GE9SK7ByWdM987"
        } 
     url "https://api.bitbucket.org/2.0/repositories/mngcorp/deploy-maven-bluestack/src/master"
     authentication 
     	{
        basic(BasicAuthentication)
    	}
     }
	}
}
```

In the build.gradle of to your application module, you can now import the Retency SDK by declaring it in the dependencies section:

```groovy
implementation 'com.retency:sdk:2.0.0'
```

### Step 2: Initialize the Retency SDK


You have to init the SDK in your application class :

```java
mRetencySDK = new RetencySDK(Context);
```

The init method takes a reference to any kind of Context

### Step 3: Set Publisher Id 

You have to set the Publisher Id :

```java
mRetencySDK.setPublisherId(RetencyApiKey);
```
If you do not have one yet, you can refer to the madvertise team.

### Step 4: Run Retency SDK

To start Retency SDK , call this method:

```java
mRetencySDK.call();
```


## Troubleshooting

### Enabling debug mode
To enbale debug mode you need to set debug mode to true :

```java
...
mRetencySDK.setDebug(true);
...

```

[Android X]:https://developer.android.com/jetpack/androidx/migrate