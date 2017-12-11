---
title: API Reference

language_tabs:
  - python


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---



# BBOXX MOBILE MONEY API

## Introduction

 The  HTTP(S) POST Notification API is designed to help developers integrate third-party applications with BBOXX Mobile Money-system. This guide provides the technical information about integrating and configuring a system by  using RESTful HTTP(S) POST to recieve notification of Mobile Money transaction information. Companies can use this API to allow real-time mobile money transactions to be processed via Pulse. This document describes the HTTP POST parameters and the format of the expected response.
Synchronous or Near Real-Time Transactions.

Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects. 



## Authentication



Authenticate your account when using the API by including your secret API key in the request. You can manage your API keys in the Dashboard. Your API keys carry many privileges, so be sure to keep them secret! Do not share your secret API keys in publicly accessible areas such GitHub, client-side code, and so forth. 



```python


        dataencoded = body + MessageId + originId + CustomerId
        try :
            hashed = hmac.new(signature, dataencoded.encode('UTF-8'), sha1)
        except Exception as e:
            print 'error hash - 403 Forbidden Response'
        responseIntegrity = hashed.digest().encode("base64").rstrip('\n')
        header_auth = CustomerId+':'+responseIntegrity
        if str(header_auth) == Authorization:
            return True
        return False
```


### Signature

Requirements: "Basic" authentication credentials (if in use)
HMAC: Keyed-Hashing for Message Authentication

To improve the security of authentication, a keyed-hash message authentication code (HMAC) is used to calculate a Message Authentication Code (MAC) that is sent over as one of the parameters (signature) and can be used to verify that the request is coming from you . The cryptographic hash function SHA-1 is used to calculate the HMAC (HMAC-SHA1).




##  Payment notification


### Headers

The following headers are mandatory for every message exchanged with this REST API:


```python


Headers ={' Authorization':'12000:fq/LZ0n8YxOp0tC3NLaj6GbPFE8=', 'SMSSupport:Y' ,
'MessageID':'74e46da2-41ff-8bba-f529-930acbffdb4c','MessageTimestamp':'20161029113022'} 

```

Name | description 
---------- | ------- 
Content-Type | If a request payload is sent, it should always be a JSON string 
Authorization | Hash to authentication the requesting system 
MessageTimestamp |Message timestamp  



### HTTP POST


#### Description
This endpoint allows for a payment to be created. 


The POST request will be sent to the following URL:
https://apierp.bboxx.co.uk/mm/1.0/payments/payment/<Providerid>/customers/<CustomerId>/payments


Name | description 
---------- | ------- 
ProviderId | If a request payload is sent, it should always be a JSON string 
CustomerId | Hash to authentication the requesting system 






#### Request Payload
Following table provides information of each JSON field of the HTTP request body:

```python
url =  'https://apierp.bboxx.co.uk/mm/1.0/payments/payment/200/customers/12000/payments'

Headers ={' Authorization':'12000:fq/LZ0n8YxOp0tC3NLaj6GbPFE8=', 'SMSSupport:Y' ,
'MessageID':'74e46da2-41ff-8bba-f529-930acbffdb4c','MessageTimestamp':'20161029113022'} 

body = '{"transactionId" : "123647",
"reference" : "4526",
  "operator" : "Mobile_provider", 
   "subscriber" : "250786474859", 
    "countryCode" : "RW", 
    "currency" : "RWF", 
    "transaction_type": "PayBill"
    "first_name": "Jhon",
    account_number:"45678",
    "last_name": "Doe",

     "amount" : 200.0 }' 

post = requests.post(url=url, header= header, body= body)

      
```

Fields | Description 
----------| ------- 
transactionId <br><font color="DarkGray">_string_</font> | Unauthorized 
business_number<br><font color="DarkGray">_string_</font>  | The Paybill number or Till number being paid to 
operator<br><font color="DarkGray">_string_</font> | The Mobile Money Provider 
transaction_reference <br><font color="DarkGray">_string_</font>| The reference number as assigned to the transaction by the mobile money provider  
internal_transaction_id<br><font color="DarkGray">_string_</font> | The internal ID of the transaction within Kopo Kopo. 
transaction_type <br><font color="DarkGray">_string_</font>| The type of the transaction eg. Paybill, Buygoods etc, 
account_number <br><font color="DarkGray">_string_</font> | The account number as entered by the subscriber. (optional – only for Paybill payments) 
sender_phone <br><font color="DarkGray">_string_</font> | The subscriber's phone number (subscriber making the payment) in E.164 format 
first_name <br><font color="DarkGray">_string_</font> | The first name of the subscriber 
last_name <br><font color="DarkGray">_string_</font>| The last name of the subscriber 
amount <br><font color="DarkGray">_int_</font>| The transaction amount 
currency <br><font color="DarkGray">_string_</font> | Currency in use 



### Response Payload 


Upon the successful processing of the POST request, a JSON encoded response will be expected in the following format: 


```python

 {"providerTransactionId":"0123456",
        "status": "ACCEPTED",
        "Description": "Dear Customer the payment was accepted."}


```

Parameter | description 
---------- | ------- 
ProviderTransactionId | The  provider’s reference ID of the payment 
Status | The status of the payment: 
Description | Tne description message  










