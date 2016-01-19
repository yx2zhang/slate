---
title: Subscription System Reference

language_tabs:
  - Node

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction
Subscription Documentation 

# SignUp

## Paypal Payment Sign Up

> Example Request

```javascript

request.post("https://connect.monstercat.com/subscription/paypal/sign-up/licensee").send({
  plan: {
    planId: "Monstercat Subscription Gold month development"
  },
  userEmail: "test@monstercat.com",
  referralCode: "NyKkQAlue"
}).end(function(err, res) {
  // asynchronously called
});
```

> Example Response

```json
{
  "body": "https://www.sandbox.paypal.com/webscr?cmd=_express-checkout&token=EC-1P504168A6727094R"
}
```
### HTTP Request

`POST https://connect.monstercat.com/subscription/paypal/sign-up/licensee`

## Stripe Payment Sign Up

> Example Request

```javascript

request.post("https://connect.monstercat.com/subscription/stripe/sign-up/licensee").send({
  returnUrl: "#{location.protocol}//#{location.host}/#sign-up/:code"
  plan: {
    planId: "Monstercat Subscription Gold month development"
  },
  stripeToken: token,
  userEmail: "test@monstercat.com",
  referralCode: "NyKkQAlue"
}).end(function(err, res) {
  // asynchronously called
});
```
> Example Response

```json

{
  "body":{
    "subscription": {
      "_id": "569d5d9c22e0baf63a4a521c",
      "subscriptionActive": true,
      "subscriptionCanceling": false,
      "subscriptionCurrentAmount": 999,
      "subscriptionCustomerId": "cus_7kFLnZfZcm5aIz",
      "subscriptionId": "sub_7kFLIrkV7Nagic",
      "subscriptionPaymentEmail": "jack+uto@monstercat.com",
      "subscriptionPaymentType": "stripe",
      "subscriptionPeriodEnd": "2016-02-18T21:48:12.000Z",
      "subscriptionPlan": "Monstercat Subscription Gold  month development",
      "userId": "569d5d9c22e0baf63a4a521d",
      "subscriptionPlanDetails":{
        "amount": 999,
        "channelNum": 2,
        "description": "$9.99/MONTH",
        "env": "development",
        "key": "pk_test_4ag4k0EknfknJi4TwJzoEO1e",
        "period": 1,
        "planId": "Monstercat Subscription Gold  month development",
        "userTypes": ["golden", "subscriber"]
      }
    },
    "user": {
      "_id": "569d5d9c22e0baf63a4a521d",
      "verify": "e8c1a5f56a5b45a79fc7aeda51455688",
      "type": ["golden", "subscriber"],
      "verify": "e8c1a5f56a5b45a79fc7aeda51455688",
      "created": "2016-01-18T21:48:12.047Z",
      "email": "test@monstercat.com",
      "label": ["52199744a7a952b793c0a771"],
      "locale": "en",
      "newSubscriber": false,
      "paymentType": "PayPal",
      "subscribed": true,
      "subscriptionModelId": "569d5d9c22e0baf63a4a521c"
    }
  }
}
```

### HTTP Request

`POST https://connect.monstercat.com/subscription/stripe/sign-up/licensee`

# Subscription

## Retrieve Subscription

> Example Request

```javascript

request.get("https://connect.monstercat.com/subscription/569c99290f979d1d3121dcaa").end(function(err, res) {
  // asynchronously called
});
```
> Example Response

```json
{
  "body": {
    "subscription":{
      "subscriptionPlanDetails":
        { "userTypes": [ "licensee", "subscriber" ],
          "description": "$14.99/MONTH",
          "dollarCost": null,
          "key": "pk_test_4ag4k0EknfknJi4TwJzoEO1e",
          "env": "development",
          "channelNum": 2,
          "period": 1,
          "amount": 1499,
          "planId": "Monstercat License Subscription  1 months 2 channels development" },
      "userId": "569c99290f979d1d3121dcab",
      "subscriptionPlan": "Monstercat License Subscription  1 months 2 channels development",
      "subscriptionPeriodEnd": "Wed Feb 17 2016 23:50:02 GMT-0800 (PST)",
      "subscriptionPaymentType": "stripe",
      "subscriptionPaymentEmail": "jack+9923@monstercat.com",
      "subscriptionId": "sub_7k2DUeDJFnZvru",
      "subscriptionCurrentAmount": 1499,
      "subscriptionCanceling": false,
      "subscriptionActive": true,
      "subscriptionCustomerId": "cus_7k2DuqW4YYTPKK",
      "__v": 0,
      "_id": "569c99290f979d1d3121dcaa"
    }
  }
}
```
### HTTP Request

`GET https://connect.monstercat.com/subscription/:id`

## Add Channel

> Example Request

```javascript

request.post("https://connect.monstercat.com/subscription/addChannel/569c99290f979d1d3121dcaa").end(function(err, res) {
  // asynchronously called
});
```
> Example Response

```json
{
  "body":{
    "subscription":{
      "subscriptionPlanDetails":
       { "description": "$19.98/MONTH",
         "dollarCost": null,
         "key": "pk_test_4ag4k0EknfknJi4TwJzoEO1e",
         "env": "development",
         "userTypes": [ "licensee", "subscriber" ],
         "channelNum": 3,
         "period": 1,
         "amount": 1998,
         "planId": "Monstercat License Subscription  1 months 3 channels development" },
      "userId": "569c99290f979d1d3121dcab",
      "subscriptionPlan": "Monstercat License Subscription  1 months 3 channels development",
      "subscriptionPeriodEnd": "Wed Feb 17 2016 23:50:02 GMT-0800 (PST)",
      "subscriptionPaymentType": "stripe",
      "subscriptionPaymentEmail": "jack+9923@monstercat.com",
      "subscriptionId": "sub_7k2DUeDJFnZvru",
      "subscriptionCurrentAmount": 1998,
      "subscriptionCanceling": false,
      "subscriptionActive": true,
      "subscriptionCustomerId": "cus_7k2DuqW4YYTPKK",
      "__v": 0,
      "_id": "569c99290f979d1d3121dcaa" 
    }
  }
}
```
### HTTP Request

`POST https://connect.monstercat.com/subscription/addChannel/:id`

## Update Subscription

> Example Request

```javascript

request.post("https://connect.monstercat.com/subscription/update/569c99290f979d1d3121dcaa").send({
  plan: {
    planId: "Monstercat Subscription Gold month development"
  }
}).end(function(err, res) {
  // asynchronously called
});
```
> Example Response

```json

{
  "body":{
    "subscription":{
      "subscriptionPlanDetails":
       { "userTypes": [ "licensee", "subscriber" ],
         "description": "$14.99/MONTH",
         "dollarCost": null,
         "key": "pk_test_4ag4k0EknfknJi4TwJzoEO1e",
         "env": "development",
         "channelNum": 2,
         "period": 1,
         "amount": 1499,
         "planId": "Monstercat License Subscription  1 months 2 channels development" },
      "userId": "569c99290f979d1d3121dcab",
      "subscriptionPlan": "Monstercat License Subscription  1 months 2 channels development",
      "subscriptionPeriodEnd": "Wed Feb 17 2016 23:50:02 GMT-0800 (PST)",
      "subscriptionPaymentType": "stripe",
      "subscriptionPaymentEmail": "test@monstercat.com",
      "subscriptionId": "sub_7k2DUeDJFnZvru",
      "subscriptionCurrentAmount": 1499,
      "subscriptionCanceling": false,
      "subscriptionActive": true,
      "subscriptionCustomerId": "cus_7k2DuqW4YYTPKK",
      "__v": 0,
      "_id": "569c99290f979d1d3121dcaa"
    }
  }
}
```

### HTTP Request

`POST https://connect.monstercat.com/subscription/update/:id`


## Cancel Subscription

> Example Request

```javascript

request.post("https://connect.monstercat.com/subscription/cancel/569c99290f979d1d3121dcaa").end(function(err, res) {
  // asynchronously called
});
```
> Example Response

```json

{
  "body": {
    "subscription":{
      "subscriptionPlanDetails":
      {
        "userTypes": ["licensee", "subscriber"],
        "description": "$14.99/MONTH",
        "dollarCost": null,
        "key": "pk_test_4ag4k0EknfknJi4TwJzoEO1e",
        "env": "development",
        "channelNum": 2,
        "period": 1,
        "amount": 1499,
        "planId": "Monstercat License Subscription  1 months 2 channels development"
      },
      "userId": "569d7b6b762776a842d06be5",
      "subscriptionPlan": "Monstercat License Subscription  1 months 2 channels development",
      "subscriptionPeriodEnd": "Thu Feb 18 2016 15:55:23 GMT-0800 (PST)",
      "subscriptionPaymentType": "stripe",
      "subscriptionPaymentEmail": "jack+upgrade@monstercat.com",
      "subscriptionId": "sub_7kHPNxFkBhulQ2",
      "subscriptionCurrentAmount": 1499,
      "subscriptionCanceling": true,
      "subscriptionActive": true,
      "subscriptionCustomerId": "cus_7kHP4P8p36kPdd",
      "__v": 0,
      "_id": "569d7b6b762776a842d06bea" }
  }
}
```

### HTTP Request

`POST https://connect.monstercat.com/subscription/cancel/:id`

