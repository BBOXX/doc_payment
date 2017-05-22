---
title: API Reference

language_tabs:
  - shell
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---


# BBOXX BUSINESS API REFERENCE

## Introduction


The BBOXX BUSINESS API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects.



# BBOXX MOBILE MONEY REFERENCE

## Introduction

 The  HTTP(S) POST Notification API is designed to help developers integrate third-party applications with bboxx mobile money (. This guide provides the technical information about integrating and configuring a system with  using a RESTful HTTP(S) POST as the method of notification for Mobile Money transaction information. Enterprises can leverage the API to allow real-time acquisition of mobile money transactions processed via the System. This document describes the HTTP POST parameters and the format of the expected response.
Synchronous or Near Real-Time Transactions

Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects. 



## Authentication

Authenticate your account when using the API by including your secret API key in the request. You can manage your API keys in the Dashboard. Your API keys carry many privileges, so be sure to keep them secret! Do not share your secret API keys in publicly accessible areas such GitHub, client-side code, and so forth. 


Requirements: "Basic" authentication credentials (if in use)
HMAC: Keyed-Hashing for Message Authentication

To improve the security of authentication, a keyed-hash message authentication code (HMAC) is used to calculate a Message Authentication Code (MAC) that is sent over as one of the parameters (signature) and can be used to verify that the request is coming from you . The cryptographic hash function SHA-1 is used to calculate the HMAC (HMAC-SHA1).




```python

        body = dataIntegrity
        MessageId =  str(self.Messageid)
        originId = str(self.originId)
        CustomerId  = str(self.customerId)
        TransactionId = str(self.transaction_reference)
        signature = str(self.key)

        dataencoded = body + MessageId + originId + CustomerId
        try :
            hashed = hmac.new(signature, dataencoded.encode('UTF-8'), sha1)
        except Exception as e:
            print 'error hash - 403 Forbidden Response'
        responseIntegrity = hashed.digest().encode("base64").rstrip('\n')
        header_auth = customerId+':'+responseIntegrity
        if str(header_auth) == self.Authorization:
            return True
        return False
```




## Header

The following headers are mandatory for every message
exchanged with this REST API:

Name | description | Exemple
---------- | ------- | -------
Content-Type | If a request payload is sent, it should always be a JSON string | application/json
Authorization | Hash to authentication the requesting system | clientXYZ:uCMfSzkjue+HSDygYB5aEg==
MessageTimestamp |Message timestamp  | Date (YYYYMMDDHHMISS)






## Request

The POST request will be sent to the following URL. The following POST parameters that will be passed will be as follows:


Parameter | description | Exemple
---------- | ------- | -------
ProviderId | Bad Request -- |
transactionId | Unauthorized -- |
business_number | The Paybill number or Till number being paid to |
service_name | The Mobile Money Provider  |
transaction_reference | The reference number as assigned to the transaction by the mobile money provider | 
internal_transaction_id | The internal ID of the transaction within Kopo Kopo. |
transaction_timestamp | The time stamp of the transaction in ISO 8601 format.  |
transaction_type | The type of the transaction eg. Paybill, Buygoods etc, |
account_number | The account number as entered by the subscriber. (optional – only for Paybill payments) |
sender_phone | The subscriber's phone number (subscriber making the payment) in E.164 format | 
first_name | The first name of the subscriber |
middle_name | The middle name of the subscriber| 
last_name | The last name of the subscriber |
amount | The transaction amount |
currency | Currency in use |


```python
body = '{

  
}'


url =  'https://apierp.bboxx.co.uk/mm/'

post = requests.post(url=url, header= header, body= body)

        body = dataIntegrity
        MessageId =  str(self.Messageid)
        originId = str(self.originId)
        CustomerId  = str(self.customerId)
        TransactionId = str(self.transaction_reference)
        signature = str(self.key)

        dataencoded = body + MessageId + originId + CustomerId
        try :
            hashed = hmac.new(signature, dataencoded.encode('UTF-8'), sha1)
        except Exception as e:
            print 'error hash - 403 Forbidden Response'
        responseIntegrity = hashed.digest().encode("base64").rstrip('\n')
        header_auth = customerId+':'+responseIntegrity
        if str(header_auth) == self.Authorization:
            return True
        return False
```





## Response


Upon the successful processing of the POST request, a JSON encoded response will be expected in the following format: 

Parameter | description | Exemple
---------- | ------- | -------
ProviderTransactionId | The  provider’s reference ID of the payment |
Status | The status of the payment: | REJECTED -ACCEPTED
Description | Tne description message  | Dear Customer the payment was accepted.




## Status codes

The bboxx Mobile Money API uses the following codes:



Code | description 
---------- | ------- 
40001  | Bad Request --
40002 | Unauthorized -- 
40003 | The Paybill number or Till number being paid to 
40004 | The Mobile Money Provider  
