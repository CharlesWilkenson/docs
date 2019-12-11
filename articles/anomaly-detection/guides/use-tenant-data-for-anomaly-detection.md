---
title: Use Tenant Traffic Data for Anomaly Detection
description: Learn how to use tenant logs to build charts for anomaly detection on the traffic going through your tenant. 
topics:
    - security
    - anomaly-detection
contentType: how-to
useCase: tenant-logs
---

# Use Tenant Traffic Data for Anomaly Detection

The tenant logs contain a number of useful data that you can use to build charts to look at the profile of the traffic going through your tenant.  

## Use event log data to see failure events

You can use the log data `event` field to view the tenant traffic data. We recommend building a daily histogram of failure events, those of the following types:

| Event Code | Event |
| -- | -- |
| `f` | Failed login |
| `fcoa` | Failed cross-origin authentication |
| `feccft` | Failed exchange |
| `fepft` | Failed exchange |
| `fsa` | Failed silent authentication |
| `fu` | Failed login (invalid email/username) |
| `sepft` | Success exchange |

These failure events depend on the flow you have set up with Auth0. 

The following example shows a credential stuffing attack on 11/20, with a large surge of events of type `fu` which is a failed username (typical of a credential stuffing attack).

![Traffic Failure Trends](/media/articles/anomaly-detection/traffic-failure-trends.png)

## Use `ip` to see failure events from distinct IPs 

You can use the `ip` event to see the number of distinct IPs that your failure traffic is coming from, in this case, the number of distinct IPs that correspond to your `fu` event traffic.

## Use event log data to see anomaly detection events

You can perform the same type of analysis with the events corresponding to anomaly detection events to see how many times they are triggered. Use the following log events which correspond to brute force detection with many accounts, one account, and breached password detection:

| Event Code | Event |
| -- | -- |
| `limit_mu` | Blocked IP address |
| `limit_wc` | Blocked account |
| `pwd_leak` | Breached password |

Here's an example of what that data might look like.

![Anomaly Detection Data](/media/articles/anomaly-detection/anomaly-detection-features.png)

## Keep reading

* [Log data event listing](/logs#log-data-event-listing)