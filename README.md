# rsnapshot-runner

## About

The standard rsnapshot cron configuration is actually quite unsafe, it will delete backups without confirming a new one exists and potentially lose all backups in a defined interval.

This wrapper sits around rsnapshot and solves those two problems, plus it lets you run the script from cron a lot more often with no additional overhead.

## Cron file /etc/cron.d/backups 
	PATH=/bin:/sbin:/usr/bin:/usr/sbin
	17 */3 * * * root /etc/rsnapshot/run_rsnapshot
