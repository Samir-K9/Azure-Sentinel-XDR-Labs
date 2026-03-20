
## Findings
- Time : 3/12/2026, 3:40:17.944 PM UTC --- 3/12/2026, 3:40:17.866 PM UTC
- Host PC: SHIR-Hive, SOC-FW-RDP , SHIR-SAP
- Targetted Accounts: \admin, \administrator, \ADMINISTRATOR

## Investigation
On 3/12/2026, multiple accounts with administrative privileges were targetted in a bruce force attempt to gain access to the system with more than a 1000 attempts made within a short span of time. The initial activity started at `3:40:17.944 PM UTC` and continued until `3:40:17.866 PM UTC`.
### Number of failed logons: 
- \administrator = 1864
- \admin = 1989
- \ADMINISTRATOR = 10255
Upon further investigation, it was identified that there were no successful logons to any of those accounts.

## WHO: \admin, \administrator, \ADMINISTRATOR
## WHAT: Multiple failed logons identified.
## WHEN: 3/12/2026, 3:40:17.944 PM UTC --- 3/12/2026, 3:40:17.866 PM UTC
## WHERE: SHIR-Hive, SOC-FW-RDP , SHIR-SAP
## WHY: As there were no successful logons, it is unclear regarding the motive of the attacker but as high privilege accounts were targetted a lot of damage could have been done.
## HOW: Brute Force (>1000 attempts on each accounts.)

## Recommendations
- Implement account lockout policies.
- Enforce strong password policies.
- Enable multi-factor authentication.
- Constant monitoring and alerting on any activities related to high privileged accounts.

## Evidence


