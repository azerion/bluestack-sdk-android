Change log and release notes for MadvertiseLocation for Android.

### Version 2.3
#### Release date: June 25th, 2019

 - Add stop method
 - Date optimzation
 - Add debug logs
 - GDPR consentement optimization
 - number of POI optimization

If you are using madvertiseLocation standalone without the mngads SDK, you must change implementation

replace


```
#!java

@Override
private void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
	
	MadvertiseLocation madvertiseLocation = new MadvertiseLocationBuilder(getApplicationContext())
                .appId(APP_ID)
                .build();

   MadvertiseLocation.with(madvertiseLocation);
}
```

by


```
#!java
MadvertiseLocation.configure(getApplicationContext(), APP_ID).start();

```



### Version 2.2
#### Release date: April 10th, 2019

 - Manage MadvertiseConsent_ConsentString (specific purposes for GPS data) from CMP that replace IABConsent_LocationPurpose
 - Allow debug Mode

### Version 2.1
#### Release date: February 8th, 2019

 - Manage IABConsent_LocationPurpose from CMP

### Version 2.0
#### Release date: January 14th, 2019

 - Optimization accuracy
 - Restart service on android 8/9

### Version 1.1
#### Release date: December 12th, 2018

 - fix issue on android 8

### Version 1.0
#### Release date: October 24th, 2018

 - initial release