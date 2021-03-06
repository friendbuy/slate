# Integration Setup

## Merchant SDK Javascript

> Code Samples

```html
<script>
  window["friendbuyAPI"] = friendbuyAPI = window["friendbuyAPI"] || [];

  // registers your merchant using your merchant ID found in the
  // retailer app https://retailer.fbot.me/settings/general
  friendbuyAPI.merchantId = "REPLACE_WITH_YOUR_MERCHANT_ID";
  friendbuyAPI.push(["merchant", friendbuyAPI.merchantId]);

  // load the merchant SDK and your campaigns
  (function (f, r, n, d, b, u, y) {
    while ((u = n.shift())) {
      (b = f.createElement(r)), (y = f.getElementsByTagName(r)[0]);
      b.async = 1;
      b.src = u;
      y.parentNode.insertBefore(b, y);
    }
  })(document, "script", [
    "https://static.fbot.me/friendbuy.js",
    "https://campaign.fbot.me/" + friendbuyAPI.merchantId + "/campaigns.js",
  ]);
</script>
```

To the right is the minimal integration to be placed in your site header. The tracking library and its instructions are designed to work asynchronously, so that if any anomalies should occur with friendbuy, there will be no impact to the behavior of your website.

Our friendbuy integration library is compatible with SPA \(Single Page Application\) design, see the `track page` section to report page changes.

### Namespace consideration

Only the `friendbuyAPI` variable is to be considered reserved on the `window` object. The friendbuy library \(including its dependencies\) is completely encapsulated and is only partially accessible through controlled `push(...)` calls on the `window.friendbuyAPI` gateway.
