---
title: Member-Survey Status
parent: Toluna’s Server-to-Server API
nav_order: 1
nav_enabled: true
---

# Member-Survey Status Notification
{: .no_toc }

These Notifications are used to securely inform Toluna of a Member's end-status within a Survey. In addition to sending these calls, the Client should also redirect the member to the appropriate endpage as described [here](/s2sClientRedirectGuide/servertoserver/redirectingMember.html).

> IMPORTANT
>
> Ensure all API requests originate from the Client Survey side and utilize HTTPS for secure communication

* TOC
{:toc}

---

## Request Structure

### Route

```plaintext
POST https://{tolunaHost}/client/survey_end 
```

### Request Parameters

| Name | Type | Description | Required? | 
| :--- | :--- | :--- | :---: |
| GID | ```guid``` | The unique identifier provided to the client as a URL parameter at the Survey's invitation | Yes |
| Status | ```string``` | The Survey Completion status on the Client side. Must be one of the following: Terminated / Screened, Qualified / Complete, QuotaFull, QualityTermination | Yes |

### Headers

| Name | Type | Description | Required? |
| :--- | :--- | :--- | :---: |
| x-api-key | ```string``` | Client-specific key provided by Toluna. Contact your Toluna representative to obtain your key | Yes |

### Example Request

```plaintext
POST https://{tolunaHost}/client/survey_end 
Header: x-api-key: {keyProvidedByToluna}

{
    "Gid": "5b866e17-c829-45e2-b065-e93b2580d4b3",
    "CompletionStatus":"complete"
}
```

## Response

The response will contain a Status field and a Redirect URL

### Example Response

```plaintext
{
    "Status": "Success",
    "RedirectUrl": "https://{tolunaHost}/TrafficUI/MSCUI/SOQualified.aspx?gid=8b6f35dc-ca6a-429e-a5ff-3bd281e4d8b9"
}
```