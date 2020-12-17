# Event Subscriptions

In addition to tracking events and loading widgets, friendbuy's javascript can also be used to establish event listeners on some browser-based friendbuy events.

The currently supported event subscriptions are:

- `couponReceived`
- `emailShareSuccess`
- `widgetActionTriggered`

The `callback` parameter in the event subscription command is a function that will receive different values depending on the type of event. This function will be called in response to the subscribed event being triggered.

## couponReceived

> Coupon Received Format

```html
<script>
  friendbuyAPI.push(["subscribe", "couponReceived", callback]);
</script>
```

> Example Coupon Received Payload

```text
"20%-off-code"
```

> Example Coupon Received Invocation

```html
<script>
  friendbuyAPI.push([
    "subscribe",
    "couponReceived",
    function (coupon) {
      console.log(coupon); // "20%-off-code"
      // Perform additional actions, like automatically
      // applying coupon code to next purchase.
    },
  ]);
</script>
```

The `couponReceived` event is triggered whenever a coupon is distributed to the user through a friendbuy widget. The callback function will receive the coupon code string that was distributed as its only argument.

## emailShareSuccess

> Email Share Success Format

```html
<script>
  friendbuyAPI.push(["subscribe", "emailShareSuccess", callback]);
</script>
```

> Example Email Share Success Payload

```json
{
  "email": "test@example.com",
  "campaignId": "4eb66e61-c466-45d7-b53d-52183217b28e",
  "widgetId": "ed317d7a-5546-4d2c-a3cc-52e1f5e5ae1b"
}
```

> Example Email Share Success Invocation

```html
<script>
  friendbuyAPI.push([
    "subscribe",
    "emailShareSuccess",
    function (share) {
      console.log(share);
      // Perform additional actions,
      // like sending the share to an analytics tool.
    },
  ]);
</script>
```

The `emailShareSuccess` event is triggered whenever an advocate sends an email share through a friendbuy widget. The callback function will receive the email of the advocate, as well as the ids of the campaign and widget used to send the share.

| Property   | type   | Description                                 |
| :--------- | :----- | :------------------------------------------ |
| email      | string | The email of the advocate.                  |
| campaignId | string | The id of the campaign the share came from. |
| widgetId   | string | The id of the widget the share came from.   |

## widgetActionTriggered

> Widget Action Triggered Format

```html
<script>
  friendbuyAPI.push(["subscribe", "widgetActionTriggered", callback]);
</script>
```

> Example Widget Action Triggered Payload

```json
{
  "actionName": "facebookShare",
  "campaignId": "46acc817-5ca9-4ab9-a597-c8c6dadadc03",
  "email": "test@example.com",
  "screenName": "Facebook Screen",
  "componentName": "Facebook CTA",
  "widgetConfigId": "41c55c45-eb9f-472d-a403-f1395cbeb601"
}
```

> Example Widget Action Triggered Invocation

```html
<script>
  friendbuyAPI.push([
    "subscribe",
    "widgetActionTriggered",
    function (action) {
      console.log(action);
      // Perform additional actions,
      // like sending the action to an analytics tool.
    },
  ]);
</script>
```

The `widgetActionTriggered` event is triggered when a user performs specific actions in the widget, including: clicking a share button, changing screens, submitting their email, copying their personal url, etc. The callback function will receive the following:

| Property       | type   | Description                                                                                                                                                                                                                                                                               |
| :------------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| actionName     | string | The name of the action being performed. For example: `friendEmailCaptured`, `advocateEmailCaptured`, `widgetClosed`, `emailShare`, `copyText`, `twitterShare`, `facebookShare`, `smsShare`, `messengerShare`, etc. Note the action names may very depending on how your widget is set up. |
| campaignId     | string | The id of the campaign the action came from.                                                                                                                                                                                                                                              |
| email          | string | The email of the user performing the action.                                                                                                                                                                                                                                              |
| screenName     | string | The name of the screen the action occured on. This is deteremined by the name given to the screen in the widget builder.                                                                                                                                                                  |
| componentName  | string | The name of the component that triggered the action, as defined in the widget builder. Give your buttons and other components descriptive names for the best effect.                                                                                                                      |
| widgetConfigId | string | The id of the widget the action came from.                                                                                                                                                                                                                                                |
