# AWS Samples–inspired SCP subset

These policies are adapted from the control categories in [aws-samples/service-control-policy-examples](https://github.com/aws-samples/service-control-policy-examples). They use a deny-list strategy and assume an appropriate allow policy (such as FullAWSAccess) remains attached.

## Included controls

| Policy | Purpose | Required customization |
| --- | --- | --- |
| `deny-security-telemetry-tampering.json` | Protects CloudTrail, AWS Config, and GuardDuty administration from unapproved changes. | Replace the break-glass role ARN. |
| `protect-sensitive-s3-bucket.json` | Stops destructive changes to a specifically named S3 bucket and its objects. | Replace `BUCKET_TO_PROTECT`. |
| `deny-root-credential-management.json` | Prevents creation, alteration, or removal of root access keys and password credentials. | Replace the break-glass role ARN if required. |

The catalog already includes the AWS Samples baseline that denies `organizations:LeaveOrganization`; it was not duplicated here.

## Rollout

Attach to a sandbox OU first. Confirm CloudTrail/Config/GuardDuty automation and break-glass operations still work, then expand gradually. These SCPs restrict maximum permissions; they do not grant access.
