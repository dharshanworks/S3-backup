# S3 Backup Solution

## Objective

Implement a simple backup and restore solution using Amazon S3.

This project demonstrates how to:
- Backup application files
- Backup configuration files
- Upload backups to Amazon S3
- Restore files from Amazon S3 in case of data loss

---

## Architecture

```
Application Files
        │
Configuration Files
        │
        ▼
 Compress (ZIP)
        │
        ▼
 AWS CLI
        │
        ▼
 Amazon S3 Bucket
        │
        ▼
 Download Backup
        │
        ▼
 Extract ZIP
        │
        ▼
 Restored Files
```

---

## Technologies Used

- Amazon S3
- AWS CLI
- PowerShell
- ZIP Compression
- Windows

---

## Project Structure

```
S3-Backup-Exercise
│
├── app
│   ├── index.html
│   └── app.js
│
├── config
│   ├── application.properties
│   └── database.properties
│
├── backup
│   └── application-backup.zip
│
└── README.md
```

---

## Prerequisites

- AWS Account
- Amazon S3 Bucket
- AWS CLI Installed
- IAM User with S3 Permissions

---

## Configure AWS CLI

```bash
aws configure
```

Provide:

```
AWS Access Key ID
AWS Secret Access Key
Region
Output Format
```

Verify configuration:

```bash
aws s3 ls
```

---

## Backup Process

### Compress Files

```powershell
Compress-Archive `
-Path app,config `
-DestinationPath backup\application-backup.zip
```

### Upload Backup to S3

```bash
aws s3 cp backup\application-backup.zip s3://<bucket-name>/
```

Verify upload

```bash
aws s3 ls s3://<bucket-name>/
```

---

## Restore Process

### Download Backup

```bash
aws s3 cp s3://<bucket-name>/application-backup.zip .
```

### Extract Backup

```powershell
Expand-Archive application-backup.zip -DestinationPath .
```

The application and configuration files are restored successfully.

---

## Validation

- Backup ZIP created successfully.
- Backup uploaded to Amazon S3.
- Local files deleted.
- Backup downloaded from Amazon S3.
- Files restored successfully.

---

## Learning Outcomes

- Amazon S3 Storage
- AWS CLI Commands
- Backup and Restore Strategy
- File Compression
- Disaster Recovery Basics

---

## Future Enhancements

- Automate backups using PowerShell scripts
- Schedule backups using Windows Task Scheduler
- Versioned backups with timestamps
- Enable S3 Versioning
- Configure S3 Lifecycle Policies
- Encrypt backups using SSE-S3 or SSE-KMS

---

## Author

**Dharshan R**

B.Tech Information Technology

DevOps & Cloud Enthusiast
