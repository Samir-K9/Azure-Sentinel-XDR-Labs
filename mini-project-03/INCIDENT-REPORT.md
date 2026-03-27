## Findings
- **Time:**  3/27/2026 | 13:07:24 PM 
- **Host:** DESKTOP-40ORUBT
- **User:** Bob Smith
- **IOC URL:**  https://github.com/redcanaryco/atomic-red-team/raw/master/atomics/T1547.001/src/Discovery.bat
- **Risk Level:** High
---

## Investigation

On 3/27/2026, between 13:07:24 PM and 13:07:42 PM, three separate Powershell processes were executed under the account of Bob Smith on host DESKTOP-40ORUBT all originating from a remote session. All these processes ran with full administrative privileges. The activity spanned approximately 19 seconds and established three distinct persistence mechanisms across both HKLM and HKCU hive locations.

- Persistence Mechanism 1 — RunOnce Key (13:07:24 UTC, PID 7412)
The first Powershell process  first wrote a value named NextRun to HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce. The value contained a fileless IEX + DownloadString payload referencing an external URL hosted on GitHub. This key executes once on the next logon and then is removed because the registry key involved is RunOnce, making it a stealthy one-time execution mechanism. The original value was empty prior to this modification.

- Persistence Mechanism 2 — HKCU Run Key with SOCKS5 Proxy (13:07:33 UTC, PID 4684)
Nine seconds later, a second PowerShell process wrote a value named socks5_powershell to HKCU\Software\Microsoft\Windows\CurrentVersion\Run. The value launched PowerShell with a hidden window, bypassing execution policy, suggesting the intent to establish a covert, persistent background process which could likely be a SOCKS5 proxy for tunneling traffic. Unlike RunOnce, Run keys persist across every logon until explicitly removed. The naming convention socks5_powershell strongly implies this was designed to maintain ongoing covert network access on the host.

- Persistence Mechanism 3 — Winlogon Shell Hijack (13:07:42 UTC, PID 6984)
Ten seconds after that, a third PowerShell process modified the Winlogon Shell value under HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon. It first backed up the original value (explorer.exe) to a new key named Shell-backup, then appended a second instance of explorer.exe (C:\Windows\explorer.exe) to the Shell value. This is a classic T1547.004 technique which is appending a malicious or secondary executable to the Winlogon Shell so it launches at every interactive logon alongside the legitimate shell. Defender confirmed the shell path changed from explorer.exe to explorer.exe, C:\Windows\explorer.exe.
---
### WHO 
- User: AzureAD\BobSmith 

### WHAT 
Three PowerShell processes established three layered persistence mechanisms: a RunOnce fileless download payload, a hidden SOCKS5 proxy Run key, and a Winlogon Shell hijack.

### WHEN 
Activity occurred between 2026-03-27 13:07:24 and 13:07:43.

### WHERE 
- Host: DESKTOP-40ORUBT

### WHY 
The intent appears to be establishing deep, layered persistence ensuring at least one mechanism survives security remediation alongside a covert outbound communication channel via the SOCKS5 proxy.

### HOW 
The actor operated remotely through BobSmith's elevated session and sequentially executed three PowerShell scripts modifying the registry to implant multiple autostart mechanisms across different hive locations and logon trigger point.

---

## Recommendations
- Immediately isolate DESKTOP-40ORUBT and treat the host as being fully compromised.
- Audit and remove all three malicious registry entries and reimage the machine.
- Investigate any outbound traffic from this host.
- Determine how the remote session has authorized to Bob's account and reset Bob Smith's credentials immediately.
- Hunt across other endpoints for lateral movement and see if those scripts are seen elsewhere.

---

## Evidence

Alert Generated

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/dda986e308784d4496bd6ab110a4a401376e3833/mini-project-03/screenshots/Screenshot%202026-03-27%20152050.png)

Malicious Registry Entries

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/c45e81181a22c3d55c1807510e2055b15efe0c1e/mini-project-03/screenshots/Screenshot%202026-03-27%20152050.png)




