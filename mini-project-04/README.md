# Mini Project 04 — Identity Protection & Conditional Access with Microsoft Entra ID

**Tools Used:** Microsoft Entra ID · Microsoft Sentinel · Microsoft Defender XDR · Log Analytics Workspace

**Focus:** Conditional Access policy configuration, identity log ingestion, and Sentinel integration

---

## Overview

This project explores identity protection using Microsoft Entra ID. The goal was to configure a Conditional Access policy to restrict access based on location, validate the policy by testing a blocked sign-in, and integrate Entra ID logs into Microsoft Sentinel for identity-based threat detection and monitoring.

---

## Table of Contents

1. [Create a Named Location for Canada](#1-create-a-named-location-for-canada)
2. [Disable Security Defaults](#2-disable-security-defaults)
3. [Create a Conditional Access Policy to Block Access from Canada](#3-create-a-conditional-access-policy-to-block-access-from-canada)
4. [Test the Conditional Access Policy](#4-test-the-conditional-access-policy)
5. [Install Microsoft Entra ID Solution from Content Hub](#5-install-microsoft-entra-id-solution-from-content-hub)
6. [Configure Microsoft Entra ID Data Connector](#6-configure-microsoft-entra-id-data-connector)
7. [Verify Log Ingestion in Microsoft Sentinel](#7-verify-log-ingestion-in-microsoft-sentinel)

---

## Steps

### 1. Create a Named Location for Canada

Created a Named Location in Microsoft Entra ID to define Canada as a geographic location. This will be referenced in a Conditional Access policy to block sign-in attempts originating from Canada for a specific user.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/500304d3b4572d97d2aa1ea4f00c37b93cd8d09a/mini-project-04/screenshots/Screenshot%202026-04-03%20130513.png)

---

### 2. Disable Security Defaults

Disabled Security Defaults in Microsoft Entra ID before creating the Conditional Access policy. Security Defaults and Conditional Access policies cannot be used at the same time. Security Defaults must be turned off first to allow custom Conditional Access policies to take effect.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/6cb07f0588f9c111ca186b632032e065eb89c5eb/mini-project-04/screenshots/Screenshot%202026-04-03%20130826.png)

---

### 3. Create a Conditional Access Policy to Block Access from Canada

Created a Conditional Access policy in Microsoft Entra ID to block Jenny's access when signing in from Canada. The policy was configured with the following settings:

- Users: Jenny (specific user included)
- Target Resources: All resources (all cloud apps)
- Network: Canada named location included
- Access Control: Block access

Once saved, any sign-in attempt by Jenny originating from Canada will be blocked by this policy.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/7c1cd256630afc38fe19c6e402bc0d2ca1ee93d5/mini-project-04/screenshots/Screenshot%202026-04-03%20131355.png)

---

### 4. Test the Conditional Access Policy

Tested the policy by attempting to sign in as Jenny from a Canadian location. The sign-in was blocked and confirmed that even though Jenny's credentials are valid, access is denied based on the location condition applied by the policy.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/a532506807be8646879b3f2ccfa9578462b7c498/mini-project-04/screenshots/Screenshot%202026-04-03%20131538.png)

The blocked sign-in was also visible in the Microsoft Entra ID sign-in logs, confirming the event was captured and auditable for investigation purposes.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/35de95a2edb11e7590cf9b8dc8136470088b60ec/mini-project-04/screenshots/Screenshot%202026-04-03%20151304.png)

---

### 5. Install Microsoft Entra ID Solution from Content Hub
Navigated to the Content Hub under Microsoft Sentinel in Microsoft Defender and installed the Microsoft Entra ID solution. This deploys pre-built data connectors, analytics rules, and workbooks designed to monitor and detect identity-based threats using Entra ID sign-in and audit logs, extending Sentinel's detection capabilities to cover identity events.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/a972ecd37dbb715c56b450156fc79ce7abbb8cf6/mini-project-04/screenshots/Screenshot%202026-04-03%20154613.png)

---

### 6. Configure Microsoft Entra ID Data Connector

Navigated to Configuration → Data Connectors in Microsoft Sentinel, selected the Microsoft Entra ID connector and opened the connector page. Enabled the following log types to begin ingesting identity data into the Log Analytics Workspace:

- Sign-in Logs — captures all user sign-in activity including successful and failed attempts, locations, and applied Conditional Access policies.
- Audit Logs — records administrative actions and changes made within Microsoft Entra ID such as user creation, role assignments, and policy changes.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/2f1159d2cbca3a89fae2cc67bb10bd28eac1bdbe/mini-project-04/screenshots/Screenshot%202026-04-03%20154745.png) 

---

### 7. Verify Log Ingestion in Microsoft Sentinel

Navigated to Logs under Log Management in Microsoft Sentinel to verify that the Entra ID logs were being ingested successfully. Both the SigninLogs and AuditLogs tables were visible and returning data, confirming that identity events from Microsoft Entra ID are now flowing into the Log Analytics Workspace and available for querying and detection.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/e5d8d51a33f08411fea05cb34cfc62f0b6c7fef2/mini-project-04/screenshots/Screenshot%202026-04-05%20202328.png)

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/e5d8d51a33f08411fea05cb34cfc62f0b6c7fef2/mini-project-04/screenshots/Screenshot%202026-04-05%20202435.png)

---

## Key Takeaways

- Security Defaults must be disabled before Conditional Access policies can take effect because the two cannot coexist.
- Named Locations allow granular location-based access control, enabling policies to be applied to specific countries or IP ranges.
- Conditional Access policies enforce Zero Trust principles.
- Even a valid sign-in can be blocked if it does not meet the conditions defined in a Conditional Access policy.
- Integrating Entra ID sign-in and audit logs into Sentinel extends identity visibility into the SIEM, making it possible to detect and investigate identity-based threats in one place.

---

## What's Next

This is the final mini project in the **Azure-Sentinel-XDR-Labs** series. Across all four projects, the lab covered foundational SOC setup, email threat detection, endpoint security, and identity protection — building a practical end-to-end SOC environment using the Microsoft security stack.

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*



