# AWS Organizations Policy Catalog

A security-oriented catalog of AWS Organizations policy baselines:

- **SCPs**: principal-side maximum-permission guardrails for IAM users and roles in member accounts.
- **RCPs**: resource-side maximum-permission guardrails for the AWS services that support RCPs.
- **Declarative policies**: service-level configuration policies that enforce durable configuration rather than API authorization.

## Scope and safety

This is a reference library, not a one-click deployment. Test each policy in a sandbox OU, account for required AWS services and break-glass roles, then attach progressively. SCPs and RCPs do not affect the AWS Organizations management account; declarative policies can.

The catalog deliberately does **not** claim that every AWS service supports RCPs or declarative policy types. See `coverage/` for the current capability map and primary AWS references.

## Layout

- `scp/` — organization-wide authorization guardrails.
- `rcp/` — resource perimeter guardrails plus supported-service manifest.
- `declarative/` — policy-type inventory and JSON examples for Amazon EC2, Amazon S3, and tag standards.
- `coverage/` — machine-readable service and policy-type support records.

## Apply

Use the policy type appropriate to the file:

```sh
aws organizations create-policy \
  --type SERVICE_CONTROL_POLICY \
  --name deny-leaving-organization \
  --content file://scp/deny-leaving-organization.json
```

A declarative EC2 policy instead uses `DECLARATIVE_POLICY_EC2`; an S3 declarative policy uses `S3_POLICY`. Review the AWS Organizations policy-type documentation before creating or attaching any policy.

## Sources

This catalog is aligned to the AWS Organizations documentation for [SCP syntax](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_syntax.html), [RCP support](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_rcps.html), and [declarative policy types](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_declarative_policies.html). AWS adds capabilities over time; revalidate the coverage manifest before adoption.
