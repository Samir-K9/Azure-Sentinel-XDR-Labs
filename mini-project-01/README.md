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
6. [Setup Microsoft Defender XDR](#6-setup-microsoft-defender-xdr)
7. [Ingest Training Logs](#7-ingest-training-logs)
8. [Create Workbook](#8-create-workbook)
9. [Connect Microsoft Defender XDR to Sentinel](#9-connect-microsoft-defender-xdr-to-sentinel)
10. [Create Alerts](#10-create-alerts)
11. [Create Bookmarks](#11-create-bookmarks)

---

## Steps

### 1. Sign Up for Office 365 E5 Trial (No Teams)

Signed up for the Office 365 (no Teams) E5 trial, which activates a Microsoft 365 E5 trial license. This license includes access to Microsoft Defender for Endpoint and Microsoft Defender for Office 365 — both essential for building out the detection and response capabilities used throughout this lab.

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

![Image Alt]([screenshots/04-log-analytics-workspace.png](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/c547ca00972c2f7669dee5d97a79a1a3934dcbb7/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20121112.png)

---

### 5.Create a Log Analytics Workspace

Created a Log Analytics Workspace in the Azure portal. This serves as the central data store where all logs and security events are collected, stored, and queried. Microsoft Sentinel is built on top of the Log Analytics Workspace, making this a foundational step before any detection or monitoring can be configured.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/405f12d26e3eab881ec977ae8f2e29f19b1126bb/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-19%20121711.png))

---

### 6. Setup Microsoft Sentinel

Activated Microsoft Defender XDR to provide extended detection and response coverage across endpoints, identity, and cloud apps.

![Defender XDR Setup](screenshots/06-defender-xdr-setup.png)

---

### 7. Ingest Training Logs

Ingested sample training logs into the Log Analytics Workspace to simulate real event data for detection and analysis.

![Training Logs Ingested](screenshots/07-training-logs.png)

---

### 8. Create Workbook

Built a Sentinel Workbook to visualize ingested log data and monitor the environment at a glance.

![Workbook Created](screenshots/08-workbook.png)

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

