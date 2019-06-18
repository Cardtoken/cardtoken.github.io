# Getting Started
The following guide outlines the steps to get started.

**Model**
A tenant can have multiple merchants. A merchant can have multiple cards. A card can have multiple vendor tokens.

## Creating a tenant
A tenant provides the concept and properties of a solution, app or provider of payments.

A tenant allows creating multiple merchants and multiple gateways.

## Creating a merchant
A merchant holds the concept of cards, gateways and vendor tokens.

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
