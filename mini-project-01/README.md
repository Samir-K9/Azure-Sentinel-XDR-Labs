# Mini Project 01 — SOC Foundations with Sentinel & Defender

**Tools Used:**  Microsoft 365 Admin Centre · Microsoft Azure · Microsoft Sentinel · Microsoft Defender XDR · Log Analytics Workspace 
**Focus:** Environment setup, log ingestion, threat detection, .and foundational SOC configuration

---

## Overview

This project documents the full setup of a cloud-based SOC lab environment using Microsoft Azure, Sentinel, and Defender XDR. Starting from account creation through to log ingestion, detection rules, workbooks, and incident investigation.

---

## Table of Contents

1. [Sign Up for Office 365 E5 Trial (No Teams)](#1-sign-up-for-office-365-e5-trial-no-teams)
2. [Assign Microsoft 365 E5 Licence to Your User](#2-assign-microsoft-365-e5-licence-to-your-user)
3. [Create a Microsoft Azure Portal Account](#3-create-a-microsoft-azure-portal-account)
4. [Set Up a Billing Alert in Azure](#4-set-up-a-billing-alert-in-azure)
5. [Create a Log Analytics Workspace](#5-create-a-log-analytics-workspace)
6. [Set Up Microsoft Sentinel](#6-set-up-microsoft-sentinel)
7. [Export Activity Logs from Azure Subscription to Log Analytics Workspace](#7-export-activity-logs-from-azure-subscription-to-log-analytics-workspace)
8. [Install AzureActivity Solution from Content Hub](#8-install-azureactivity-solution-from-content-hub)
9. [Install Microsoft Sentinel Training Lab Solution](#9-install-microsoft-sentinel-training-lab-solution)
10. [Create a Microsoft Sentinel Workbook](#10-create-a-microsoft-sentinel-workbook)
11. [Install Microsoft Defender XDR Data Connector](#11-install-microsoft-defender-xdr-data-connector)
12. [Create a Detection Rule for Brute Force Attacks](#12-create-a-detection-rule-for-brute-force-attacks)


---

## Steps

### 1. Sign Up for Office 365 E5 Trial (No Teams)

Signed up for the Office 365 (no Teams) E5 trial, which activates a Microsoft 365 E5 trial license. This license includes access to Microsoft Defender for Endpoint and Microsoft Defender for Office 365 which are both essential for building out the detection and response capabilities used throughout this lab.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/e827e19335fc03c1aef943cd5ef8b839163defed/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20114713.png)

---

### 2. Assign Microsoft 365 E5 Licence to Your User

Assigned the Microsoft 365 E5 licence to my user account in the Microsoft 365 admin centre. This activates the full suite of security features under that account, including Microsoft Defender for Endpoint and Defender for Office 365, which are required for the lab environment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/54ed9977c486c3d334af3d85e4d2a1c7de0b926e/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20115948.png)

---

### 3. Create a Microsoft Azure portal account

Created a Microsoft Azure portal account with a free trial. This links the Azure environment to the existing Microsoft 365 tenant, allowing resources like Log Analytics Workspace and Microsoft Sentinel to be deployed and connected to the security tools already configured in the Microsoft 365 admin centre.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/4d9ae558838250b4427ed21d5ca971d7d015fe84/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20120547.png)

---

### 4. Set Up a Billing Alert in Azure

Configured a billing alert in the Azure Cost Management portal to monitor spending and avoid unexpected charges during the lab. Set a budget threshold so an email notification is triggered if costs approach the defined limit.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/c547ca00972c2f7669dee5d97a79a1a3934dcbb7/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20121112.png)

---

### 5. Create a Log Analytics Workspace

Created a Log Analytics Workspace in the Azure portal. This serves as the central data store where all logs and security events are collected, stored, and queried. Microsoft Sentinel is built on top of the Log Analytics Workspace, making this a foundational step before any detection or monitoring can be configured.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/405f12d26e3eab881ec977ae8f2e29f19b1126bb/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20121711.png)

---

### 6. Set Up Microsoft Sentinel

Deployed Microsoft Sentinel and connected it to the Log Analytics Workspace created in the previous step. Sentinel acts as the SIEM and SOAR solution for this lab, providing a centralised platform for threat detection, incident investigation, and automated response across the environment.

> [!NOTE]
> Microsoft Sentinel has migrated to the Microsoft Defender portal. All Sentinel features including incidents, analytics rules, and workbooks are now accessible directly within the unified Defender portal, bringing SIEM and XDR capabilities together in a single interface.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/8d1f44715102abbff8fdecccafc6bfbc194f3354/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20122426.png)

---

### 7. Export Activity Logs from Azure Subscription to Log Analytics Workspace

Exported the Azure subscription's activity logs to the Log Analytics Workspace. Specifically administrative, security and alert logs were ingested.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/56cc2083e5f4df758dfc9dcdb751f161f37b6f97/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20105814.png)


---

### 8. Install AzureActivity Solution from Content Hub

Installed the AzureActivity solution from the Content Hub in Microsoft Sentinel.This will enable the logs that we wanted to be exported from the Azure to be ingested into Microsoft Sentinel through pre-built data connectors, analytics rules, and workbooks specifically designed to monitor and detect threats based on Azure subscription activity logs.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/1909ea4991e7152046e003f1695ab38556b47b16/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20110736.png)

---

### 9.  Install Microsoft Sentinel Training Lab Solution

Installed the Microsoft Sentinel Training Lab solution from the Azure portal. This deploys a set of pre-configured sample data, analytics rules, incidents, and workbooks designed specifically for hands-on learning into detection and investigating simulating a real-world production environment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/ccb96c9d2e3bfde3745967206293e63b3e2c4d5a/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20111946.png)


---

### 10. Create a Microsoft Sentinel Workbook

Created a custom Microsoft Sentinel Workbook to visualise key authentication activity across the environment, including failed logins by account, successful logins by computer, and sign-in activity by location. This provides a centralised view for monitoring access patterns and identifying suspicious behaviour.


![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/bb24151d8bade3b2b63aefd26e4192ef9813d995/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20113544.png)
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/bb24151d8bade3b2b63aefd26e4192ef9813d995/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20113643.png)
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/bb24151d8bade3b2b63aefd26e4192ef9813d995/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20113702.png)

---

### 11. Install Microsoft Defender XDR Data Connector

Installed the Microsoft Defender XDR data connector in Microsoft Sentinel to integrate alerts and incidents from Defender XDR into the Sentinel environment. For this lab, Microsoft Defender Alerts were selected so that it brings Defender alerts and associated evidence directly into Sentinel for investigation. This includes alerts from endpoint, office 365, cloud app security and identity platforms.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/6fd5a47bda04ab66b893352f6ea5b983ecba9841/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20120256.png)


![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/d6827ef2eee5f37a14a7fdb067de908ad4847d98/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20115515.png)

### 12.  Create a Detection Rule for Brute Force Attacks

Created an analytics rule in Microsoft Sentinel using the sample data provided by the Training Lab solution to test and validate detection logic in the lab environment.
The rule queries the SecurityEvent_CL table for Event ID 4625 (failed logon), summarises the count by account, and triggers an alert when an account reaches 1000 or more failed logons.As this is a test environment, the rule runs every 5 minutes against the last 1 day of data and generates a medium severity incident automatically when results are returned.

Query used:
```
SecurityEvent_CL 
|where EventID_s == "4625" 
|summarize FailedLogons = count() by Account_s
|where FailedLogons >= 1000
|sort by FailedLogons desc
```

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/cd999079eed241aaa341dbd52091d07e0c800527/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20121411.png)

Once saved, the rule successfully triggered an alert in Microsoft Sentinel, confirming that the detection logic was working as expected against the training data.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/4d00f297e255e47a583b3a52b4da1c2436273543/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20121640.png)

### 13. Create a Bookmark for a Suspicious Event

While investigating the Microsoft Sentinel Training Lab sample data, identified a suspicious `FileAccessed` event originating from an unknown IP address. Bookmarked the event to preserve it as evidence and flag it for further investigation.

Query Used:
```
OfficeActivity_CL 
|where Operation_s == "FileAccessed"
```
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/7ad1690f88a7510376c67eaaf4f716901f9e3efd/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20124437.png)

Next, this bookmark was escalated as an incident for further investigation.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/9836c38d1f3cf5a5fbb920bc8dd71999b17eed86/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20125414.png)

---

## Key Takeaways

- The Log Analytics Workspace is the foundation of the entire setup because Sentinel cannot be deployed without it.
- Connecting Defender XDR to Sentinel unifies alerts across endpoints, identity, and email into a single investigation interface.
- The Training Lab solution provides realistic sample data to test detection rules and queries without needing live events.
- Writing KQL queries to detect evens showed how attack patterns like brute force can be translated into actionable alerts.
- Building a Sentinel Workbook provides a visual dashboard for monitoring and identifying suspicious patterns.
- Bookmarks can help track suspicious findings which can be escalated as incidents for further investigation.
---

## Findings & Incident Report
After the brute force detection rule triggered an alert in the Microsoft Sentinel Training Lab, I investigated the incident using KQL queries to identify accounts with the most failed logons and determine whether any successful logins followed. The findings were documented in a formal incident report following a standard SOC reporting structure.

[📄 View Incident Report](INCIDENT-REPORT.md)


## What's Next

**Mini Project 02** — Email threat detection, phishing simulation, and email security policy configuration using Microsoft Defender XDR.

---

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*

