# Rsnapshot Wrapper

## About

The standard rsnapshot cron configuration is actually quite unsafe, it will delete backups without confirming a new one exists and potentially lose all backups in a defined interval.

This wrapper sits around rsnapshot and solves those two problems, plus it lets you run the script from cron a lot more often with no additional overhead.

## Cron file /etc/cron.d/backups 

	PATH=/bin:/sbin:/usr/bin:/usr/sbin
	17 */3 * * * root /etc/rsnapshot/run_rsnapshot

run_rsnapshot attempts to be a "well behaved" unix cron script in that it will only echo text out to cron if there's a problem. So this will send me an email whenever anything goes wrong.

## Manually running

In this example I run the mythtv backup found in conf.d.examples/mythtv.conf manually.

My backups are currently recent enough, so I remove the success files:

	root@drudge:/etc/rsnapshot# rm last_success.d/mythtv.conf

I then just run the main wrapper:

	root@drudge:/etc/rsnapshot# ./run_rsnapshot
	(mythtv) Taking a snapshot
	(mythtv) Snapshot succeeded

Done.
