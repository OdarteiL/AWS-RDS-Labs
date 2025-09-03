# 🧹 Post-Lab Cleanup Instructions

## ⚠️ CRITICAL: Clean Up All Resources to Avoid Charges

### 1. RDS Instances Deletion

**Delete ALL RDS Instances:**
- Original MySQL instance
- PostgreSQL instance  
- Local read replica (if not promoted)
- Cross-region read replica
- Promoted read replica
- Restored instance

**Deletion Process:**
1. Select instance → Actions → "Delete"
2. Uncheck "Create final snapshot" (for lab purposes)
3. Check "I acknowledge that automatic backups will be deleted"
4. Type "delete me" to confirm
5. Click "Delete"

### 2. Manual Snapshots Cleanup

**Delete Manual Snapshots:**
1. Go to "Snapshots" in RDS console
2. Select your manual snapshots
3. Actions → "Delete snapshot"
4. Confirm deletion

### 3. Security Groups Cleanup

**Clean Up Security Groups:**
1. Go to EC2 → Security Groups
2. Delete the RDS security groups you created
3. (Only delete if no longer referenced by instances)

### 4. Cross-Region Resources

**Switch to us-west-2:**
1. Delete cross-region read replica
2. Delete associated security groups
3. Verify no resources remain

## ✅ Verification Checklist

- [ ] All RDS instances deleted (check both regions)
- [ ] All manual snapshots deleted
- [ ] Custom security groups deleted
- [ ] No remaining charges in billing dashboard

## 🔍 Verification Commands

```bash
# List all RDS instances
aws rds describe-db-instances --query 'DBInstances[*].[DBInstanceIdentifier,DBInstanceStatus]' --output table

# List all snapshots
aws rds describe-db-snapshots --query 'DBSnapshots[*].[DBSnapshotIdentifier,Status]' --output table

# Check security groups
aws ec2 describe-security-groups --query 'SecurityGroups[?contains(GroupName, `rds`)].GroupName' --output table
```

## 💰 Cost Monitoring

1. Check AWS Billing Dashboard
2. Review Cost Explorer for RDS charges
3. Set up billing alerts for future labs
4. Verify $0 charges after cleanup

## 🆘 Emergency Cleanup

If you're seeing unexpected charges:

1. **Immediate Actions:**
   - Stop all RDS instances
   - Delete all running instances
   - Remove all snapshots

2. **Contact AWS Support:**
   - If charges continue after deletion
   - For account-specific issues
   - For billing disputes

## 📊 Final Cost Report Template

Track your lab costs:

| Resource Type | Instance Count | Hours Used | Estimated Cost |
|---------------|----------------|------------|----------------|
| db.t3.micro | | | |
| Multi-AZ | | | |
| Read Replicas | | | |
| Backup Storage | | | |
| **Total** | | | **$** |

---

**Remember:** AWS charges by the hour for running instances. Even stopped instances may incur storage charges. Complete deletion is the only way to stop all charges.
