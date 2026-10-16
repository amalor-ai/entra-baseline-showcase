# Examples

Illustrative only. These files show the format and the approach, not a complete or tenant-ready baseline.

- `CA003-require-mfa-all-users.json`: one baseline policy as data. The `{{BreakGlassGroupId}}` placeholder is replaced per client. In a real engagement it is created in **report-only** mode and enforced only after review.
- `client.example.json` / `client-config.schema.json`: how one client is described. All IDs are fake.
- `sample-drift-report.md`: what a client receives after a normal week, generated against a simulated tenant.

Do not import these into a production tenant without an assessment. See the main README.
