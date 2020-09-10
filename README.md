# AWS Backup

The following cloudformation template delivers a simple AWS Backup Manager vault and plan which backups systems based on tag selection. Add this to your account within a specific region to enable a backup solution. The following below details the backup plans and the tag selectors.

## Backup Plans

The AWS Backup solution delivers several tiers for managing backups which is based on the defined Recovery Point Objective (RPO).

| Backup Plan Name | RPO | Runs Every | Tagging Schema |
| --- | ---------- | -------------- | --- |
| Default | 24 Hours | Runs backups on Daily, Weekly, and Monthly rules | `AWS-Backup:Default` |
| Daily | 24 Hours | Runs at 5 AM UTC daily | `AWS-Backup:Daily` |
| Weekly | 7 Days | Runs 5 AM UTC on Saturdays | `AWS-Backup:Weekly` |
| Monthly | ~31 Days | Runs on the 1st of the month at 5 AM UTC | `AWS-Backup:Monthly` |

## Backup Storage Lifecylce

The following details each rule set and the duration the backups are kept:

| Backup Rule | Move To Cold Storage (Days) | Delete After (Days) |
| ----------- | -------- | ------- |
| DailyBackups | NA | 35 |
| WeeklyBackups | NA | 90 |
| MonthlyBackups | 90 | 1825 |
