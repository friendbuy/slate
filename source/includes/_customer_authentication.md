# Customer Authentication

> Code Samples

```html
<script>
  const epoch = Math.round(new Date().getTime() / 1000);
  const authString = epoch + ":" + customerEmail + ":" + customerUserId;
  // Example:  epoch + ":test@example.com:57ec28c3-0834-42cc-8522-9ed6dab0e04a";
  const signature = sha256.hmac(secretKey, authString);
  friendbuyAPI.push(["auth", authString, signature]);
</script>
```

```php
<?php
$customerEmail = 'customer@example.com';
$customerUserId = 'CUSTOMER123';
$secret = '[your friendbuy secret key]';
$epoch = time();
$authString = $epoch . ':' . $customerEmail . ':' . $customerUserId;
$signature = hash_hmac('sha256', $authString, $secret);
?>

<script>
const authString = "<?php echo $authString; ?>";
const signature = "<?php echo $signature; ?>";

window["friendbuyAPI"] = friendbuyAPI = window["friendbuyAPI"] || [];

friendbuyAPI.push(["auth", authString, signature]);
</script>

```

## **Summary**

Customer Authentication is an additional security measure that enables additional functionality for the end user within Friendbuy’s widgets and integrations. Note that Customer Authentication should only be done after a Customer has already been tracked by Friendbuy. Customer Authentication enables the following features:

- Loyalty Opt-In
- Ledger Transactions \(i.e. redemption of account credit, awarding credit for referrals\)
- Referral Dashboards in widgets
  - Includes listing referred friends and reward counts

## Instructions

1. In order to authenticate a customer, you will need to create an authentication string composed of the following separated by colons:
   - Current epoch time
   - Customer email
   - Customer id
2. You will then need to create an HMAC SHA256 signature from the authentication string using the Secret Key from your Friendbuy account.
   - **NOTE: Never expose your secret key on the frontend. The signature should be calculated by the backend and then passed to the frontend.**
3. Finally, track the authentication using the authentication string and the signature.

**Again, never expose your secret key, never calculate the signature on the front end.**
