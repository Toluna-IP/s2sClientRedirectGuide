---
title: URL Signature and Validation
nav_order: 1
has_children: false
nav_exclude: true
search_exclude: true
---

# Introduction
{: .no_toc }

To enhance the security and integrity of survey URLs, Toluna provides a mechanism for signing Survey start URLs and validating the Complete redirect URLs. Clients can choose to implement encryption on either the Start link or Complete Redirect - or both. Below you will find steps for Clients to integreate and utilize this feature effectively. 


* TOC
{:toc}


## Survey Start URL Signature

When a Member initiates a Survey, Toluna signs the Survey start URL using the HMAC SHA256 algorithm and a Client-specific key. The resulting Signature is appended as an additional parameter to the URL. The value of the parameter can be utilized by Clients to verify the URL's authenticity and ensure it has not been tampered with. 

### Signature Details

Toluna will encrypt the Suvey Start URL
- Encryption Method: HMAC SHA256 with Client-specific key
- Output Format: HEX, set to UPPERCASE
- Parameter Name: TolunaStartEnc
- Verification: Clients should verify the URL (excluding the "TolunaStartEnc" parameter)

### Implementation

The URL used by Members to start the Survey will include the "TolunaStartEnc" parameter

1. Validation: Clients should validate the URL (excluding the "TolunaStartEnc" parameter) using HMAC SHA256 with the provided key)
2. Output Format: Ensure the Signature output is in HEX and set to UPPERCASE
3. Comparison: Compare the signed result with the "TolunaStartEnc" parameter to ensure the URL's integrity

### Example


| :--- | :--- |
| Original URL | https://www.survey.com/survey/selfserve/53b/g004/231268?list=494&supplier_id=494&idtype=0&country=US&decLang=english&ID=1000001&sname=qp4lYkBILSpbVy11yCf9RayJ1-I&IDS=1000001 |
| Key | 239494365 |
| URL With Signature | https://www.survey.com/survey/selfserve/53b/g004/231268?list=494&supplier_id=494&idtype=0&country=US&decLang=english&ID=1000001&sname=qp4lYkBILSpbVy11yCf9RayJ1-I&IDS=1000001&TolunaStartEnc=EBEDA7E495B2B5F499989CE5086494DA223B256B57457C3858A16666A2414BA5 |


## Complete Redirect URL Validation

When redirecting back to Toluna, clients can sign the redirect URL using a per survey key and append the hashed result. Toluna will validate this hashed value to confirm the URL's integrity.

### Signature Details

The Redirect URL from the Client back to Toluna should be signed by the Client
- Signing Method: HMAC SHA256 with a Client-specific key
- Output Format: HEX, set to UPPERCASE
- Parameter: The signature should be appended as "&TolunaENC="
- Validation: Toluna will validate the hashed value by signing the same URL and comparing results

### Implementation

These step should be implemented by the Client

1. URL Construction: Construct the Redirect URL to Toluna based on the Redirect URLs provided [here](/servertoserver/redirectingMember.html).
2. Signing: Sign the URL using HMAC SHA256 with the provided, Client-specific key
3. Output Format: Ensure the output is in HEX format and set to UPPERCASE
4. Parameter Addition: Append the result to the Redirect URL as the "TolunaENC" parameter
5. Redirection: Redirect the User to the constructed URL
6. Exact Signing: Sign the URL exactly as it is, without alertation

### Example

| :--- | :--- |
| Original URL | https://ups.surveyrouter.com/TrafficUI/MSCUI/SOQualified.aspx?sname=Kp3xAWQXdik2djVhX7uJBGOlfk8&gid=10001 |
| Key | 232594365 |
| URL with Signature | https://ups.surveyrouter.com/TrafficUI/MSCUI/SOQualified.aspx?sname=Kp3xAWQXdik2djVhX7uJBGOlfk8&gid=10001&TolunaENC=50CEB0FC667A97B993A0BFD1496B84552392A7A1EBADB910D7E083ED9F5BDA72 |