# OlympCron Manager End User License Agreement (EULA)

**Last Updated:** 2026-05-16

---

## Contents

1. Scope
2. License Grant
3. Updates and Maintenance
4. Third-Party Dependencies
5. Support
6. Functionality Disclaimer
7. Limitation of Liability
8. High-Risk Operations
9. Security Responsibility
10. Changes to the Software
11. Termination
12. Governing Law
13. Severability
14. Contact Information

---

## 1. Scope

This End User License Agreement ("Agreement") governs the use of the software product:

**OlympCron Manager**  
(the "Software")

provided by:

**Alexander Stusse / Stusse Development**  
(the "Developer")

By downloading, installing, or using the Software, you ("User") agree to be bound by this Agreement.

If you do not agree to these terms, you must not use the Software.

---

## 2. License Grant

The Software is licensed, not sold.

Subject to this Agreement, the Developer grants the User a limited, non-exclusive, non-transferable, revocable license to install and use the Software for personal or commercial purposes, free of charge.

No ownership rights to the Software or source code are transferred to the User.

No activation, license key, or account is required to use the Software.

---

## 3. Updates and Maintenance

The Developer may provide updates, bug fixes, security patches, and improvements at the Developer's sole discretion.

Except where required by applicable law, the Developer is not obligated to:

- provide updates indefinitely,
- maintain compatibility with all future operating systems,
- maintain compatibility with all future SSH implementations,
- add new features,
- fix every reported issue.

The Developer may discontinue updates and maintenance at any time.

---

## 4. Third-Party Dependencies

The Software depends on third-party software and services, including but not limited to:

- Linux operating systems
- SSH servers
- Flutter and other frameworks
- Open-source libraries

The Developer is not responsible for:

- changes to third-party software,
- breaking changes introduced by vendors,
- discontinued third-party services,
- incompatibilities caused by external systems.

Use of third-party components may be subject to their respective license terms.

---

## 5. Support

Support may be provided voluntarily and at the Developer's sole discretion.

Unless explicitly stated in a separate written agreement, the Developer does not guarantee:

- any response time,
- any resolution time,
- continuous support,
- custom feature development.

---

## 6. Functionality Disclaimer

The Software is provided **"AS IS"** and **"AS AVAILABLE"**.

The Developer does not warrant that:

- the Software will be error-free,
- the Software will operate uninterrupted,
- all features will remain available,
- the Software will meet the User's specific requirements.

---

## 7. Limitation of Liability

To the maximum extent permitted by law, the Developer shall not be liable for:

- data loss,
- server downtime,
- crontab misconfiguration,
- scheduled job failures or unintended executions,
- system damage,
- security incidents,
- loss of profits,
- indirect, incidental, special, or consequential damages.

The User is solely responsible for all cron jobs deployed through the Software and all resulting consequences.

Where liability cannot be excluded under applicable law, liability is limited to zero, as the Software is provided free of charge.

---

## 8. High-Risk Operations

The Software enables deployment of cron jobs to remote Linux servers, including potentially destructive actions such as:

- deleting files or directories on a schedule,
- restarting or stopping services,
- modifying database contents,
- pruning Docker resources,
- running system-level commands.

Such scheduled actions may cause irreversible damage.

The User acknowledges and accepts full responsibility for all cron jobs configured and deployed using the Software.

---

## 9. Security Responsibility

The User is solely responsible for:

- securing SSH credentials,
- protecting private keys,
- restricting server access,
- reviewing all cron job commands before deployment,
- maintaining backups,
- implementing appropriate security measures.

The Developer is not responsible for unauthorized access caused by improper credential management or inadequate security practices.

---

## 10. Changes to the Software

The Developer reserves the right to:

- add, modify, or remove features,
- discontinue the Software,
- change licensing models.

Such changes may apply to future versions of the Software.

---

## 11. Termination

This license terminates automatically if the User violates this Agreement.

Upon termination, the User must:

- cease all use of the Software,
- delete all copies of the Software.

---

## 12. Governing Law

This Agreement is governed by the laws of the Federal Republic of Germany.

If the User is a merchant (Kaufmann), legal entity under public law, or special fund under public law, the exclusive place of jurisdiction shall be Worms, Germany, to the extent permitted by law.

---

## 13. Severability

If any provision of this Agreement is held invalid or unenforceable, the remaining provisions shall remain in full force and effect.

---

## 14. Contact Information

**Developer:** Alexander Stusse / Stusse Development  
**Website:** https://olympstack.com  
**Email:** contact@olympstack.com
