# Entra baseline · contoso-gruppe · 2026-10-16

**4 open finding(s)** out of 13 items (mode Report).

## BreakGlass

| | Item | Detail |
|---|---|---|
| ✅ | Exclusion group 'BreakGlass-Exclusion' | 3 member(s) |
| ✅ | bg01@contoso.onmicrosoft.com | Enabled, cloud-only, excluded from AMALOR CA |
| ✅ | bg02@contoso.onmicrosoft.com | Enabled, cloud-only, excluded from AMALOR CA |
| ⚠️ | temp.admin@contoso.de | Unexpected member of the exclusion group: this account bypasses all AMALOR CA policies |

## ConditionalAccess

| | Item | Detail |
|---|---|---|
| ⚠️ | AMALOR-CA001 Require MFA for admin roles | Differs in: conditions.users.excludeGroups |
| ✅ | AMALOR-CA002 Block legacy authentication |  |
| ⚠️ | AMALOR-CA003 Require MFA for all users | Differs in: state (tenant: enabled, baseline: enabledForReportingButNotEnforced) |
| ✅ | AMALOR-CA004 Require MFA for Azure management |  |
| ✅ | AMALOR-CA005 Require MFA to register or join devices |  |

## Delegation

| | Item | Detail |
|---|---|---|
| ✅ | AMALOR-Site-Leipzig |  |
| ✅ | AMALOR-Site-Leipzig / Helpdesk Administrator |  |
| ⚠️ | AMALOR-Site-Leipzig / User Administrator | Unexpected assignment to 44444444-4444-4444-4444-444444444444 |
| ✅ | AMALOR-Protected-Accounts |  |

_Legend: ✅ ok · 🔧 applied · ❌ missing · ⚠️ drift · ✋ manual action · 🛑 error_
