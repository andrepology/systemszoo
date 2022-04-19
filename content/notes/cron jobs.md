>Term for "script that runs periodically", alias "cron job"
+ **cron**tab is a cli and scripting language in UNIX based OS
	+ `init-db` within [[kanban]] is a kind of cron job, in that it is paired to the synchronous execution of an app. 
	+ #todo: relation to web workers
+ Error handling is important here, and generally something we want a package to handle a la `axios` for HTTP requests. 

### Methods
+ Naive: Loops
	+ Blocking: stuck in permanent `while` , which is blocking to other code. 
+ Threaded loops
	+ Run forever, on an independently managed process and resolve blocking issue.  
	+ Poor error handing 
+ python-crontab
	+ unix-string with command, with a Python wrapper

## Scheduler Libraries
> Do the above, except with a nicer API and better handling. Some are products in and of themselves. 
+ Celery
+ APScheduler
+ Background thread custom
+ cron job
	+ service available to unix-based OS. 
	+ crontab command opens text editor on users crontab file
		+ `***** command`
			+ plain, unforgiving syntax for when to run
			+ command itself can be tricky
+ Prefect


+ Redis container
	+ redis: remote dictionary server, key-value store as opposed to relational
		+ ie no foreign keys, no SQL support for interaction 
		+ in-memory cahce, fast as a result
	+ Use to quickly do IO. 
