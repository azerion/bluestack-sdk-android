# Best practice Mngads : optimized use case for several ad formats on one page

When trying to display several ad formats on one page try to synchronize your requests instead of making multiple ones at the some time. By making the requests at the same time you are decreasing your chance of receving an Ad and you are making your app slow .You can check the number of MNGAdsFactory running a request by calling :  

```
#!java

    int mNumberOfRunningFactory=MNGAdsFactory.getNumberOfRunningFactory() ;
...

You can see an example on [AdsFragment.java].


[AdsFragment.java]:https://bitbucket.org/anypli/mng-ads-demo-android/src/HEAD/MngAdsDemo/src/com/example/mngadsdemo/fragment/AdsFragment.java?at=master