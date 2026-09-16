# Policy adoption checklist

1. Enable all AWS Organizations features and the required policy types.
2. Replace every placeholder (for example, the RCP organization ID).
3. Validate JSON and test the exact policy against a sandbox account or OU.
4. Confirm critical operations, service-linked roles, automation roles, and break-glass access still work.
5. Attach first to a test OU; inspect CloudTrail and service errors.
6. Roll out in stages and retain a documented rollback procedure.

## Important distinctions

- SCPs limit principals in member accounts. They do not grant access.
- RCPs limit supported resources in member accounts. They do not grant access and cannot use a bare `*` Action in customer-managed RCPs.
- Declarative policies enforce service configuration and can affect the management account.
