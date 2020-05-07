# Tracking Call Examples

## Tracking Customer

You may provide the customer's information on the widget using a track customer call. This reduces friction during the sharing process by pre-filling these fields in the widget.

To track a customer use the following tracking call:

```markup
<script>
  friendbuyAPI.push([
    "track",
    "customer",
    {
      id: "customer-1",
      email: "john.doe@example.com",
      firstName: "John",
      lastName: "Doe",
    },
  ]);
</script>
```

## Tracking email

If you were to only know the email of the visitor, you can use the track email command which only requires an email to be captured.

```markup
<script>
  friendbuyAPI.push([
    "track",
    "email",
    { email: "john.doe@example.com" },
  ]);
</script>
```

## Tracking Pages

You can name your pages to simplify widget display triggers and analytics. To do so, make sure the page you want to track includes the merchant SDK integration code above.

```markup
<script>
  friendbuyAPI.push(["track", "page", { name: "home" }]);
</script>
```

We recommend naming pages like "product", "homepage", "post-purchase"

## Tracking Purchase

Tracking a purchase requires a few mandatory fields:

* `amount`, should be a number
* `id`, should be a non-null string
* `currency`, should be a 3 character currency code

This would be a minimal purchase track call:

```markup
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    { id: "order-1", amount: 55.45, currency: "USD" },
  ]);
</script>
```

### New customer tracking

If the purchase was made by a new customer, you can add this information to the tracking event. By default we will attempt to discover if the customer is to be considered a new customer. You may override that process by providing the `isNewCustomer` field.

```markup
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    { id: "order-1", amount: 55.45, currency: "USD", isNewCustomer: true },
  ]);
</script>
```

### Tracking purchase customer

Optionally, you can also track purchase's customer, in which case, the customer `id` and the customer's `email` would be required

```markup
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    {
      id: "order-1",
      amount: 55.45,
      currency: "USD",
      customer: {
        id: "customer-1",
        email: "jon.doe@example.com",
      },
    },
  ]);
</script>
```

### Tracking purchase products

Finally, you can also add the products being purchased, in which case, the product `sku`, `price` and `quantity` will be required and should be contained in an array. This would give you a rich purchase tracking event as such:

```markup
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    {
      id: "order-1",
      amount: 55.45,
      currency: "USD",
      customer: {
        id: "customer-1",
        email: "jon.doe@example.com",
      },
      products: [
        {
          name: "Cool Widget", // name is optional
          sku: "product-1",
          price: 20,
          quantity: 2,
        },
      ],
    },
  ]);
</script>
```

## Track Signup

To track a new subscription to your services, you may use the track `signup` call as follow:

```markup
<script>
  friendbuyAPI.push([
    "track",
    "sign_up",
    {
      email: "john.doe@example.com",
      name: "John",
      id: "customer-2",
    },
  ]);
</script>
```



