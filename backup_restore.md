# Installation and configuration of our infrastructure using ansible playbook:
ansible-playbook infra.yaml

# MySQL data restoration from backup:
**To download the MySQL backup use backup user:**
```
duplicity --no-encryption restore rsync://yyjjjjy666@backup.spray.gel//home/yyjjjjy666/mysql /home/backup/restore/
```
**To restore MySQL backup run this command as a root:**
```
mysql agama < /home/backup/restore/agama.sql
```

# InfluxBD data restoration from backup
**To download the InfluxDB backup use backup user:**
```
duplicity --no-encryption restore rsync://yyjjjjy666@backup.spray.gel//home/yyjjjjy666/influx /home/backup/restore/
```

**To restore InfluxBD backup run this pack of command as a root:**
```
service telegraf stop
influx -execute 'DROP DATABASE telegraf'
influxd restore -portable -database telegraf /home/backup/restore
service telegraf start
```
