# Exchange React Native 

React Native support for [Payment.js](https://asxgw.com/documentation/gateway#payment-js-javascript-integration).

## Description

The following library allows developers to use [Payment.js](https://asxgw.com/documentation/gateway#payment-js-javascript-integration) with react native without ejecting. Developers can use it with both client and server side integrations.

## Prequisites

- This library relies on:

[React Native Webview](https://www.npmjs.com/package/react-native-webview), [Axio](https://www.npmjs.com/package/axios) and [React Native Config](https://github.com/luggit/react-native-config). Please follow the prequisites guide first before the installation.

## Installation

- Ensure you've completed the setps in [prequisites.](#prequisites)

- Install package via npm or yarn:

`npm install --save exchangecheckout` OR `yarn add exchangecheckout`

- Import in your project

```javascript
import ExchangeCheckout from "exchangecheckout";
```

## Usage

```jsx
import ExchangeCheckout from "exchangecheckout";

/*
Please make sure you follow react-native-config guide and make sure env config are properly setup,
otherwise you can apply your own way of obfuscating sensitive keys in your app.
*/
const apiInfo = {
  transactionApiUrl: Config.API_URL, // AllSecure Exchange gateway environment url
  apiKey: Config.API_KEY, // Api key
  apiUser: Config.API_USER, // Api username
  apiPassword: Config.API_PASS, // Api password
  webClientUrl: Config.WEB_CLIENT_URL, // Url of the web client that host card tokenization
};

const MyExchangeCheckout = () => (
  <ExchangeCheckout
    merchantApi={apiInfo}
    transactionId="" // Unique merchant transaction id
    amount="2.00"
    onSucccess={(data) =>
      console.log("Exchange checkout session is successful:", data)
    }
    onError={(err) => {
      Alert.alert("Error", err.response.errorMessage, [
        {
          text: "OK",
        },
      ]);
    }}
  />
);

export default MyExchangeCheckout;
```

## Component props

- `merchantApi` (Object) - REQUIRED key-val api data.
- `onSuccess` (?Function) - Called upon success of the payment session
- `onError` (?Function) - Called upon error of the checkout session
- `amount` (String) - Decimals separated by ., max. 3 decimals

### Roadmap

- advance form styling
- autofill feature
- cvv refreshing feature
- eslint
