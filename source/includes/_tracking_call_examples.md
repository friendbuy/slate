# Tracking Call Examples

## Tracking Customer

> Tracking Customer Example

```javascript
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
```

You may provide the customer's information on the widget using a track customer call. This reduces friction during the sharing process by pre-filling these fields in the widget.

## Tracking email

> Tracking Email Example

```javascript
<script>
  friendbuyAPI.push([
    "track",
    "email",
    { email: "john.doe@example.com" },
  ]);
</script>
```

If you were to only know the email of the visitor, you can use the track email command which only requires an email to be captured.

## Tracking Pages

> Tracking Page Example

```javascript
friendbuyAPI.push(["track", "page", { name: "home" }]);
```

You can name your pages to simplify widget display triggers and analytics. To do so, make sure the page you want to track includes the merchant SDK integration code above.

We recommend naming pages like "product", "homepage", "post-purchase"

## Tracking Purchase

> Tracking Purchase Example

```javascript
friendbuyAPI.push([
  "track",
  "purchase",
  { id: "order-1", amount: 55.45, currency: "USD" },
]);
```

Tracking a purchase requires a few mandatory fields:

- `amount`, should be a number
- `id`, should be a non-null string
- `currency`, should be a 3 character currency code

This would be a minimal purchase track call:

### New customer tracking

> Purchase with New Customer Example

```javascript
friendbuyAPI.push([
  "track",
  "purchase",
  { id: "order-1", amount: 55.45, currency: "USD", isNewCustomer: true },
]);
```

If the purchase was made by a new customer, you can add this information to the tracking event. By default we will attempt to discover if the customer is to be considered a new customer. You may override that process by providing the `isNewCustomer` field.

### Tracking purchase customer

> Purchase with Customer Example

```javascript
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
```

Optionally, you can also track purchase's customer, in which case, the customer `id` and the customer's `email` would be required

### Tracking purchase products

> Purchase with Products Example

```javascript
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
```

Finally, you can also add the products being purchased, in which case, the product `sku`, `price` and `quantity` will be required and should be contained in an array. This would give you a rich purchase tracking event as such:

## Track Signup

> Track Signup Example

```javascript
friendbuyAPI.push([
  "track",
  "sign_up",
  {
    email: "john.doe@example.com",
    name: "John",
    id: "customer-2",
  },
]);
```

To track a new subscription to your services, you may use the track `signup` call.
