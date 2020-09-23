# Visitor Status

> Format

```html
<script>
  friendbuyAPI.push(["getVisitorStatus", callback]);
</script>
```

> Example Invocation

```html
<script>
  friendbuyAPI.push([
    "getVisitorStatus",
    function (status) {
      console.log(status);
      // Do something based on the visitor status data
    },
  ]);
</script>
```

> Example responses

> Failed reward criteria

```json
{
  "status": "success",
  "payload": {
    "globalId": "dd61f81a-e590-4b69-b3b9-96a3c56238ea",
    "profileId": "155adb3c-196d-4f22-8e21-4e39c81ddc17",
    "customerId": "CUST01234",
    "attributionId": "278dcca0-fc4d-4ace-9e79-d8254b867ac7",
    "isSelfReferral": false,
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "advocateFirstName": "Britian",
    "advocateRewardInfo": {
      "requirementsFailed": [
        {
          "name": "new customer",
          "message": "Customer is known as 3078574637120, found matching purchase: 2112707199040"
        },
        {
          "name": "new customer",
          "message": "Customer is known as jeremy+test@friendbuy.com, found matching purchase: 2112707199040, 987398472938749, 780927840912740, 98279871294"
        },
        {
          "name": "new customer",
          "message": "Customer is known as jeremy+friend@friendbuy.com, found matching purchase: 2112710377536"
        }
      ],
      "integrationRequirementsFailed": [],
      "tiersCheckResult": {
        "conversionCount": 1,
        "tierIndex": 0,
        "nextTier": null,
        "tier": {
          "delivery": "codeBank",
          "couponBankId": "f299e6ca-0266-4a1e-8b0e-65fb9ef629b2",
          "rewardType": "discount"
        },
        "message": "Found a reward config for 1 conversions",
        "tierStatus": "pass"
      }
    }
  },
  "base64Payload": "eyJnbG9iYWxJZCI6ImRkNjFmODFhLWU1OTAtNGI2OS1iM2I5LTk2YTNjNTYyMzhlYSIsInByb2ZpbGVJZCI6IjE1NWFkYjNjLTE5NmQtNGYyMi04ZTIxLTRlMzljODFkZGMxNyIsImN1c3RvbWVySWQiOiJDVVNUMDEyMzQiLCJhdHRyaWJ1dGlvbklkIjoiMjc4ZGNjYTAtZmM0ZC00YWNlLTllNzktZDgyNTRiODY3YWM3IiwiaXNTZWxmUmVmZXJyYWwiOmZhbHNlLCJyZWZlcnJhbENvZGUiOiI4eXlrbW5zMyIsInJlZmVycmFsQ29kZUJsb2NrZWQiOmZhbHNlLCJhZHZvY2F0ZUZpcnN0TmFtZSI6IkJyaXRpYW4iLCJhZHZvY2F0ZVJld2FyZEluZm8iOnsicmVxdWlyZW1lbnRzRmFpbGVkIjpbeyJuYW1lIjoibmV3IGN1c3RvbWVyIiwibWVzc2FnZSI6IkN1c3RvbWVyIGlzIGtub3duIGFzIDMwNzg1NzQ2MzcxMjAsIGZvdW5kIG1hdGNoaW5nIHB1cmNoYXNlOiAyMTEyNzA3MTk5MDQwIn0seyJuYW1lIjoibmV3IGN1c3RvbWVyIiwibWVzc2FnZSI6IkN1c3RvbWVyIGlzIGtub3duIGFzIGplcmVteSt0ZXN0QGZyaWVuZGJ1eS5jb20sIGZvdW5kIG1hdGNoaW5nIHB1cmNoYXNlOiAyMTEyNzA3MTk5MDQwLCA5ODczOTg0NzI5Mzg3NDksIDc4MDkyNzg0MDkxMjc0MCwgOTgyNzk4NzEyOTQifSx7Im5hbWUiOiJuZXcgY3VzdG9tZXIiLCJtZXNzYWdlIjoiQ3VzdG9tZXIgaXMga25vd24gYXMgamVyZW15K2ZyaWVuZEBmcmllbmRidXkuY29tLCBmb3VuZCBtYXRjaGluZyBwdXJjaGFzZTogMjExMjcxMDM3NzUzNiJ9XSwiaW50ZWdyYXRpb25SZXF1aXJlbWVudHNGYWlsZWQiOltdLCJ0aWVyc0NoZWNrUmVzdWx0Ijp7ImNvbnZlcnNpb25Db3VudCI6MSwidGllckluZGV4IjowLCJuZXh0VGllciI6bnVsbCwidGllciI6eyJkZWxpdmVyeSI6ImNvZGVCYW5rIiwiY291cG9uQmFua0lkIjoiZjI5OWU2Y2EtMDI2Ni00YTFlLThiMGUtNjVmYjllZjYyOWIyIiwicmV3YXJkVHlwZSI6ImRpc2NvdW50In0sIm1lc3NhZ2UiOiJGb3VuZCBhIHJld2FyZCBjb25maWcgZm9yIDEgY29udmVyc2lvbnMiLCJ0aWVyU3RhdHVzIjoicGFzcyJ9fX0=",
  "signature": "ajKYw+By3o9TthxDUsOuTsmCzsvJVsLKVBIhQKvdnco="
}
```

> Passed reward criteria

```json
{
  "status": "success",
  "payload": {
    "globalId": "e3d60027-e176-41cd-9fc8-8e44bd2c0bfa",
    "profileId": "c95b77f5-c9a8-44eb-bff3-56b61febff2f",
    "customerId": "CUST01234",
    "attributionId": "964224f0-c22c-46eb-a0c4-6b20f11bddfb",
    "isSelfReferral": false,
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "advocateFirstName": "Britian",
    "advocateRewardInfo": {
      "requirementsFailed": [],
      "integrationRequirementsFailed": [],
      "tiersCheckResult": {
        "conversionCount": 1,
        "tierIndex": 0,
        "nextTier": null,
        "tier": {
          "delivery": "codeBank",
          "couponBankId": "f299e6ca-0266-4a1e-8b0e-65fb9ef629b2",
          "rewardType": "discount"
        },
        "message": "Found a reward config for 1 conversions",
        "tierStatus": "pass"
      }
    }
  },
  "base64Payload": "eyJnbG9iYWxJZCI6ImUzZDYwMDI3LWUxNzYtNDFjZC05ZmM4LThlNDRiZDJjMGJmYSIsInByb2ZpbGVJZCI6ImM5NWI3N2Y1LWM5YTgtNDRlYi1iZmYzLTU2YjYxZmViZmYyZiIsImN1c3RvbWVySWQiOiJDVVNUMDEyMzQiLCJhdHRyaWJ1dGlvbklkIjoiOTY0MjI0ZjAtYzIyYy00NmViLWEwYzQtNmIyMGYxMWJkZGZiIiwiaXNTZWxmUmVmZXJyYWwiOmZhbHNlLCJyZWZlcnJhbENvZGUiOiI4eXlrbW5zMyIsInJlZmVycmFsQ29kZUJsb2NrZWQiOmZhbHNlLCJhZHZvY2F0ZUZpcnN0TmFtZSI6IkJyaXRpYW4iLCJhZHZvY2F0ZVJld2FyZEluZm8iOnsicmVxdWlyZW1lbnRzRmFpbGVkIjpbXSwiaW50ZWdyYXRpb25SZXF1aXJlbWVudHNGYWlsZWQiOltdLCJ0aWVyc0NoZWNrUmVzdWx0Ijp7ImNvbnZlcnNpb25Db3VudCI6MSwidGllckluZGV4IjowLCJuZXh0VGllciI6bnVsbCwidGllciI6eyJkZWxpdmVyeSI6ImNvZGVCYW5rIiwiY291cG9uQmFua0lkIjoiZjI5OWU2Y2EtMDI2Ni00YTFlLThiMGUtNjVmYjllZjYyOWIyIiwicmV3YXJkVHlwZSI6ImRpc2NvdW50In0sIm1lc3NhZ2UiOiJGb3VuZCBhIHJld2FyZCBjb25maWcgZm9yIDEgY29udmVyc2lvbnMiLCJ0aWVyU3RhdHVzIjoicGFzcyJ9fX0=",
  "signature": "ZpQV4uZAPLl0hOdqsLpTen9AoWOcWqfGYI9VPFZbgR8="
}
```

Visitor Status returns relevant data we have captured around the current user.

The `callback` parameter in the `getVisitorStatus` command is a function that will receive an object containing the
visitor status `payload` and a verifiable `base64Payload` with a `signature` to verify the authenticity of the `base64Payload`.

### Verifying the Visitor Status Payload

You may wish to distribute rewards or do some other desirable action for the user based on their visitor status response.
The `base64Payload` contains the same data as the `payload`, base64 encoded. To prevent fraud you can verify the `base64Payload`
validates against the `signature` provided in the response. Then base64 decode the `base64Payload` and use that data to determine
the action you wish to perform.

Please see the section
<a href="#signature-validation">Signature Validation</a> for further instructions.
