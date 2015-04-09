# upgrading SDK

## Upgrading to 1.2.5

You must add **AppNexus-sdk** 

## Upgrading from 1.1 to 1.2

New method for carousel can be used, see [Ad Examples]

To make a request you have to call 'createNativeCollection(int requestedAdNumber)'. this method return a bool value (canHandleRequest) 

```
#!java
if(mngAdsNativeAdsFactory.createNativeCollection(int requestedAdNumber){
//Wait callBack from native listener
}else{
//adsFactory can not handle your request
}
```

## Upgrading from 1.0 to 1.1

No special steps are required to upgrade to v1.1.



[Ad Examples]:https://bitbucket.org/mngcorp/mngads-demo-android/wiki/inspiration