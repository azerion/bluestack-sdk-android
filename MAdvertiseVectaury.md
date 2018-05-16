# MAdvertiseVectaury


## Installation
Add this dependency to your build.gradle file 

```groovy
    implementation 'io.vectaury.android:sdk:1.2.0'
```

You will also need to add this maven repository

```groovy
	maven {
        url "https://nexus.vectaury.io/repository/sdk/"
    }
```

Vectaury will need to use your device's location, so you may need to ask for the location permission in your app. Also you need to make sure to add their Settings.bundle after the installation is complete https://cdn.vectaury.io/sdk/doc/android/integration/)
That's it, you're all set.