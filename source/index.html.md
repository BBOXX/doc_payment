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

# Introduction
 The  HTTP(S) POST Notification API is designed to help developers integrate third-party applications with bboxx mobile money (. This guide provides the technical information about integrating and configuring a system with K2 using a RESTful HTTP(S) POST as the method of notification for Mobile Money transaction information. Enterprises can leverage the API to allow real-time acquisition of mobile money transactions processed via the K2 System. This document describes the HTTP POST parameters and the format of the expected response.
Synchronous or Near Real-Time Transactions

Enterprises that want to receive their mobile money transaction details as they are processed will utilize the XML over HTTP(S) bridge or the HTTP(S) POST Notification API. This document details the HTTP(S) POST Notification API option. The HTTP POST Notification API requires that the Enterprise system in question (Back Office MIS) expose a URL that HTTP or HTTPS (preferable) POST requests can be sent to. 


# Authentication

> To authorize, use this code:


```python
import json
import requests


api = request.post('XXXXXX')
```

```shell
# With shell, you can just pass the correct header with each request


curl -H "Accept/*" -H "Content-Type: application/json" -H "Authorization:12000:fq/LZ0n8YxOp0tC3NLaj6GbPFE8=
" -H "SMSSupport:Y" -H "MessageID:74e46da2-41ff-8bba-f529-930acbffdb4c" -H "MessageTimestamp:20161029113022" -X POST -d '{"transactionId" : "123647","reference" : "4526","origin" : {  "operator" : "mtn_tst",  "subscriber" : "250786474859",  "countryCode" : "RW"},"amount" : {  "local" : {    "currency" : "RWF",    "value" : 200.0  },  "target" : {    "currency" : "RWF",    "value" : 200.0  },  "exchangeRate" : 0.0},"extensions" : [ {  "name" : "extension1",  "value" : "paymentRef:"} ]
}' -i http://127.0.0.1:5000/mm/1.0/payments/payment/200/customers/12000/payments


```



Bboxx use Security Code to allow access to the API . You can register a new Kittn API key at our [developer portal](http://example.com/developers).


Bboxx expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: XXXXXXXX`

<aside class="notice">
You must replace <code>XXXXX</code> with your personal API key.
</aside>



This endpoint retrieves all Payments.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Payment

```python
import json
import requests


api = request.post('XXXXXX')
```

```shell
# With shell, you can just pass the correct header with each request


curl -H "Accept/*" -H "Content-Type: application/json" -H "Authorization:12000:fq/LZ0n8YxOp0tC3NLaj6GbPFE8=
" -H "SMSSupport:Y" -H "MessageID:74e46da2-41ff-8bba-f529-930acbffdb4c" -H "MessageTimestamp:20161029113022" -X POST -d '{"transactionId" : "123647","reference" : "4526","origin" : {  "operator" : "mtn_tst",  "subscriber" : "250786474859",  "countryCode" : "RW"},"amount" : {  "local" : {    "currency" : "RWF",    "value" : 200.0  },  "target" : {    "currency" : "RWF",    "value" : 200.0  },  "exchangeRate" : 0.0},"extensions" : [ {  "name" : "extension1",  "value" : "paymentRef:"} ]
}' -i http://127.0.0.1:5000/mm/1.0/payments/payment/200/customers/12000/payments


```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve


# Request

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


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




# Response


<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


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


## Status codes

Parameter | description | Exemple
---------- | ------- | -------
ProviderId | Bad Request -- |
transactionId | Unauthorized -- |
business_number | The Paybill number or Till number being paid to |
service_name | The Mobile Money Provider  |