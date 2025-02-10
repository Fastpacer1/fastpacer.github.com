---
title: "Executing Queries in Splunk and Chronicles"
date: 2024-02-10T15:34:30-04:00
categories:
  - blog
tags:
  - Project
---

## Splunk

**Scenario:**

You are a security analyst working at the e-commerce store Buttercup Games. You've been tasked with identifying whether there are any possible security issues with the mail server. To do so, you must explore any failed SSH logins for the root account. 

Tasked with this scenario, I uploaded the provided log data into Splunk Cloud for analysis:
> I ran index="main" to confirm that the relevant data was ingested into the default index and is accessible for analysis. Additionally, I set the date range to "All time" to ensure all events, regardless of their timestamp, are included in the search:

![Splunk1](assets/images/Splunk1.png)
