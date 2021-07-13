# Tracking Events

## Tracking Call API

> Example Track Call

```html
<script>
  friendbuyAPI.push([
    "track", // this is a track event
    "email_capture", // this is an event capture event
    {
      email: "john.doe@example.com", // the email
      name: "John Doe", // the name (optional)
      age: 55, // the age (custom parameter)
    },
    true, // Send custom parameters to friendbuy
  ]);
</script>
```

Friendbuy comes with some built-in event tracking settings:

- `email_capture`
- `customer`
- `purchase`
- `product`
- `page`
- `sign_up`

This only means that when you are tracking these events, you are bound to respect a given format. You can also define your own custom event which won't have any restrictions.

### Event Metadata

> Example Metadata

```json
{
  "metadata": {
    "title": "Welcome to Foo Store - Account page",
    "name": "account page",
    "url": "https://www.foo-store.com/account/user-1234",
    "widgetDisplayName": "widget foo bar baz",
    "origin": "https://www.foo-store.com",
    "pathname": "/account/user-1234"
  },
  "payload": {
    "type": "foo",
    "name": "bar"
  }
}
```

Every event sends the metadata of the current state. The metadata contains:

- Page title
- Page name \(through the track page event\)
- the name of the widget \(under `widgetDisplayName` when relevant\)
- the page URL
- The origin of the track call (the base domain of the url)
- The pathname of the track call (the path of the url)

An example of metadata format is to the right:

### Event Profile

All events must have a profile associated with them. The merchant SDK will always postpone events until a profile has been retrieved from friendbuy's backend.

More information about profile in the attribution documentation \(information may not be disclosed in this documentation\)

### Event Routing

This is the journey of an event \(up to our backend public API\).

1. An event is generated in the integration library.
2. If an event is considered "controlled" \(`purchase`, `email_capture` ...\) the event is validated.
3. The signed profile is added to the event request \(we use pixel tracking\).
4. The event is sent to the public endpoint of our backend.

## Event rules by type

### Email Capture Event

> Email Capture Code Sample

```html
<script>
  friendbuyAPI.push([
    "track",
    "email_capture",
    { email: "john.doe@example.com" },
  ]);
</script>
```

> Email Capture with Optional Name Parameter

```html
<script>
  friendbuyAPI.push([
    "track",
    "email_capture",
    {
      email: "john.doe@example.com",
      name: "John",
    },
  ]);
</script>
```

> Email Capture Custom Parameter Example

```html
<script>
  friendbuyAPI.push([
    "track",
    "email_capture",
    {
      email: "john.doe@example.com",
      subscribed: "yes", // custom parameter
    },
    true, // Send custom parameters to friendbuy
  ]);
</script>
```

| Attribute | Type   | Required | Example                  |
| :-------- | :----- | :------- | :----------------------- |
| `email`   | string | **yes**  | `"john.doe@example.com"` |
| `name`    | string | no       | `"John Doe"`             |

The only required field for an email capture event is the `email` field. A minimal email capture event is defined as followed:

All events accept additional information but these additional information will not be sent to friendbuy backend unless requested during the tracking call. If you want additional data to be sent to friendbuy, you'll have to add the boolean `true` to the list of argument passed to track as followed:

This last `true` parameter will indicate to the merchant SDK that any additional custom fields you would like to track \(in this case `subscribed`\) need to be added to the event payload. This can be useful for example if a reward configuration requires additional information not provided by the event by default.

### Customer Event

> Minimal Customer Payload

```json
{
  "id": "customer-123",
  "email": "john.doe@example.com"
}
```

> Complete Customer Payload

```json
{
  "id": "customer-123",
  "email": "john.doe@example.com",
  "firstName": "John",
  "lastName": "Doe",
  "isNewCustomer": false,
  "customerSince": "2020-06-12T17:58:44.000Z",
  "age": 26
}
```

> Customer Payload with Custom Parameters

```html
<script>
  friendbuyAPI.push([
    "track",
    "customer",
    {
      email: "john.doe@example.com",
      id: "customer-123",
      name: "John",
      category: "vip",
    },
    true,
  ]);
</script>
```

>

| Attribute       | Type    | Required | Example                                  |
| :-------------- | :------ | :------- | :--------------------------------------- |
| `id`            | string  | **yes**  | `"c42526a0-86bb-4b2b-8015-3c88e5502fb3"` |
| `email`         | string  | **yes**  | `"john.doe@example.com"`                 |
| `name`          | string  | no       | `"John Doe"`                             |
| `firstName`     | string  | no       | `"John"`                                 |
| `lastName`      | string  | no       | `"Doe"`                                  |
| `isNewCustomer` | boolean | no       | `false`                                  |
| `customerSince` | string  | no       | `"2020-06-12T17:58:44.000Z"`             |
| `age`           | integer | no       | 26                                       |

You can track a customer using the track customer endpoints. Track customer requires a least both an `id` and a valid `email`. You may also add the `isNewCustomer` information.

If you want to provide additional information you must add the boolean `true` as last argument

### Purchase Event

>

> Minimal Purchase Payload

```html
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    {
      id: "order-123",
      amount: 57.87,
      currency: "USD",
    },
  ]);
</script>
```

> Detailed Purchase Payload

```html
<script>
  friendbuyAPI.push([
    "track",
    "purchase",
    {
      id: "order-123",
      amount: 57.87,
      currency: "USD",
      isNewCustomer: true,
      couponCode: "abc-123",
      customer: {
        email: "john.doe@example.com",
        name: "John Doe",
        id: "customer-123",
        category: "vip",
        age: 32,
        customerSince: "2020-06-12T17:58:44.000Z",
      },
      products: [
        { sku: "PLU-8542", quantity: 4, price: 5.54, name: "flowers" },
        { sku: "PLU-8751", quantity: 3, price: 9.48, name: "chocolates" },
      ],
    },
  ]);
</script>
```

| Attribute       | Type    | Required | Example                  |
| :-------------- | :------ | :------- | :----------------------- |
| `id`            | string  | **yes**  | `"ORD-4586"`             |
| `amount`        | number  | **yes**  | `55.50`                  |
| `currency`      | string  | **yes**  | `"USD"`                  |
| `isNewCustomer` | boolean | no       | `false`                  |
| `couponCode`    | string  | no       | `"abcd1234"`             |
| `giftCardCodes` | array   | no       | `["abc-123", "xyz-456"]` |

Purchase accepts a sub-attribute `customer`. The required fields below are only required if customer data is provided.

| Customer sub-attribute   | Type    | Required | Example                      |
| :----------------------- | :------ | :------- | :--------------------------- |
| `customer.id`            | string  | _yes_    | `"CUST-3821"`                |
| `customer.email`         | string  | _yes_    | `"john.doe@gmail.com"`       |
| `customer.name`          | string  | _yes_    | `"John Doe"`                 |
| `customer.isNewCustomer` | boolean | _no_     | false                        |
| `customer.customerSince` | string  | _no_     | `"2020-06-12T17:58:44.000Z"` |
| `customer.age`           | integer | _no_     | `26`                         |

and a sub-attribute `products` \(as an array of objects\)

| Products sub-attribute    | Type   | Required | Example                                    |
| :------------------------ | :----- | :------- | :----------------------------------------- |
| `products[0].sku`         | string | no       | `"PLU-8324-187"` or default to `"unknown"` |
| `products[0].name`        | string | no       | `"Yellow Jacket`                           |
| `products[0].quantity`    | number | _yes_    | `5`                                        |
| `products[0].price`       | number | _yes_    | `28.99`                                    |
| `products[0].description` | string | _no_     | `"Test Product"`                           |
| `products[0].category`    | string | _no_     | `"Apparel"`                                |
| `products[0].url`         | string | _no_     | `"https://example.com/apparel"`            |
| `products[0].imageUrl`    | string | _no_     | `"https://example.com/images/1234"`        |

Purchase event are the most common conversions.

### Product Event

>

> Minimal Product Format

```json
{
  "sku": "sku-123",
  "name": "Potatoes"
}
```

> Minimal Product Payload Example

```html
<script>
  friendbuyAPI.push(["track", "product", { sku: "sku-123", name: "Potatoes" }]);
</script>
```

> Detailed Product Payload Example

```html
<script>
  friendbuyAPI.push([
    "track",
    "product",
    {
      sku: "sku-potats",
      name: "Potatoes",
      price: 0.51,
      currency: "USD",
      category: "vegetables",
      url: "https://www.example.com/product/potats",
      imageUrl: "https://static.example.com/mr-potatoe.jpg",
    },
  ]);
</script>
```

| Attribute     | Type   | Required         | Example                                           |
| :------------ | :----- | :--------------- | :------------------------------------------------ |
| `sku`         | string | **yes**          | `"PLU-846871"`                                    |
| `name`        | string | **yes**          | `"Yogurt"`                                        |
| `price`       | number | no               | `10.52`                                           |
| `currency`    | string | _yes_ if `price` | `"USD"`                                           |
| `category`    | string | no               | `"dairy"`                                         |
| `url`         | string | no               | `"https://www.example.com/product/846871"`        |
| `imageUrl`    | string | no               | `"https://static.example.com/product-846871.jpg"` |
| `description` | string | no               | `"Plain yogurt"`                                  |

We allow a merchant to capture a product view using this controlled event capture method.

### Page Event

>

> Example Page Event

```html
<script>
  friendbuyAPI.push(["track", "page", { name: "user account" }]);
</script>
```

| Attribute | Type   | Required | Example          |
| :-------- | :----- | :------- | :--------------- |
| `name`    | string | **yes**  | `"product page"` |

Page event allows you to track the page name. The page name simplifies targeting vs URLs which often requires wildcards. A page event payload only requires a `name`

### Sign Up Event

> Example Sign Up Event

```html
<script>
  friendbuyAPI.push([
    "track",
    "sign_up",
    {
      email: "john.doe@example.com",
      id: "user-123",
      age: 40,
    },
  ]);
</script>
```

| Attribute | Type    | Required | Example                  |
| :-------- | :------ | :------- | :----------------------- |
| `id`      | string  | **yes**  | `"CUST-8348"`            |
| `email`   | string  | **yes**  | `"john.doe@example.com"` |
| `name`    | string  | no       | `"John"`                 |
| `age`     | integer | no       | `40`                     |

When a user creates an account, you can register this event using the `sign_up` event type. Note that a signup event will consider the user to be a new user \(as opposed to a [track customer event](customer-event)\). The controlled fields for a sign up event are `id`, `email`, `name`, `campaignId`.

### Custom Event

> Example Custom Event

```html
<script>
  friendbuyAPI.push([
    "track",
    "video-viewed",
    {
      id: "welcome-new-user-video",
      userId: "user-123",
      email: "john.doe@example.com",
      deduplicationId: "user-123:welcome-new-user-video",
    },
  ]);
</script>
```

In addition to the previous "controlled" events, you may decide to add your own custom event. For example you could trigger a "video viewed" custom event at the end of a marketing video or "survey taken" at the end of a quiz.

Note that a custom event will always send all the information it receives.

When creating a custom event, we strongly recommend
passing in a unique `deduplicationId`. This property must be a string.  We will not reward any subsequent custom events with the same type and `deduplicationId`.  You can use any string you prefer as the `deduplicationId`, as long as it is unique. You should pick a unique identifier approriate to the event you are tracking. 
