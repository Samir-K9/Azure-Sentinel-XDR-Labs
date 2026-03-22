# Incident Report — Phishing Email Investigation

**Project:** Mini Project 02 — Email Threat Detection & Phishing Simulation  
**Tool:** Microsoft Defender XDR Portal  
**Severity:** Medium  
**Status:** Resolved

---

## Findings

A phishing simulation was launched via Attack Simulation Training in the Microsoft Defender XDR portal. A simulated phishing email was sent to a target user. The user clicked the phishing link, triggering a landing page warning and an automated security awareness training email. The URL click was confirmed in Threat Explorer, providing visibility into the user's interaction with the malicious link.

---

## Investigation Summary

A suspicious email was delivered to a target user as part of a controlled phishing simulation. The email bypassed the user's awareness and the link was clicked. Microsoft Defender for Office 365 detected the interaction and logged the event. The investigation followed a standard SOC analyst workflow — from alert to evidence gathering to response.

---

## Who, What, When, Where, Why, How

**Who:** The target user (Bob) was the recipient of the phishing email.

**What:** A simulated phishing email containing a malicious link was delivered to the user's inbox. The user clicked the link.

**When:** The event occurred during the phishing simulation. The URL click was logged in real time and visible in Threat Explorer.

**Where:** The attack took place within the Microsoft 365 environment, targeting the user's Outlook mailbox.

**Why:** The user was not aware the email was a phishing attempt and clicked the link without verifying the sender or URL.

**How:** The phishing email was crafted to appear legitimate. Upon clicking the link, the user was redirected to a landing page confirming the simulation. Microsoft Defender logged the URL click and triggered an automated training response.

---

## Recommendations

- Enforce mandatory security awareness training for all users, particularly those who interact with phishing simulations
- Enable and tune Anti-Phishing policies to flag emails from infrequent or unknown senders
- Ensure Safe Links policies are applied to all users to rewrite and scan URLs before they can be accessed
- Regularly run phishing simulations to assess user awareness and measure improvement over time
- Monitor Threat Explorer for URL click activity to identify users who engage with suspicious links
- Implement MFA across all accounts to limit the impact of credential harvesting phishing attempts

---

*Part of the [Azure-Sentinel-XDR-Labs](../README.md) project series.*
