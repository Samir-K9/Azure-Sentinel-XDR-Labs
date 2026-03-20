
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

#### WHO: \admin, \administrator, \ADMINISTRATOR
#### WHAT: Multiple failed logons identified.
#### WHEN: 3/12/2026, 3:40:17.944 PM UTC --- 3/12/2026, 3:40:17.866 PM UTC
#### WHERE: SHIR-Hive, SOC-FW-RDP , SHIR-SAP
#### WHY: As there were no successful logons, it is unclear regarding the motive of the attacker but as high privilege accounts were targetted a lot of damage could have been done.
#### HOW: Brute Force (>1000 attempts on each accounts.)

## Recommendations
- Implement account lockout policies.
- Enforce strong password policies.
- Enable multi-factor authentication.
- Constant monitoring and alerting on any activities related to high privileged accounts.

## Evidence
#### Number of failed logons.

![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/adae989f1456d200968b830a4cb59d9ff0d84fcd/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20134736.png)

#### Time Range
  
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/d936c7272084b20716bc99bb274cb32cc5c99bce/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20140504.png)

#### No successful logons.
  
![Image Alt](https://github.com/Samir-K9/Azure-Sentinel-XDR-Labs/blob/aac29e9f7b43437a18a2819ea01205f5d12e0834/mini-project-01/%20%20%20screenshots/Screenshot%202026-03-20%20140716.png)



