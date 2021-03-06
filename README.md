# SmartAPI Javascript Client SDK

## Installation
```bash
npm i smartapi-javascript
```

## Getting started with API
```javascript
let { SmartAPI, WebSocket } = require("smartapi-javascript");

let smart_api = new SmartAPI({
    api_key: "YOUR_API_KEY",    // PROVIDE YOUR API KEY HERE
    // OPTIONAL
    // access_token: "YOUR_ACCESS_TOKEN",
    // refresh_token: "YOUR_REFRESH_TOKEN"
});

smart_api.generateSession("CLIENT_CODE", "PASSWORD")
    .then((data) => {
        return smart_api.getProfile();

        // return smart_api.getProfile()

        // return smart_api.logout()

        // return smart_api.placeOrder({
        //     "variety": "NORMAL",
        //     "tradingsymbol": "SBIN-EQ",
        //     "symboltoken": "3045",
        //     "transactiontype": "BUY",
        //     "exchange": "NSE",
        //     "ordertype": "LIMIT",
        //     "producttype": "INTRADAY",
        //     "duration": "DAY",
        //     "price": "19500",
        //     "squareoff": "0",
        //     "stoploss": "0",
        //     "quantity": "1"
        // })

        // return smart_api.modifyOrder({
        //     "orderid": "201130000006424",
        //     "variety": "NORMAL",
        //     "tradingsymbol": "SBIN-EQ",
        //     "symboltoken": "3045",
        //     "transactiontype": "BUY",
        //     "exchange": "NSE",
        //     "ordertype": "LIMIT",
        //     "producttype": "INTRADAY",
        //     "duration": "DAY",
        //     "price": "19500",
        //     "squareoff": "0",
        //     "stoploss": "0",
        //     "quantity": "1"
        // });

        // return smart_api.cancelOrder({
        //     "variety": "NORMAL",
        //     "orderid": "201130000006424"
        // });

        // V2 API'S
        // return smart_api.getOrderBook();

        // return smart_api.getTradeBook();

        // return smart_api.getRMS();

        // return smart_api.getHolding();

        // return smart_api.getPosition();

        // return smart_api.covertPosition({
        //     "exchange": "NSE",
        //     "oldproducttype": "DELIVERY",
        //     "newproducttype": "MARGIN",
        //     "tradingsymbol": "SBIN-EQ",
        //     "transactiontype": "BUY",
        //     "quantity": 1,
        //     "type": "DAY"
        // });

    })
    .then((data) => {
        // Profile details
    })
    .catch(ex => {
        //Log error
    })

    // TO HANDLE SESSION EXPIRY, USERS CAN PROVIDE A CUSTOM FUNCTION AS PARAMETER TO setSessionExpiryHook METHOD
    smart_api.setSessionExpiryHook(customSessionHook);

    function customSessionHook() {
        console.log("User loggedout");
        
        // NEW AUTHENTICATION CAN TAKE PLACE HERE
    }
```

## Getting started with SmartAPI Websocket's
```javascript
########################### Socket Sample Code Starts Here ###########################

let web_socket = new WebSocket({
    client_code: "CLIENT_CODE",
    feed_token: "FEED_TOKEN",
    script: "nse_cm|2885&nse_cm|1594"   //exchange|token for multi stocks use & seperator
});

web_socket.connect();
web_socket.on('tick', receiveTick)

function receiveTick(data) {
    console.log("Receive stock ticks::", data)
}
########################### Socket Sample Code Ends Here ###########################
```