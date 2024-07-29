---
layout: default
title: "AI OPs"
---
# AI OPs


## What is AI OPs

[Hewlett Packard Enterprise says](https://www.hpe.com/emea_europe/en/what-is/aiops.html)

> AIOps, or artificial intelligence for IT operations, refers to use of artificial intelligence, such as machine learning (ML) and generative AI (GenAI), to automate the identification and resolution of common IT issues or improve operational efficiency


## Resources

### Github Projects

* [Opslane][opslane]
	* Alert Classification: Opslane can classify alerts as actionable or noisy using LLMs. We analyze alert history and Slack conversations to determine if an alert is actionable.
	* Slack Integration: Opslane operates in a Slack channel where a team receives alerts. We provide insights and additional resources for debugging actionable alerts.
	* Analytics: Opslane provides weekly reporting data for the quality of alerts in a Slack channel. We analyze the pattern of alerts and provide an option to silence noisy alerts directly from Slack.
	* Open Source: Opslane is open source and welcomes contributions from the community.

[opslane]: https://github.com/opslane/opslane


### YouTube

* [Effective AIOps with Open Source Software in a Week](https://youtu.be/NuL1u_CIkQw?si=v-sXy3pBFF1UDIct)
	* > Classic event, incident, problem and change management are ITSM practices that are getting integrated with DevOps/SRE and ML through a competency known as AIOps. Large streams of data generated through logs, metrics and traces are organized and computed using machine learning algorithms to extract insights on the anomalies of system behavior that could be impacting end-users and business transactions. Businesses cannot afford to see their end-users impacted by those anomalies and therefore would want to proactively predict the likelihood of systems regressing and take corrective action long before any material impact.
	> 
	> In this talk, we show the use of simple linear regression and multivariate linear regression techniques to predict the likelihood of system behavior resulting in one or two sigma of standard deviation. We show how to use FOSS tools to predict them using various decision trees that are integrated to high performing streaming platforms like Apache Flink, Apache Beam, Prometheus and Grafana which makes it a lot easier to visualize the various alerts and triage their way back to performing root cause analysis. These high performing systems are also backed by KAFKA for its streaming and distributed computing capabilities by partitioning the data for various staged analysis some of which can be done in parallel and concurrently based on the use cases. We present a fully integrated architecture that helps you realize a commercial AIOps capability without having to license expensive software products. The above open architecture allows you to implement various ML algorithms as needed and its agnostic to programming languages and tools.
	> 
	> The talk will combine various techniques with demos and is focused to practicing engineers and developers who are familiar with ML.