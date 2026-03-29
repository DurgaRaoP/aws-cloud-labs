# IAM Access Control — Key Learnings

## Architecture Built
- IAM Users → assigned to Groups → Groups have Policies
- Never attach policies directly to users
- Use Roles for EC2 instead of access keys

## Issues Resolved
**AccessDenied error:**
- Go to IAM Policy Simulator
- Identify missing permission
- Attach correct policy to group

## Best Practices Applied
- Root account: MFA enabled, no access keys
- EC2 instances: use IAM Role, never embed keys
- Least privilege: only grant what is needed
- Reviewed permissions using IAM Access Analyzer
