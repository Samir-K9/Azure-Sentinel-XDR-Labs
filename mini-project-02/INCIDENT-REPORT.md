## Findings
- **Time:**  3/19/2026 10:22:10 AM UTC | 3/22/2026, 3:09 PM UTC
- **Sender:** samirkhadka@proton.me
- **Description:** Phishing email impersonating a Finance Team member.
- **Subject:** Banking Details URGENT!
- **Target Users:** Bob Smith (bob@mydfirlearn.onmicrosoft.com), Jenny Smith (jenny@mydfirlearn.onmicrosoft.com)
- **Action Taken by User:** Bob Smith clicked the phishing link. Jenny Smith did not interact with the email.
- **Embedded URL:** https://example.com/
---

## Investigation

On 3/19/2026, at `10:22:10 AM UTC` a phishing email was sent from `samirkhadka@proton.me` to `Jenny Smith`, and on 3/22/2026, at `3:09:37 PM UTC` the same email was sent to `Bob Smith`, both impersonating a Finance Team member. The email was delivered to the Junk folder of both users with a warning that the sender was not frequently contacted. The email contained an urgent request to change banking information with a suspicious link embedded in the body. Despite the junk classification and sender warning, Bob Smith clicked the link. Jenny did not interact with this email. Notably, the email passed all email authentication checks (DMARC, DKIM, SPF), indicating the attacker used a legitimate proton.me account rather than a spoofed address.

**Red Flags Identified:**
- The email did not come from an internal email address but rather from an external email provider (`proton.me`).
- "Banking Details URGENT!" is a phishing tactic designed to pressure the user into acting quickly.
- Suspicious embedded link with no context on where it leads.
- Signed off as "Finance Team" to appear as a legitimate internal communication.
- Based on email protection policies, Outlook flagged the sender as unfamiliar — "You don't often get email from samirkhadka@proton.me".
---

### WHO:
- **Sender:** samirkhadka@proton.me
- **Targets:** 
  - Bob Smith — bob@mydfirlearn.onmicrosoft.com
  - Jenny — jenny@mydfirlearn.onmicrosoft.com

### WHAT:
A phishing email impersonating a Finance Team member was delivered to Bob Smith and Jenny's Outlook mailboxes. The email used urgency as a lure, requesting an immediate change to banking details and directing the user to click a suspicious link. Only Bob Smith clicked the link. Jenny did not interact with the email.

### WHEN:
- Jenny — 3/19/2026 at `10:22:10 AM UTC`
- Bob Smith — 3/22/2026 at `3:09:37 PM UTC` — URL click confirmed and logged via Threat Explorer.
- 
### WHERE:
Outlook mailbox.

### WHY:
The motive is not confirmed but it could be a credential harvesting attempt to gain initial access or even financial fraud.

### HOW:
A phishing email was crafted to impersonate an internal Finance Team member, sent from an external proton.me address. The email passed all authentication checks (DMARC, DKIM, SPF), indicating a legitimate proton.me account was used rather than a spoofed address, allowing it to bypass authentication-based filters. The email contained multiple social engineering tactics designed to bypass user awareness.

---

## Recommendations
- Train users to verify sender addresses, especially when emails arrive in Junk or show unfamiliar sender warnings.
- Train users to be cautious of urgent financial request emails regardless of who they appear to be from.
- Regularly run phishing simulations using financial lures to assess and improve user awareness.
- Ensure Safe Links policies are applied to all users to scan URLs before they can be accessed.
- Implement MFA across all accounts to limit the impact of credential harvesting attempts.
- Monitor Threat Explorer regularly for URL click activity from flagged senders.

---

## Evidence

#### Phishing Email Delivered to Junk Folder

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/42faf917995624589b34e7f96349405d1b76da9a/mini-project-02/screenshots/Screenshot%202026-03-22%20151446.png)

### Embedded Link

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/6ee0734f27977ef23f049eafe42edfaa92d2b36b/mini-project-02/screenshots/Screenshot%202026-03-22%20163734.png)

### Accounts Targeted

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/5328e7a5a46533a2f831c7387d577e220c5feaff/mini-project-02/screenshots/Screenshot%202026-03-22%20171322.png)

### URL click

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/5537fd49ac3e64bcc99e8757e57adf7ea5fff802/mini-project-02/screenshots/Screenshot%202026-03-22%20165547.png)

