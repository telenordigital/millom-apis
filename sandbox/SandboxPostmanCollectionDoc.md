# The Millom Sandbox

## Introduction

The Millom Sandbox provides a smooth and fast introduction to the Millom upstream API. 
It includes a Postman collection with samples of the flows specified in the Millom upstream API. 
The collection utilises one of our backends, which is running the same code as our Millom Production services, 
but with mocked MNO responses.

Note that authentication is disabled on the Millom Sandbox backend (for simplicity), 
but production access requires OAuth 2.0 Client Credentials.

## The Postman collection

The collection contains samples on all the flows in the the Millom upstream API.
Specifically the following flows are demonstrated:

- account info
- balance
- upsell offer
- purchase plan

The sandbox backend is currently running without authentication, it uses mocked data, 
and have provisioned a test service-provider that is used in this collection.

## How to use the collection

Make sure that you select the supplied ***StandardGenericsDevelopment*** environment before you run the requests.

This environment defines variables used throughout all requests:

- baseUrl - The base URL for accessing the Millom service.
- serviceProvider - The service-provider provisioned in the Millom upstream API.

In addition, the environment provides two sample MSISDNs:

- sidHaveMoneyGoodToGo - This subscriber have money and offers, and can purchase.
- sidHaveLoanNeedTopUp - This subscriber do not have money and have loan, is not presented any offers, and can not purchase.

Try out these MSISDNs to familiar yourself with the flows. You may as well try other sids, 
and change other parameters, to provoke different error responses.

The 'Purchase plan' request takes an argument in the request-body called planid, 
this is the identification of the plan that shall be purchased. 
The offered plans are found in the response of the 'Get upsellOffer' request. 
Find the plan, and the planid, from this response, to use in the 'Purchase plan' request-body.

Note that the Millom backend implements a timer on purchases, preventing frequent purchases of the same plan. 

## References
The Millom upstream API is documented on: <br>
https://telenordigital.github.io/millom-apis/apis/service-providers

The Postman collection can be imported into your Postman Workspace from here: <br>
    https://github.com/telenordigital/millom-apis#get-the-postman-collection

## A friendly request from the Millom team
This Sandbox shall be used to familiar yourself with the Millom API, its requests and its responses. 
Please do not run heavy loads towards the Millom sandbox backend, and please stop any scripts, 
and such, when the day is over.


