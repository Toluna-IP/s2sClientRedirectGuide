---
title: Member-Start Validation
parent: General Overview
nav_order: 2
nav_enabled: true
---

# Member-Start Validation
{: .no_toc }

* TOC
{:toc}

---

## Request Structure

Below are detail on validating a Member has started a survey with a given GID. GID values should be captured from the Survey URL and included in the API call to Toluna.


{: .label .label-red }
Important

Ensure all API requests originate from the Client Server side and utilize HTTPS for secure communication.

### Route

```plaintext
POST https://{tolunaHost}/client/validate_survey_start 
```

### Parameters

| Name | Type | Description | Required? | 
| :--- | :--- | :--- | :---: |
| GID | ```guid``` | The unique identifier provided to the client as a URL parameter at the Survey's invitation | Yes |
| SurveyStartURL | ```string``` | The Survey URL exactly as directed by Touna into the Survey | No |

> Notes:
> - Using the GID without the SurveyStartURL will validate if the GID is tracked as a valid Start in Toluna.
> - Using GID and SurveyStartURL will validate the URL as it was redirected by Toluna and landed on the Survey.

### Headers

| Name | Type | Description | Required? |
| :--- | :--- | :--- | :---: |
| x-api-key | ```string``` | Client-specific key provided by Toluna. Contact your Toluna representative to obtain your key | Yes |

### Example Request

#### GID only

```plaintext
POST https://{tolunaHost}/client/validate_survey_start 
Header: x-api-key: {keyProvidedByToluna} 
{ 
    "Gid": "ec1e7622-6034-465b-a3c3-8d232abfe273" 
} 
```

#### GID and SurveyStartURL

```plaintext
POST https://{tolunaHost}/client/validate_survey_start 
Header: x-api-key: {keyProvidedByToluna} 
{ 
    "Gid": "ec1e7622-6034-465b-a3c3-8d232abfe273", 
  "SurveyStartURL": "https://www.dummysurvey.com/540812185541.aspx?gid=ec1e7622-6034-465b-a3c3-8d232abfe273&CSEX=2" 
} 
```

## Response

The response body will contain a status field and an Error Message

### Examples

```plaintext
{ 
    "Status": "Success" 
} 
```

```plaintext
{ 
    "Status": "Success", 
   "Gid": "ec1e7622-6034-465b-a3c3-8d232abfe273" 
} 
```