# Active_Directory-and-Windows_Server_Administration
Windows Server 2022 Active Directory lab in VirtualBox: AD DS, DNS, DHCP, Group Policy, NTFS/share permissions, PowerShell automation, troubleshooting write-ups and recovery. Isolated two-VM domain (DC01 + Windows 11 client).

# Active Directory Home Lab

A virtualised Windows Server 2022 domain environment built to practise
day-to-day Windows system administration: identity management, Group Policy,
file access control, networking services, PowerShell automation, troubleshooting
and recovery.

The lab simulates a small company (**homelab.local**) with three departments
(IT, HR, Sales). It runs on an isolated VirtualBox host-only network
(192.168.56.0/24) with no internet exposure.

<img width="1583" height="1003" alt="Lab Architecture" src="https://github.com/user-attachments/assets/6b8722ec-9073-480c-b81f-8d770751a901" />
Fig 1. Lab Architecture

<img width="1583" height="978" alt="Active Directory Structure" src="https://github.com/user-attachments/assets/6740bf38-8e90-4c8f-a752-cc85a88eceae" />
Fig 2. Structure of Active Directory


## What I built

- **DC01 (Windows Server 2022):** AD DS, DNS, DHCP and file shares, static IP 192.168.56.10
- **CLIENT01 (Windows 11 Enterprise):** domain-joined workstation using a DHCP lease
- **Structured Active Directory:** department OUs, role-based security groups,
  a separate admin account, and delegated password-reset rights for the help desk
- **Group Policy:** domain password and lockout policy, workstation screen lock,
  Control Panel restriction for Sales, department drive maps, logon banner
- **File services:** department shares secured with NTFS and share permissions
  (least privilege) with access-based enumeration
- **PowerShell automation:** bulk user creation from CSV (with `-WhatIf`, error
  handling and logging), account reporting, and leaver offboarding
- **Troubleshooting labs:** documented faults covering DNS, DHCP, permissions,
  GPO and account lockout, each with symptom, diagnosis, fix and lesson learned
- **Recovery:** snapshots, AD Recycle Bin restore, and system-state backup

## Skills demonstrated

| Area | What I did |
|------|-----------|
| Active Directory | OUs, security groups, user life cycle, delegation of control |
| Group Policy | Domain-level password policy, OU-targeted user/computer GPOs, verified with `gpresult` |
| DNS and DHCP | Scope 192.168.56.100-200, reverse lookup zone, A/CNAME/PTR/SRV records |
| File services | NTFS + share permissions, tested allowed and denied access per role |
| PowerShell | Idempotent scripts with error handling, logging and no hard-coded passwords |
| Troubleshooting | Structured method: IP, DNS, authentication, policy, then fix one thing and re-test |

## Repository contents

- `docs/` network diagram, IP and naming plan, AD structure, GPO list, permissions matrix
- `scripts/` PowerShell scripts with a sample CSV (fictional data only)
- `troubleshooting/` symptom, investigation, root cause and fix write-ups
- `screenshots/` evidence for each task

## Lessons learned

- Most domain-join failures were DNS problems, not Active Directory problems.
- VirtualBox's built-in DHCP server must be disabled or clients can receive the wrong DNS.
- Group membership changes need a fresh sign-in before access updates.

## Next steps

Second domain controller and replication, Windows LAPS, WSUS, Microsoft Entra Connect.

> This is an isolated lab environment. All names, users and passwords are fictional.
