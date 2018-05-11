# GDPR

The GDPR (General Data Protection Regulation) is a set of rules within the EU law that regulates the use and process of the consumer's personal data.
The new General Data Protection Regulation law will apply in Europe starting 25th May 2018. It will provide the custumers with more protection over their personal informations by making companies more responsable about the way they interact them.

MAdvertise provides a method with which the publisher will determine whether GDPR scope applies to the app or user / device and if applicable, capture end user consent in [IAB EU Transparency Consent Framework](http://advertisingconsent.eu/) format.

Apps should provide wether they are in the GDPR scope, and if so the consent strings.
More informations in the [GDPR Consent Demo]([https://quantcast.mgr.consensu.org/index.html](https://quantcast.mgr.consensu.org/index.html)).

Usage example of MAdvertiseConsent
```java
if (isInGdprScope){
	MAdvertiseConsent.setConsentInformation(context, true, consents);
} else {
	MAdvertiseConsent.setConsentInformation(context, false, null);
}
```
Notes: 
- For now, end user consent string must be passed with key name IAB. Anything else will be ignored.