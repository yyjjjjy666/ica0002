# Backup coverage
Backup service covers only next services:
_Database_ services - **MySQL** and **InfluxDB**. (Those services conatin user data, which can't be restored by ansible playbook).
---
# RPO (recovery point objective)
text
---
# Versioning and retention
2 types of backup: **full** and **incremental**.
Full backup contain all data from services which are backed up. Full backup is done on every 28 days.
First incremental backup retain difference from the last created full backup, second incremental backup retain difference from in the data relative to the last created incremental backup.
All backups are retained for 28 days (4 weeks), but only 28 versions of backups can be stored at the same time.
Backups that are older than 29 days are deleted every Saturday at 3am.
---
# Usability checks
Usability of the last backup is checked every 7 days and tested in virtual environment setup, simulating our real infrastructure.
---
# Restoration criteria
Backup should be restored only if stored data was corrupted, stolen, modified by unathorized 1st or 3rd party or deleted.
---
# RTO (recovery time objective)
Recovering of whole infrastructure may take up to 2 hours. 