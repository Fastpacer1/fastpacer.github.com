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

![Splunk1](https://github.com/Fastpacer1/fastpacer.github.com/blob/d651e9644f44799302e7696673b9629abe15f48a/assets/images/Splunk1.png)

> I examined the fields created by Splunk indexes data. These fields become a part of the searchable index event data:

"assets/images/Splunk2.jpg"

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

![Chronicle1](/assets/images/Chronicle 1.png)

I proceeded to evaluate the search results in Chronicle for the identified domain: 

![Chronicle2](/assets/images/Chronicle2.png)

- VT Context: This Section provides the VirusTotal information that is available for the domain.
- WHOIS: This section summarizes information about the domain using WHOIS, a free public directory that provides details about registered domain names, including the domain owner’s name and contact information.
- Prevalence: This section includes a graph that outlines the historical prevalence of the domain. 
- RESOLVED IPS: This section provides additional context about the domain, including the IP address mapped to signin.office365x24.com, which resolved to 40.100.174.34.
- SIBLING DOMAINS: This section provides additional context about the domain. Sibling domains share a common top-level or parent domain. In this case login.office365x24.com shares the same parent domain, office365x24.com, with the domain under investigation, -signin.office365x24.com.
- TIMELINE: This section shows information regarding events and interactions made with this domain
- ASSETS: This section provides a list of the assets that have accessed the domain

I clicked on VT CONTEXT to evaluate the available VirusTotal information about this domain. 10 security vendors flagged the domain as malicious:

![Chronicle3](/assets/images/Chronicle3.png)

I then proceeded to investigate the top level domain by performing a new search:

![Chronicle4](/assets/images/Chronicle4.png)

The VirusTotal for the top domain also returned 5 vendors marking the domain as malicious: 

![Chronicle5](/assets/images/Chronicle5.png)

Using the TIMELINE tab, I identified the POST request, indicating that data was sent to the malicious domain. This suggests a potential successful phishing attempt:

![Chronicle6](/assets/images/Chronicle6.png)

Following this, I checked the resolved IP address for POST requests, here we can see three different employees sent POST requests suggesting there was a successful phishing attempt:

![Chronicle7](/assets/images/Chronicle8.png)

**Reflection**

In this Security Investigation, I used Splunk and Chronicle to investigate security threats in two different scenario

