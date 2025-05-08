---
title: Toluna’s Server-to-Server API
nav_order: 0
has_children: true
---

# Introduction

This guide provides instructions for integrating Toluna's server-to-server API for member-survey status notifications. 

By leveraging Toluna's web service, clients can achieve:

- Seamless integration between the Client's system and Toluna's platform
- Enhanced data integrity by reducing fraudulent Survey Completions and improving Respondent Quality
- A one-time implementation process for long-term efficiency



---

## RESTful API for Member-Survey Status Notification

Toluna offers a RESTful API that allows clients to communicate the status of a Member-Survey upon its completion. This integration ensures accurate tracking and reporting of Survey outcomes. Learn more [here.](/s2sClientRedirectGuide/general/memberSurveyStatus.html)

## Member Start Validation

Clients may confirm if a particular Invite URL has been used by a member, while also retrieving the GID value of that Member's Response. Learn more [here.](/s2sClientRedirectGuide/general/memberStartValidation.html)

## Redirect URL

In addition to the API call, the Client should also redirect the member to the appropriate endpage as described [here](/s2sClientRedirectGuide/general/redirectingMember.html).



