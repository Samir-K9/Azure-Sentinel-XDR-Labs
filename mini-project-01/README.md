# Mini Project 01 — SOC Foundations with Sentinel & Defender

**Tools Used:** Microsoft Azure · Microsoft Sentinel · Microsoft Defender XDR · Log Analytics Workspace  
**Focus:** Environment setup and foundational SOC configuration

---

## Overview

This project documents the full setup of a cloud-based SOC lab environment using Microsoft Azure, Sentinel, and Defender XDR. The goal was to build a working detection and monitoring environment from scratch before moving into KQL queries, alerts, and dashboards in later projects.

---

## Table of Contents

1. [Sign Up for Office 365 E5 Trial (No Teams)](#1-sign-up-for-office-365-e5-trial-no-teams)
2. [Setup Billing](#2-setup-billing)
3. [Create Windows Virtual Machine](#3-create-windows-virtual-machine)
4. [Setup Log Analytics Workspace](#4-setup-log-analytics-workspace)
5. [Setup Microsoft Sentinel](#5-setup-microsoft-sentinel)
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

![Azure Account Setup](screenshots/01-azure-account.png)

---

### 2. Setup Billing

Configured billing settings to manage costs and ensure the lab environment stays within budget.

![Billing Setup](screenshots/02-billing-setup.png)

---

### 3. Create Windows Virtual Machine

Deployed a Windows Virtual Machine in Azure to act as the endpoint generating logs and events for monitoring.

![Windows VM Creation](screenshots/03-windows-vm.png)

---

### 4. Setup Log Analytics Workspace

Created a Log Analytics Workspace — the central data store where all logs are collected and queried.

![Log Analytics Workspace](screenshots/04-log-analytics-workspace.png)

---

### 5. Setup Microsoft Sentinel

Deployed Microsoft Sentinel on top of the Log Analytics Workspace to enable SIEM capabilities including detection, investigation, and response.

![Microsoft Sentinel Setup](screenshots/05-sentinel-setup.png)

---

### 6. Setup Microsoft Defender XDR

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

