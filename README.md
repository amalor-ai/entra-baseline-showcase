# Entra Baseline · Microsoft Entra ID hardening as code

**Your tenant hardened in 3 days, kept hardened every week, with proof for your auditor.**

Built and maintained by [AMALOR](https://amalor.ai). This repository is a public overview. The module itself is private and delivered as a service.

---

## The problem

Most Microsoft 365 tenants in the Mittelstand were set up years ago and hardened by hand, if at all:

- Conditional Access policies clicked together, undocumented, with silent exceptions
- Emergency ("break-glass") accounts missing, or excluded from nothing, or excluded from everything
- Helpdesk staff with tenant-wide admin rights because scoping was "too complicated"
- No one notices when a setting changes, until the auditor, the cyber insurer or an attacker does

NIS2, cyber insurance questionnaires and Copilot rollouts all ask the same question: *can you show that your identity setup is secure and stays that way?*

## What the baseline does

| Pack | Outcome |
|---|---|
| **Emergency access** | Two cloud-only break-glass accounts, excluded from every baseline policy through one protected group. Checked every week. |
| **Conditional Access** | A small, opinionated set of policies: MFA for admins and all users, legacy authentication blocked, Azure management and device registration protected. |
| **Delegation** | Administrative units per site or subsidiary, helpdesk rights scoped to their own users, sensitive accounts in a restricted management unit. |
| **Drift monitoring** | A weekly report of everything that changed against the approved baseline. |

See [`examples/sample-drift-report.md`](examples/sample-drift-report.md) for what a client receives after a normal week: someone added a temporary admin to the break-glass group, an exclusion was changed by hand, and a policy was enforced without approval.

## How it is built

- **Baseline as data.** Every policy is a JSON file, versioned and reviewed like code. Example: [`examples/CA003-require-mfa-all-users.json`](examples/CA003-require-mfa-all-users.json)
- **One config per client.** No client-specific code. What differs per client is a validated config file: [`examples/client.example.json`](examples/client.example.json) against [`examples/client-config.schema.json`](examples/client-config.schema.json)
- **Runs from a pipeline, not a laptop.** GitHub Actions signs in to the client tenant with federated credentials. No passwords or secrets are stored anywhere. Details in [`docs/architecture.md`](docs/architecture.md).

## Safety rules (enforced in code, covered by tests)

1. **Report before change.** Every engagement starts with a read-only gap report.
2. **Report-only first.** New Conditional Access policies are always created in report-only mode. Enforcement happens per policy, only after the client approves it in writing.
3. **Never loosen.** If a policy is stricter in the tenant than in the baseline, it is flagged, never weakened automatically.
4. **No emergency access, no changes.** If break-glass checks fail, Conditional Access changes are blocked.
5. **No deletes.** Only objects prefixed `AMALOR-` are created or updated. Nothing else in the tenant is touched.
6. **Four eyes.** Every change to a client tenant needs approval from a second person.
7. **Client keeps control.** Deleting two app registrations ends all access. Everything created keeps working without us.

## Engagement

| | |
|---|---|
| **Onboarding** | Workshop, gap report, apply in report-only, enforcement review after 7 days. Fixed scope, fixed price. |
| **Monitoring** | Weekly drift report, quarterly baseline updates, break-glass test with your team. Monthly fee. |
| **Requirements** | Microsoft Entra ID P1 for all users |

Remote, in German, English or Russian.

**Contact:** [amalor.ai](https://amalor.ai)

---

© AMALOR. The files in `examples/` may be reused under the MIT license (see `LICENSE`). The Entra Baseline module is proprietary and not part of this repository.
