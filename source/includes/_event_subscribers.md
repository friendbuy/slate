# Event Subscriptions

In addition to tracking events and loading widgets, friendbuy's javascript can also be used to establish event listeners on some browser-based friendbuy events.

The currently supported event subscriptions are:

* `couponReceived`

An event subscription will have the following format:

```javascript
friendbuyAPI.push(["subscribe", "couponReceived", callback]);
```

The `callback` parameter in the event subscription command is a function that will receive different values depending on the type of event. This function will be called in response to the subscribed event being triggered.

### couponReceived

The `couponReceived` event is triggered whenever a coupon is distributed to the user through a friendbuy widget. The callback function will receive the coupon code string that was distributed as its only argument.

#### Example Payload

```text
"20%-off-code"
```

#### Example Invocation

```javascript
friendbuyAPI.push(["subscribe", "couponReceived", 
    function (coupon) {
        console.log(coupon); // "20%-off-code"
        // Perform additional actions, like automatically
        // applying coupon code to next purchase.
    }
]);
```

