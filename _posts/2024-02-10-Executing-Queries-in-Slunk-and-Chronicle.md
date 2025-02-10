---
title: "Executing Queries in Splunk and Chronicles"
date: 2019-04-18T15:34:30-04:00
categories:
  - blog
tags:
  - Project
---
Executing Queries with Splunk and Chronicle

- Splunk

You are a security analyst working at the e-commerce store Buttercup Games. You've been tasked with identifying whether there are any possible security issues with the mail server. To do so, you must explore any failed SSH logins for the root account. 

Tasked with this scenario, I uploaded the provided log data into Splunk Cloud for analysis:
- I ran index="main" to confirm that the relevant data was ingested into the default index and is accessible for analysis. Additionally, I set the date range to "All time" to ensure all events, regardless of their timestamp, are included in the search:

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
