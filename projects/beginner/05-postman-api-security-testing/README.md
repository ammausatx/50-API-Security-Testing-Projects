# 05. Postman API Security Testing

**Level:** Beginner  
**Focus:** Build a repeatable API security test collection  
**Tools:** Postman, Postman environments, curl

## Objective
Create a reusable collection testing authentication, authorization, validation, error handling, and response properties.

## Scope and safety
This walkthrough is for an isolated, intentionally vulnerable local training API or a system you own and are explicitly authorized to assess. Use synthetic data and disposable accounts. Do not test public or production APIs without written permission. Screenshots are simulated fictional training visuals, not evidence from a real assessment.

## Lab preparation
Use a local training API and synthetic users. Define baseUrl, lowPrivilegeToken, adminToken, and disposable object IDs. Never commit real credentials.

## Walkthrough
1. Create collection folders for discovery, authentication, authorization, validation, and regression tests.
2. Define a local environment and store test-only tokens as variables; keep secrets out of exported files.
3. Add a health-check request and assert expected status and JSON content type.
4. Create paired requests for low-privilege and administrator roles; compare access to the same test object.
5. Add negative tests for missing token, malformed JSON, unexpected fields, and invalid identifiers.
6. Use post-response scripts to assert status, headers, response schema, and absence of synthetic sensitive fields.
7. Export a sanitized collection and environment template; remove tokens and personal data before committing.

## Example commands
Run only against your local lab; adjust port and paths to match your environment.
```bash
curl -i http://127.0.0.1:8888/api/v1/profile -H 'Authorization: Bearer LAB_TOKEN_REPLACE_ME'
curl -s http://127.0.0.1:8888/api/v1/profile -H 'Authorization: Bearer LAB_TOKEN_REPLACE_ME' | jq 'keys'
```

## What to look for
A collection can expose inconsistent access checks, missing-token behavior, verbose errors, schema-validation gaps, and regressions. Passing assertions do not prove complete coverage.

## Remediation guidance
Use environment-scoped lab credentials, avoid secrets in shared exports, assert positive and negative authorization cases, keep tests deterministic, and align assertions with the API contract.

## Validation
Run the collection with each role against a clean lab reset. Confirm a deliberately introduced lab weakness causes a failing assertion and that the fix restores passing tests.

## Simulated walkthrough screenshots
The following visuals illustrate the workflow and fictional training output. They are not genuine tool captures or scan evidence.
### Lab / request setup

![Simulated Postman API Security Testing screenshot 1](../../../_assets/screenshots/05-postman-collection.svg)

### Testing workflow

![Simulated Postman API Security Testing screenshot 2](../../../_assets/screenshots/05-postman-test-run.svg)

### Findings and remediation

![Simulated Postman API Security Testing screenshot 3](../../../_assets/screenshots/05-postman-results.svg)

## Evidence and reporting
Record approved scope, test date, lab version, account role, endpoint and method, sanitized request/response, expected versus observed behavior, impact, severity rationale, remediation, retest result, and limitations. Never publish real client identifiers, tokens, credentials, or personal data.

## Completion checklist
- [ ] Lab is isolated and uses synthetic data.
- [ ] Endpoints and test roles are documented.
- [ ] Requests and responses are sanitized.
- [ ] Findings are validated rather than inferred from tool alerts.
- [ ] Remediation and regression checks are documented.
- [ ] No real secrets or personal data are committed.

---
*Training material for authorized API security testing. Example results and screenshot content are fictional.*
