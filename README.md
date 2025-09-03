# AWS RDS Labs - Complete Learning Series

A comprehensive hands-on learning series covering Amazon RDS fundamentals, high availability, read replicas, and backup/recovery strategies.

## 📚 Lab Overview

| Lab | Topic | Duration | Key Skills |
|-----|-------|----------|------------|
| [Lab 1](lab1/) | RDS Instance Creation & Configuration | 45 min | Instance setup, security groups, connections |
| [Lab 2](lab2/) | Multi-AZ Deployment & High Availability | 45 min | Failover testing, availability zones |
| [Lab 3](lab3/) | Read Replicas & Performance Scaling | 60 min | Read scaling, cross-region replication |
| [Lab 4](lab4/) | Automated Backups & Point-in-Time Recovery | 40 min | Backup strategies, disaster recovery |

**Total Duration:** 3 hours 10 minutes

## 🎯 Learning Objectives

### Core RDS Concepts
- Database engine selection and configuration
- Instance classes and storage optimization
- Security group configuration and network access
- Connection management and endpoint usage

### High Availability & Disaster Recovery
- Multi-AZ deployment for automatic failover
- Cross-region read replicas for disaster recovery
- Backup retention and point-in-time recovery
- RTO/RPO planning and implementation

### Performance & Scaling
- Read replica creation and management
- Performance monitoring and optimization
- Load distribution strategies
- Replication lag management

## 🏗️ Architecture Patterns Covered

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Application   │    │   Application   │    │   Application   │
│     Tier        │    │     Tier        │    │     Tier        │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          ▼                      ▼                      ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Single RDS     │    │   Multi-AZ      │    │ Read Replicas   │
│   Instance      │    │   Deployment    │    │   + Multi-AZ    │
│                 │    │                 │    │                 │
│  Lab 1 Focus    │    │  Lab 2 Focus    │    │  Lab 3 Focus    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 📋 Prerequisites

- AWS Account with appropriate permissions
- Basic SQL knowledge
- Understanding of networking concepts
- MySQL/PostgreSQL client tools

## 🚀 Getting Started

1. **Clone this repository:**
   ```bash
   git clone <repository-url>
   cd AWS-RDS-Labs
   ```

2. **Start with Lab 1:**
   ```bash
   cd lab1
   cat README.md
   ```

3. **Follow labs in sequence** - each builds on previous knowledge

## 💰 Cost Management

### Estimated Costs (per hour)
- **db.t3.micro:** ~$0.017/hour
- **Multi-AZ:** 2x base cost
- **Read Replicas:** Additional instance cost
- **Backup Storage:** $0.095/GB-month

### Cost Optimization Tips
- Use `db.t3.micro` for labs (free tier eligible)
- Delete resources immediately after completion
- Monitor billing dashboard regularly
- Set up billing alerts

## 🔧 Lab Environment Setup

### Required AWS Services
- Amazon RDS (MySQL, PostgreSQL)
- Amazon EC2 (Security Groups)
- Amazon VPC (Default VPC acceptable)
- AWS CloudWatch (Monitoring)

### Tools Needed
- MySQL client or MySQL Workbench
- PostgreSQL client (psql)
- AWS CLI (optional)
- SSH client for EC2 connections

## 📊 Key Takeaways by Lab

### Lab 1: Foundation
- ✅ Engine selection impacts features and costs
- ✅ Instance classes should match workload requirements
- ✅ Security groups control database access
- ✅ Connection endpoints remain consistent

### Lab 2: High Availability
- ✅ Multi-AZ provides availability, not performance
- ✅ Failover time is typically 1-2 minutes
- ✅ Cost doubles with Multi-AZ enabled
- ✅ Applications don't need connection string changes

### Lab 3: Read Scaling
- ✅ Read replicas improve read performance
- ✅ Cross-region replicas provide DR capability
- ✅ Replication lag varies based on distance/load
- ✅ Promotion breaks replication permanently

### Lab 4: Backup & Recovery
- ✅ Automated backups enable point-in-time recovery
- ✅ Manual snapshots persist beyond instance deletion
- ✅ Recovery creates new instance, doesn't replace existing
- ✅ Backup retention affects storage costs

## 🎓 Exam Preparation

### Common AWS Certification Scenarios

| Scenario | Solution | Lab Reference |
|----------|----------|---------------|
| "Need 99.99% availability" | Multi-AZ deployment | Lab 2 |
| "Read-heavy workload performance issues" | Read replicas | Lab 3 |
| "Disaster recovery in different region" | Cross-region read replica | Lab 3 |
| "Accidentally deleted critical data" | Point-in-time recovery | Lab 4 |
| "Long-term backup retention for compliance" | Manual snapshots | Lab 4 |

## 🛠️ Troubleshooting Guide

### Connection Issues
```bash
# Check security group rules
aws ec2 describe-security-groups --group-ids sg-xxxxxxxxx

# Test connectivity
telnet <rds-endpoint> 3306
```

### Common Error Solutions
- **"Can't connect to MySQL server"** → Check security group and public accessibility
- **"Cannot modify to Multi-AZ"** → Ensure instance is in "Available" state
- **"Cannot create read replica"** → Enable automated backups on source
- **"Cannot restore to point in time"** → Check retention period and backup status

## 🧹 Post-Lab Cleanup

### Critical: Delete All Resources

1. **RDS Instances:**
   - Original instances (MySQL, PostgreSQL)
   - Read replicas (local and cross-region)
   - Restored instances

2. **Snapshots:**
   - Manual snapshots
   - Automated backups (deleted with instance)

3. **Security Groups:**
   - Custom RDS security groups
   - Verify no dependencies exist

4. **Cross-Region Resources:**
   - Switch to all used regions
   - Verify complete cleanup

### Verification Checklist
- [ ] All RDS instances deleted (check all regions)
- [ ] All manual snapshots deleted
- [ ] Custom security groups deleted
- [ ] No remaining charges in billing dashboard

## 📈 Performance Metrics Tracked

- Instance creation time
- Connection establishment time
- Query response times
- Failover duration
- Backup/restore duration
- Replication lag measurements

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for improvements.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**⚠️ Important:** Always clean up AWS resources after completing labs to avoid unexpected charges. Monitor your AWS billing dashboard regularly.
