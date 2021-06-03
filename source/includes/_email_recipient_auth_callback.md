# Email Recipient Authorization Callback

## Overview

The Email Recipient Authorization Callback allows you to block the sending of a share email based on the recipient's email address. This allows you to apply your own email opt-out rules on top of Friendbuy's unsubscribe system.

## Request Payload

When an advocate shares an offer with a friend via the email channel, Friendbuy sends an email to the friend on the advocate's behalf. Before actually sending the email, Friendbuy checks to see whether the friend has previously opted-out of receiving share emails and, if so, the email is not sent. If you have configured an Email Recipient Authorization Callback for your account then, after an email has passed all of Friendbuy's internal checks, we will make an HTTP POST request to the URL you have provided. The body of the request will contain a list of email addresses, as described below.

> Example Payload

```json
{
  "id": "4ac0e132-d1d7-4dc1-963f-dfaf9763594c",
  "type": "emailAuth",
  "data": [
    "allowed.friend@example.com",
    "blocked.friend@example.com"
  ],
  "createdOn": "2021-06-01T14:28:14.794Z"
}
```

| Property  | Type             | Description                                                       |
|:----------|:-----------------|:------------------------------------------------------------------|
| id        | string           | A unique ID for the request. Useful for troubleshooting.          |
| type      | "emailAuth"      | Indicates that this is an Email Recipient Authorization callback. |
| data      | array of strings | An array of recipient email addresses.                            |
| createdOn | ISO timestamp    | The time the request was sent.                                    |

## Response Payload

> Example Response

```json
["allowed.friend@example.com"]
```

Friendbuy expects the response to the email recipient authorization callback to be a list of the allowed email addresses. The share emails for recipients in the returned list of allowed email addresses will be sent, and the share emails to recipients not in the returned list will be blocked.

### Retry Behavior

If the Email Recipient Authorization Callback fails or if it receives a failure response, the sending of those share emails will be temporarily blocked and the callback will be retried later, on Friendbuy's email retry schedule. The delay between tries is 10 minutes, 5 hours, 40 hours, 7 days, and 22 days. If, after six tries the callback is still failing, the emails will not be sent.
