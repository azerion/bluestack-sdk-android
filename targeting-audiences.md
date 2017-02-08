# Targeting Audiences

In order to take advantage of our targeting campaign, you must use our **Preferences object**.


```
#!java
mngPreference = new MNGPreference();
```



## Location Targeting

**The Madvertise adserver and certain ad can use your user’s location to send more targeted ads by passing Latitude and Longitude.**


```
#!java

    /**
     * get user location
     *
     * @param context
     * @return
     */
    public static Location getCurrentLocation(Context context) {
        Location mostRecentLocation = null;
        LocationManager mLocationManager = (LocationManager) context.getSystemService(Context.LOCATION_SERVICE);
        Criteria criteria = new Criteria();
        criteria.setAccuracy(Criteria.ACCURACY_FINE);
        String provider = mLocationManager.getBestProvider(criteria, true);
        if (provider != null) {
            if (ActivityCompat.checkSelfPermission(context, Manifest.permission.ACCESS_FINE_LOCATION) == PackageManager.PERMISSION_GRANTED && ActivityCompat.checkSelfPermission(context, Manifest.permission.ACCESS_COARSE_LOCATION) == PackageManager.PERMISSION_GRANTED) {
                mostRecentLocation = mLocationManager.getLastKnownLocation(provider);
            }
        }
        return mostRecentLocation;

    }
 Location location = Utils.getCurrentLocation(context);
 if (location != null) {
            mngPreference.setLocation(location);
        }
```

>this link can help you to get [device location].


## Keyword Targeting

Keywords allow you to target certain ad requests with user data. Keywords are useless for targeting, if you can provide **dynamic values** per users/devices.

To add keyword targeting, you will need to pass these keywords up through the application (They should be formatted as key/value pairs) :

```
#!java

mngPreference.setKeyword("page=football;category=sport");//Separator in case of multiple entries is ; key=value
```

Target campaigns using the keyword targeting function on Madvertise Console by Madvertise Team.

We can use Positive or Negative targeting

![screenshot-console.mng-ads.com 2017-02-08 14-17-47.png](https://bitbucket.org/repo/aen579/images/3770499640-screenshot-console.mng-ads.com%202017-02-08%2014-17-47.png)


## User demographic Targeting

When people are signed in on your app, can you please share **Demographic informations**  from their settings with following code :

```
#!java
mngPreference.setAge(25);//int
mngPreference.setGender(MNGGender.MNGGenderFemale); //MNGGender.MNGGenderMale

```
Target campaigns with following rules can be apply by Madvertise Team.

 - Age. Target ads to people within an age range.
 - Gender. Target ads to women, men or both.


## Madvertise Audience Targeting

Audiences can be defined by date of birth, gender, locations, Apple's Advertising Identifier (IDFA), Android's advertising ID or by a combination of rules used to identify users who took specific actions on your app (device, carrier, ...).



[device location]:https://developer.android.com/training/location/retrieve-current.html