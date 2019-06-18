# Getting Started
The following guide outlines the steps to get started.

## Understanding the model
Cardtoken.io is meant for application- and solution providers. As such, the model of Cardtoken.io allows seperation of merchant and tenants. 

A tenant can have multiple merchants. A merchant can have multiple cards. A card can have multiple vendor tokens.

## Creating an application vendor (a tenant)
A tenant provides the concept and properties of a solution, app or provider of payments. A tenant holds one or many merchants.
A tenant allows creating multiple merchants and multiple gateways.

```curl
curl -X POST \
  https://api.cardtoken.io/tenants \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{	"Name" : "Sugar Hill Services", "Email" : "somebody@sugarhill.tld" }'
```

Once a merchant is created, an e-mail is sent to activate the account. Please activate the account before adding a merchant. This e-mail and the response of the API will return a tenant key. *PLEASE STORE THIS KEY SAFELY FOR FUTURE REFERENCE. KEEP THE KEY SAFE AND SECURE.*.

## Creating a merchant
A merchant holds the concept of cards, gateways and vendor tokens. A merchant can be a webshop, an application or a single company consuming a payment solution.

```curl
curl -X POST \
  https://api.cardtoken.io/merchants/ \
  -u 'paste-key-here:'
  -H 'Accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{ "Name" : "webshop 222", "TestMode" : true }'
```

Once a merchant is created. Next step is to add a payment gateway.

---

# Advanced topics

## 3d Secure
In this sample we will be using QuickPay with CardToken and 3D secure. The flow details as follows.

1. Create a gateway on the merchant using QuickPay.
2. Add a card using CardToken. The card will return a Card, a Token and a Vendor Token.
3. In this case, the vendor token (quickpay) is the **card-id**.
4. Using this **card-id**, you can use the credentials and directly retrieve a payment link (https://api.quickpay.net/cards/:cardid/link) of the card using the QuickPay API. This request will not proxy through CardToken.
5. To use *3d-secure* add the form-data of `payment_methods = 3d-visa`.
6. You can now link the 3d-secure payment and process.
7. Subsequent payments using CardToken will re-tokenize the payment and process without 3d Secure.
