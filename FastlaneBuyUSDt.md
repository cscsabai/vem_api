# API documentation for Exchange Module: Fastlane Buy USDt over fiat gateway function
version: 1.0

RESTful API for VEM backend. Default output is NON pretty printed JSON.

##API calls list<br>
**Functions:**   
    [Public:registerSilentRequestWL1](#publicregistersilentrequest_custom_wl1)  
 

# Public:registerSilentRequestWL1

Create a fastlane USDt only buy request with full customer registration and onboarding process.

**URL** : `https://{APIENDPOINT}/express/api/v0.1/public/registersilentrequest_custom_wl1`

**Method** : `POST`

**Auth required** : NO

**Data constraints**

Provide necessary information of registration, onboarding and buy request.

```json
{
    "email_address": "[string, equal with the login name later]",
    "mobile_num": "[string, SMS ready mobile number with plus and countrycode prefix, do not use any separator!]",
    "coin_id": "[int, coin identifier of source, only HUF int(7) and EURO int(5) is allowed here!]",
    "dest_coin_id": "[int, coin identifier for buy request, only USDt int(10) is allowed here!]",
    "amount": "[float, source amount to buy, cointed in 'coin_id' currency]",
    "first_name": "[string, first name of buyer]",
    "last_name": "[string, last name of buyer]",
    "dest_addr": "[string, destination address when will contains the bought USDt (Only OMNI/Bitcoin addresses is allowed)]",
    "lang": "[string, prefered language for communication with customr, only 'hu' and 'en' allowed]",
    "affiliate": "[string, inviter customer's affiliate code for bonuses]",
}
```

**Success result**

```json
{
  "error": {
    "code": "none", 
    "message": "none"
  }, 
  "result": {
    "status": "ok"
  }
}
```

**Error results**  
* EGEN_badreq_E001 / Bad request or missing field, please check the API documentation
* EGEN_dbresp_E001 / Backend's response is invalid, please contact support
* BUY_invalid_coin / Invalid coin id for buy request
* EGP_missing_E001 / Missing or invalid trading pair. Only HUFUSDt and EURUSDt is allowed in this API endpoint!
* EWADD_invalid_E002 / Invalid withdraw address, check coin type and address again, only OMNI/Bitcoin addresses is allowed
* EREG_invemail_E001 / The specified email address is invalid
* KYC_invphone_E001 / Invalid phone number, please try it again
* KYC_numused_E001 / Mobile number already used for other account
* EGEN_unauth_E001 / Customer exists in VEM with this informations, need to log in
* EWADD_invalid_E003 / Invalid address, address already used
* EADD_wronguser_E001 / Wallet address does not belong to the user
* BUY_bainvalid_E001 / Missing, invalid or other user's bank account
* REQ_invalid / Invalid request
