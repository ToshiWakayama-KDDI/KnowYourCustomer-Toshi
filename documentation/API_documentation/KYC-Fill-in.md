# CAMARA KnowYourCustomer KYC Fill-in API

(NOTE: This API description is supposed to be incorporated into the YAML definition file in the future releases.)

This API provides the customer with the ability request and receive the information for a particular user, which on file (and verified) by the user's Operator in their own KYC records, in order for the SP to confirm the accuracy of the information and provide a specific service to the user.

## Relevant Definitions and concepts

* **KYC**: stands for Know Your Customer and it is the process of a business verifying the identity of their clients and assessing their suitability, along with the potential risks of illegal intentions towards the business relationship.

## API Functionality

This API allows API clients to request for API provider / MNO to provide information related to a mobile phone user, derived from the account data bound to their phone number.  The API is intended to be used in the following scenario, for example:

* To fill-in the user personal data during the digital registration of an account to a 3rd party service.

The following figure is the generic high-level flows of this API.  

<img width="854" alt="KYC_Fill-in_flow" src="https://github.com/ToshiWakayama-KDDI/KnowYourCustomer-Toshi/assets/53090722/f23daa52-bb28-4236-b90d-0184d303f907">

Note:

* Before calling this API, 3rd parties / enterprise customers who want to use this API should make contract with API provider/ Operator for use of this API.  As that will depend on each API provider / MNO's business processes as well as GSMA Open Gateway standard process, it is out of scope of this API definition.

* When calling this API, at the beginning, there should be required processes for Authentication / Authorisation / End User Consent capturing.  As those processes are to be defined as CAMARA commonality standards, they are out of scope of this API definition, however, use of the OpenID Connect (OIDC) is stated as security scheme.  **As an important note**, capturing end user consent is necessary, because this API provides end user information (PII).

* The above mentioned AuthN/AuthZ/End User consent capturing processes can give the API provider/ MNO the 3rd party identity (with the Access Token) and the end user identity (with the ID Token), so the API provider/ MNO can identify the 3rd party / enterprise customer and the end user.  Then, it is up to API provider/ MNO to decide which information the 3rd party will receive by calling the API, and also the API provider / MNO is responsible for security and privacy issues.

* For example, below is a potential operation:
  * when making contract with API provider/ MNO, a 3rd party / enterprise customer receives its 3rd party identity and also decide which information (attributes) it will receive for its API call
  * then, API provider / MNO will provide information (attributes) which the 3rd party / enterprise customer is allowed to receive by the contract.


## Resources and Operations overview

The API provides the following endpoint:

* An endpoint to request information related to an end user against the acount data bound to their phone number.


