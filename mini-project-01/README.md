# Mini Project 01 — SOC Foundations with Sentinel & Defender

**Tools Used:** Microsoft Azure · Microsoft Sentinel · Microsoft Defender XDR · Log Analytics Workspace  
**Focus:** Environment setup and foundational SOC configuration

---

## Overview

This project documents the full setup of a cloud-based SOC lab environment using Microsoft Azure, Sentinel, and Defender XDR. The goal was to build a working detection and monitoring environment from scratch before moving into KQL queries, alerts, and dashboards in later projects.

---

## Table of Contents

1. [Sign Up for Office 365 E5 Trial (No Teams)](#1-sign-up-for-office-365-e5-trial-no-teams)
2. [Assign Microsoft 365 E5 Licence to Your User](#2-assign-microsoft-365-e5-licence-to-your-user)
3. [Create a Microsoft Azure Portal Account](#3-create-a-microsoft-azure-portal-account)
4. [Set Up a Billing Alert in Azure](#4-set-up-a-billing-alert-in-azure)
5. [Create a Log Analytics Workspace](#5-create-a-log-analytics-workspace)
6. [Set Up Microsoft Sentinel](#6-set-up-microsoft-sentinel)
7. [Export Activity Logs from Azure Subscription to Log Analytics Workspace](#7-export-activity-logs-from-azure-subscription-to-log-analytics-workspace)
8. [Create Workbook](#8-create-workbook)
9. [Connect Microsoft Defender XDR to Sentinel](#9-connect-microsoft-defender-xdr-to-sentinel)
10. [Create Alerts](#10-create-alerts)
11. [Create Bookmarks](#11-create-bookmarks)

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

### 3. Create a Microsoft Azure portal account.

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

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/8d1f44715102abbff8fdecccafc6bfbc194f3354/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20122426.png))

---

### 7. Export Activity Logs from Azure Subscription to Log Analytics Workspace

Exported the Azure subscription's activity logs to the Log Analytics Workspace. Specifically administrative, security and alert logs were ingested.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/56cc2083e5f4df758dfc9dcdb751f161f37b6f97/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20105814.png)


---

### 8. Install AzureActivity Solution from Content Hub

Installed the AzureActivity solution from the Content Hub in Microsoft Sentinel.This will enable the logs that we wanted to be exported from the Azure to be ingested into Microsoft Sentinel through pre-built data connectors, analytics rules, and workbooks specifically designed to monitor and detect threats based on Azure subscription activity logs.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/1909ea4991e7152046e003f1695ab38556b47b16/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20110736.png)

---

### 9. Connect Microsoft Defender XDR to Sentinel

Configured the Defender XDR data connector in Sentinel to unify alerts and incidents across both platforms into a single investigation experience.

![Defender XDR Connected to Sentinel](screenshots/09-xdr-sentinel-connection.png)

---

### 10. Create Alerts

Created analytics rules in Sentinel to generate alerts based on specific conditions detected in the log data.

![Alerts Created](screenshots/10-alerts.png)

---

### 11. Create Bookmarks

Used Sentinel's bookmark feature to flag and preserve key events during investigation for future reference.

![Bookmarks Created](screenshots/11-bookmarks.png)

---

## Key Takeaways

- Setting up the Log Analytics Workspace first is critical — everything else in Sentinel depends on it
- Connecting Defender XDR to Sentinel gives a unified view of incidents, which is how most enterprise SOCs operate
- Bookmarks are a simple but powerful way to track evidence during an investigation
- Having training logs available from the start made it much easier to test rules and queries without waiting for real events

---

## What's Next

**Mini Project 02** — KQL queries, threat hunting, and custom detection rules

---

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*

