![Millom Logo](images/Millom_Colour-02.png )
# Millom APIs
This repo hosts the APIs specifications for working with Telenor's [Millom](https://millom.com/) platform.
Millom is middleware exposing telco capabilities to third party Internet channels.
Millom's APIs allow authorized clients to retrieve current subscription balance,
a list of relevant offers, and activating one of the provided offers.

![Millom as middleware](images/millom-middle.svg)

Notifications can also be sent to service providers on events in the telco stack,
e.g. when user is about to run out of data or a purchase has been activated.  

---
## Prerequisites
All API requests to Millom must be authenticated with [OAuth 2.0 client credentials](https://oauth.net/2/grant-types/client-credentials/) access token.
The access token should be cached and reused until (almost) expiry.
Contact Millom for agreements and credentials.  

![Authorization example](images/authorization.svg)

---

Millom's APIs will generally reference end-user by two keys, the idValue and idType.

| idType | idValue | Description |
| ------- | ------ | ----------- |
| MSISDN | 475551234 | The users mobile number, on full E.164 form including country code |
| CPID   | abcd1234 | An anonymized token (a base 64 coded string) representing the user |

---
## APIs
Millom's downstream APIs connect to MNO's digital sales backend to retrieve and update status, offer and purchase information. Millom's upstream APIs connect to Service Providers and expose status, offers and purchase flow to end-customers.
In addition Millom provides a set of Managements API's that allow MNOs to look-up purchase status, customer insight analytics, etc.

| Exposing info to end-users | connecting and updating MNO's subscriber info | Service Management |
| ------ | ----------- | ------ |
| [Upsell API](apis/service-providers) | [End-user Account integration](apis/operators/backend) | Purchase look-up (TBA)|
| | [Notification API](apis/operators/notification) | Data Feedback Loop (TBA) |
| | [Purchase callback API](apis/operators/purchase-callback) | Settlements Reports (TBA) |

---
## Sandbox API
Millom provides a Sandbox API to enable easy testing of the Millom upstream API.<br/><br/>
Note that authentication is disabled on the Sandbox API (for simplicity), but production access requires OAuth 2.0 Client Credentials.

A Postman collection, with samples of the requests, is available here:

[![Run in Postman](https://run.pstmn.io/button.svg)](https://god.postman.co/run-collection/983e953bbad95bc8ccdd#?env%5BStandardGenericsDevelopment%5D=W3sia2V5IjoiYmFzZVVybCIsInZhbHVlIjoiaHR0cHM6Ly9hcGkuZGR0LmRldmVsb3BtZW50LnRlbGVub3IuaW8iLCJlbmFibGVkIjp0cnVlfSx7ImtleSI6InNlcnZpY2VQcm92aWRlciIsInZhbHVlIjoidGVzdHNlcnZpY2Vwcm92aWRlciIsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoic2lkSGF2ZUxvYW5OZWVkVG9wdXAiLCJ2YWx1ZSI6IjkyNDU0MjYxMDAwMCIsImVuYWJsZWQiOnRydWV9LHsia2V5Ijoic2lkSGF2ZU1vbmV5R29vZFRvR28iLCJ2YWx1ZSI6IjkyNDU0MjYxMDAwMyIsImVuYWJsZWQiOnRydWV9XQ==)

Please 'view documentation' in this Postman collection for more information and details.
