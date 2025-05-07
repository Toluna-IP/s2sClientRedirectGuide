---
title: Redirecting Members
parent: General Overview
nav_order: 3
nav_enabled: true
---

# Redirection of Members

In conjunction with the Member-Survey status Notification, Members should be redirected to the appropriate Toluna end URL. This redirection should occur simultaneously with the API call.

The URL used would be determined according to the status:
- Qualification: https://ups.surveyrouter.com/TrafficUI/MSCUI/SOQualified.aspx?GID=[GID]
- Termination / Quality Termination: https://ups.surveyrouter.com/TrafficUI/MSCUI/SOTerminated.aspx?GID=[GID]
- QuotaFull: https://ups.surveyrouter.com/TrafficUI/MSCUI/SOQuotafull.aspx?GID=[GID] 

Each of these URLs can also include Encryption Data for additional security and validations. Instructions for encryption can be found [here](/encryption).