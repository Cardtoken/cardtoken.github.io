# Welcome to Cardtoken.io
The following guide outlines the steps to get started. Cardtoken.io is multi-provider service offered via a restful API.

## Supported Gateways
The following payment provider gateways are currently supported. If you need additional gateways added, please contact us. New gateways are certified and reviewed through PCI DSS compliance and operationally within 3 week(s).

| ------------ | ------------ | ------------ |
| Gateway      | Vendor token | Cardtoken.js |
| ------------ | ------------ | ------------ |
| Adyen        | Y | Y |
| AltaPay      | Y | Y |
| DIBS D2      | Y | N |
| DIBS D10     | Y | N |
| ePay/Bambora | Y | N |
| Netaxept     | Y | Y |
| PayLike      | Y | Y |
| Stripe       | Y | Y |
| QuickPay     | Y | Y |

## Supporting application vendors and merchants.
Cardtoken.io provides support for both application vendors and merchants with the difference that each vendor may have multiple merchants.

## Model
A tenant can have multiple merchants. A merchant can have multiple cards. A merchant can have multiple gateways. A card can have multiple vendor tokens, based on the number of gateways.

## Next steps
The following steps are suggested as continuation from this point.
* Read the [Client implementation guie](docs/client.md) here.
* Read the [Getting Started](docs/getting-started.md) guide here.
* Read the [API reference](api/) here.
