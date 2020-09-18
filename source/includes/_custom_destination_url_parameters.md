# Custom Destination URL Parameters

> Code Samples

```html
<script>
  friendbuyAPI.push([
    "set",
    "utm_params",
    { utm_survey: "true", utm_page: "refer" },
  ]);
</script>
```

> Example Destination URL

```text
http://yoursite.com?utm_survey=true&utm_page=refer
```

Friendbuy allows you to set custom query string parameters for any share that takes place. When you set custom parameters, Friendbuy will include them in the shares that are created on that page. When someone clicks on a shared link, a query string parameter will be added for each of the custom parameters provided. Any custom parameters that copy an existing reserved parameter will be added as duplicate parameters.

**Note** that all custom parameters must start with `utm_`.
