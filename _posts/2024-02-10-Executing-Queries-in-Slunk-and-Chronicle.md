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

![Splunk1](/assets/images/Splunk1.jpg)

> I examined the fields created by Splunk indexes data. These fields become a part of the searchable index event data:

![Splunk2](/assets/images/Splunk2.jpg)

The following fields are observed:

- host: The host field indicates the name of the network host where the event originated.
- source: The source field specifies the file name where the event originated.
- sourcetype: The sourcetype field determines how the data is formatted.

I proceeded to use a query to investigate any failed SSH logins for the root account on the mail server: index = “main” host = “mailsv” fail* root

This query retrieves all events containing the word "fail" for the root user in the main index, specifically for events under the mailsv network host, where SSH logins are processed:

![Splunk3](/assets/images/Splunk3.png)

## Chronicle

**Scenario:**

You are a security analyst at a financial services company. You receive an alert that an employee received a phishing email in their inbox. You review the alert and identify a suspicious domain name contained in the email's body: signin.office365x24.com. You need to determine whether any other employees have received phishing emails containing this domain and whether they have visited the domain. You will use Chronicle to investigate this domain.

Given this scenario, I searched for the domain used in the phishing email:
