> The [twelve-factor app](https://12factor.net/) is a methodology for building software-as-a-service apps that use declarative setup automation, maintain clean contract and portability, deploy on modern clouds, scale up, use CI for max agility

+ Software Erosion
	+ **Dynamics of collaboration**
	+ Dynamics of the **growth** of an app


1. Codebase
	+ **Principle**: One codebase tracked in revision control, **many deploys**
		+ Deploys are running instances of the app
			+ production, staging, dev1, dev2 etc
	+ **Rationale**: centralisation! 
2. Dependencies
	+ **Principle**: Explicitly **declare and isolate** dependencies in a manifest
		+ A twelve-factor app never relies on implicit existence of system-wide packages
		+ Uses a dependency isolation tool for other deps to not leak in
	+ **Rationale**: Simplifies setup for new devs, just run install
3. Config
	+ **Principle**: Store config in the environment variables (env)
		+ Everything that might vary between deploys
			+ Resource handles to db
			+ Credentials
			+ Per-deploy values, like canonical hostname (ports etc.)
			+ 'dev' mode will need dev dependencies, for example
		+ Separation between config and code
			+ Code is the same between deploys, config varies			
4. Backing Services
	+ Principle: The code for a twelve-factor app makes no distinction between local and third party services.
		+ A _backing service_ is **any service the app consumes over the network** as part of its normal operation
		+ Datastores, messaging/queueing systems, STMP services, caching systems
		+ A deploy of the twelve-factor app should be able to swap out a local MySQL database with one managed by a third party (such as Amazon RDS) without any changes to the app’s code.
			+ The twelve-factor app treats these databases as attached resources, which indicates their **loose coupling to the deploy they are attached to**.
	+ Rationale: Resources can be attached to and detached from deploys at will.
		+ if the app’s database is misbehaving due to a hardware issue, the app’s administrator might spin up a new database server restored from a recent backup. The current production database could be detached, and the new database attached – all without any code changes.
5. Build, Release, Run
	+ Principle: The twelve-factor app uses strict separation between the build, release, and run stages.
		+ Build: converts codebase at a certain commit into exec/bin executable
		+ Release: combines with current config, all pieces for env
		+ Run: runs in execution env
	+ Rationale: Ease of management
		+ the `Capistrano` deployment tool stores releases in a subdirectory named releases, where the current release is a symlink to the current release directory. Its `rollback` command makes it easy to quickly roll back to a previous release.
6. Processes
	+ Principle: Execute the app as one or more stateless processes
		+ Twelve-factor processes are **stateless** and **share-nothing**
			+ Any data that needs to persist must be stored in a stateful backing service, typically a database.
			+ filesystem of the process can be used as a brief, single-transaction cache
			+  twelve-factor app never assumes that anything cached in memory or on disk will be available on a future request or job
			+ Sticky sessions are a violation of twelve-factor and should never be used or relied upon.
7. Port Binding
	+ Principle: Export services via port binding
		+ Web apps are sometimes executed inside a [[webserver container]].
		+ The twelve-factor app is completely self-contained and does not rely on runtime injection of a webserver into the execution environment to create a web-facing service. The web app exports HTTP as a service by binding to a port, and listening to requests coming in on that port.
			+ http://localhost:5000/
		+ typically implemented by using dependency declaration to add a webserver library to the app, such as Tornado for Python
8. Concurrency
	![[Screenshot 2022-02-23 at 9.49.08 AM.png]] 
	+ #principle : scale out via the process model
		+ Any computer program, once run, is represented by one or more processes
			+ #todo: relation to threading?
			+ HTTP requests may be handled by a web process, and long-running background tasks handled by a worker process.
		+ Twelve-factor app processes should never daemonize or write PID files.
9. Disposability
	+ #principle Maximize robustness with fast startup and graceful shutdown
		+ The twelve-factor app’s processes are disposable, meaning they can be started or stopped at a moment’s notice.
		+ Processes should strive to minimize startup time.
		+ Processes **shut down gracefully when they receive a [SIGTERM](http://en.wikipedia.org/wiki/SIGTERM)** signal from the process manager.
			+ For a web process, graceful shutdown is achieved by ceasing to listen on the service port (thereby refusing any new requests), allowing any current requests to finish, and then exiting.
		+ Processes should also be robust against sudden death, in the case of a failure in the underlying hardware. 

10. Dev/Prod Parity
	+ #principle: Keep development, staging, and production as similar as possible
		+ Differences in dev/prod are based on 
			+ Time gap: devs take a while to write code
			+ Personnel Gal: devs write code, ops deploy
			+ Tools gap: difference in stack
		+ CD/CI keeps the gap between these small
			+ Authors/deployers are same
			+ Envs are kepy similar
			+ Time is kept short
		+ Parity is esp important with [[Backing Services]]
			+ The twelve-factor developer resists the urge to use different backing services between development and production
11. Logs
	+ #principle : Treat logs as event streams
		+ Logs provide visibility into the behavior of a running app
		+  In server-based environments they are commonly written to a file on disk (a “logfile”); but this is only an output format.
		+ See [[heroku]]'s `heroku logs --tail`
	+ A twelve-factor app never concerns itself with routing or storage of its output stream. It should not attempt to write to or manage logfiles. 
		+ each running process writes its event stream, unbuffered, to stdout
		+ During local development, the developer will view this stream in the foreground of their terminal to observe the app’s behavior.
	
12. Admin Processes
	+ #principle : Run admin/management tasks as one-off processes
		+ One-off admin processes should be run in an identical environment as the regular long-running processes of the app.




Theory

(II) What does Python use for dependency management, and how do we use it?
	pip3 or pipenv
(III) How do we set and access environment variables in Python / Linux?
	use the `export` keyword, and `os.environ` , a dict of all variables. 
(III) What sort of variables do we definitely not want to store in our codebase?
	API keys, secret keys, passwords
(IV) What are some example **connection strings for SQL servers**? Be sure to specify different **[[SQL]] dialects** in your answer.
	`Server=myServerAddress;Database=myDataBase;Trusted_Connection=True;``	
(VI) What are the benefits of a stateless app?
	Stateless apps run consistently and. 
	
(VIII) What does it mean to scale an app vertically? What does it mean to scale an app horizontally? What is wrong with vertical scaling?
	Horizontally: add more unique processes
	Veritcally: add more threads
(XI) What sort of questions can log files help answer?
	Requests made, timestamp, when the server turns on/off
(XII) The twelve factor app suggests that admin processes be run separately from the app. Does this mean that there is no role for admin users in your app? Explain your answer.
	I'm not sure. 

	
Final Project
(I) How well does your final project adhere to the guideline of a "one-to-one correlation between the codebase and the app"?
	Unsure yet, but if we can just do `git push heroku master` then there is a one to one correspondance, as everything in the latest commit in the master will be built and deployed. 
(III) What sort of issues might arise if someone got access to a copy of your final project's source code?
	Hacking. Not sure why they would want to. 
(IV) Is it possible to use a different backing service in your final project without editing any code?
	If we have a .sql file and a single scheme, then we should be able to. Right now, flask manages the creation/deletion/teardown of database applications. 
(V) How clearly separated are the developing, building, staging, and production phases in your final project? Are there any aspects of your final project that could be improved?
	We should have branches/CI set up. 
(IX) What sort of issues might be encountered in your final project if the server went down hard?
	We might not be able to load anything/handle any requests, unless cached. 
(X) What differences are there between the environment that you develop in, and production? Is it possible to make those two environments more similar?
	We might have dev dependencies/ports when running locally. The former can superset the latter. 
(XI) Is it possible for something to go wrong when your final project is running and nothing will be logged? How much more work would it be to make sure that the error gets caught?
	We might need print statements everywhere. Which is tragic