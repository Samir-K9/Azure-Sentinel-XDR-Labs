# Mini Project 02 — Email Threat Detection & Phishing Simulation

**Tools Used:** Microsoft Defender XDR · Microsoft 365 Admin Centre · Attack Simulation Training · Microsoft Outlook

**Focus:** Email threat detection, phishing simulation, and email security policy configuration

---

## Overview

This project explores email threat detection and phishing simulation using the Microsoft Defender XDR portal. The goal was to configure email security policies, simulate a real-world phishing attack, investigate user interaction using Threat Explorer, and document findings in a formal incident report.

---

## Table of Contents

1. [Create Users and Assign Microsoft 365 E5 Licences](#1-create-users-and-assign-microsoft-365-e5-licences)
2. [Create a Safe Links Policy](#2-create-a-safe-links-policy)
3. [Create an Anti-Phishing Policy](#3-create-an-anti-phishing-policy)
4. [Report a Phishing Email and Review in Defender](#4-report-a-phishing-email-and-review-in-defender)
5. [Run a Phishing Email Test on User Account](#5-run-a-phishing-email-test-on-user-account)
6. [Launch a Phishing Simulation from Microsoft Defender](#6-launch-a-phishing-simulation-from-microsoft-defender)
7. [Click the Phishing Link as the Target User](#7-click-the-phishing-link-as-the-target-user)
8. [Review the Phishing Simulation Report and URL Click Activity](#8-review-the-phishing-simulation-report-and-url-click-activity)
---

## Steps

### 1. Create Users and Assign Microsoft 365 E5 Licences

Created two new user accounts in the Microsoft 365 admin centre and assigned Microsoft 365 E5 licences to both. Activated their Outlook mailboxes to enable email functionality. These user accounts will be used to test email-based attacks.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/3417c378c41e31760365e6202d0a88eb6cca6781/mini-project-02/screenshots/Screenshot%202026-03-20%20182444.png)

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/dc0c241f89de0d00fbff968ea76f93c874d1f491/mini-project-02/screenshots/Screenshot%202026-03-20%20183139.png)

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/dc0c241f89de0d00fbff968ea76f93c874d1f491/mini-project-02/screenshots/Screenshot%202026-03-20%20183301.png)


---

### 2. Create a Safe Links Policy

Created a Safe Links policy in the Microsoft Defender XDR portal. Safe Links protects users by scanning and rewriting URLs in emails and Office documents in real time, blocking access to malicious links at the time of click rather than at the time of delivery.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/d50be27a1bd06d23e453898092420ad184e58fff/mini-project-02/screenshots/Screenshot%202026-03-20%20184321.png)

Before the policy was applied, URLs in emails appeared as regular hyperlinks with no scanning or protection applied.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/56026092f3ce255adfd893a43877ffc490a64548/mini-project-02/screenshots/Screenshot%202026-03-20%20185924.png)

After the policy was applied, URLs are rewritten and routed through Microsoft's Safe Links scanning service before the user can access them.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/9e92e93e298b1809491908c4fba0ac13f30de168/mini-project-02/screenshots/Screenshot%202026-03-20%20190900.png)


---

### 3. Create an Anti-Phishing Policy

Created an anti-phishing policy in the Microsoft Defender XDR portal to protect users against phishing attacks including impersonation attempts, spoof emails, and malicious senders.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/ebe2b383e1cf46c3fa852762f040df70acb3bab9/mini-project-02/screenshots/Screenshot%202026-03-21%20212435.png)

---

### 4. Report a Phishing Email and Review in Defender

Reported the test emails as phishing directly from Outlook. The submission appeared in the Actions & Submissions tab in the Microsoft Defender XDR portal, confirming that user-reported phishing emails are captured and queued for review by the security team. 

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/f018441d81959ba7d13bbba96d185c6c30017fe6/mini-project-02/screenshots/Screenshot%202026-03-22%20150255.png)

---

### 5. Run a Phishing Email Test on User Account

Sent a simulated phishing email to Bob's account to test the effectiveness of the policies applied. The email was automatically directed to the junk folder rather than the inbox, with a notification warning that the sender is not frequently contacted. This confirms that the anti-phishing and Safe Links policies are working as intended

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/42faf917995624589b34e7f96349405d1b76da9a/mini-project-02/screenshots/Screenshot%202026-03-22%20151446.png)


---

### 6. Launch a Phishing Simulation from Microsoft Defender

Launched a phishing simulation using the Attack Simulation Training feature in the Microsoft Defender XDR portal. The simulation sent a realistic phishing email to the test users to evaluate how they respond to a real-world phishing attempt

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/e7cc0c6f339a78e2b52057a5910b462f6c3a4530/mini-project-02/screenshots/Screenshot%202026-03-22%20152758.png)

---

### 7. Click the Phishing Link as the Target User

Logged in as the target user and clicked the phishing link in the simulated email. Upon clicking, a landing page was displayed informing the user that they had fallen for a phishing simulation. 

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/52ba35dee19bc07dbbe05d7ca92e2dda619de522/mini-project-02/screenshots/Screenshot%202026-03-22%20153211.png)

Immediately after, the user received an automated training email, simulating how organisations deliver security awareness training to employees who interact with phishing content in a real SOC environment.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/02f95811d690b154f8200b63f09161711fea3b2b/mini-project-02/screenshots/Screenshot%202026-03-22%20153642.png)

---

### 8. Review the Phishing Simulation Report and URL Click Activity

Reviewed the simulation report in the Attack Simulation Training section of the Microsoft Defender XDR portal, which provided a breakdown of which users clicked the phishing link, who reported it, and who completed the follow-up training. Additionally, checked the URL click activity in Threat Explorer to confirm the phishing link click was logged and visible from a threat hunting perspective.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/65fcc3de902953b8f0f8736da0f1987907524bd1/mini-project-02/screenshots/Screenshot%202026-03-22%20154240.png)

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/8c6df92f8cbc75fea444f93419b2a4f39835f7fb/mini-project-02/screenshots/Screenshot%202026-03-22%20154916.png)


## Key Takeaways
- Safe Links rewrites URLs in real time, meaning protection is applied at the time of click rather than at delivery.
- Anti-phishing policies add an important layer of protection against impersonation and spoofed senders that basic spam filters may miss.
- Even with policies in place, users can still interact with phishing emails.
- Attack Simulation Training provides a realistic way to test user behaviour and measure the effectiveness of security awareness across the organisation.
- Threat Explorer gives visibility into URL click activity, allowing analysts to identify which users interacted with malicious links during an investigation.
- User-reported phishing submissions in the Actions & Submissions helps the security team improve detection and policy tuning.
---

## Findings & Incident Report
After simulating a phishing email, I investigated the results using Threat Explorer to identify which users interacted with the phishing email and whether the configured policies detected and responded to the threat. The findings were documented in a formal incident report following a standard SOC reporting structure.


[📄 View Incident Report](INCIDENT-REPORT.md)


## What's Next

**Mini Project 03 — Endpoint Security with Microsoft Defender for Endpoint & Intune**

---

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*

