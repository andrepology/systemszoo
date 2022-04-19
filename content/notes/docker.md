

### Testing with Docker

+ [Docker](https://web.archive.org/web/20150512050508/https://www.docker.com/) is an open platform for developers and sysadmins to build, ship, and run distributed applications. 
	+ For our purposes, Docker containers give us access to a **jailed operating system that any of our services can run in** with **almost none of the overhead of a virtual machine**.

+ [Dockerfiles](https://web.archive.org/web/20150512050508/https://docs.docker.com/reference/builder/) are used to define an exact template for what each application needs, from operating system to libraries to open ports
	+ user no longer needs to install all the dependencies manually and then hope it works on their own computer, since this will all be taken care of in the Docker container. This means getting up and running is fast since the **host machine** requires nothing installed but the Docker service itself.
	+ Since your application likely has dependencies on other services (database, caching server, message queue, etc), you will need **multiple Docker files to bring up a working stack.**

+ [Docker Compose](https://web.archive.org/web/20150512050508/https://docs.docker.com/compose/) enables us to easily manage a collection of containers by defining them in a short yaml file.
```
web:
  build: webServiceAPI    # location of our Dockerfile
  volumes:
    - ../target:/build    # share directory to get compiled build from
  links:
    - database:database   # network link between containers
  ports:
    - "8080:8080"                  # expose port 8080 to host
        
database:
  image: mysql:5.5                # name of community a supported image
  environment:
    - MYSQL_ROOT_PASSWORD=veryComplexPassword


```

### Black box testing
+ exposes port 8080 so it can be reached from the host
+ To run our API tests all we have to do is point them at that port, and we are testing the Dockerized API instead of a service running directly on the host

### Scalability Testing
+ You can use compose to bring up any number of instances of the services in your stack with something like:
	`docker-compose scale web=10 database=3`
	
+ This is great for testing things like database clusters or load balancers. 
	+ I have seen hundreds of database containers run on a single laptop with no problem. **Try doing that with a virtual machine.**

### Configuration Testing
+ It is easy to add very invasive automated tests here as well. 
	+ Let’s say we want to automate the testing of different system configurations. 
	+ We usually use MySQL, but this service can also work with a Postgres backend.
	+ Just create a Postgres container ([or find an existing one on Dockerhub](https://web.archive.org/web/20150512050508/https://registry.hub.docker.com/_/postgres/)), and modify our test script to run as follows:
		-   Bring up new stack (with MySQL backend), Seed with data, Run API tests, Tear down stack.
		-   Bring up new stack (with Postgres backend), Seed with data, Run API tests, Tear down stack.
		-   Report on any differences in test results between MySQL and Postgres backends.

### Simplifying Development
+ In the past, some of our system tests used a different database technology than the production deployment. We used an in-memory H2 database since it is faster to bring up than a full database server

### Simplifying Testing
+ Now that our stack is Dockerized, anyone can easily run the tests. New developers can run tests against their new code right away, leading to fewer checked in bugs.
+ QA can focus on tasks beyond **regression testing**.


### Integration Testing With Docker Compose
+ Monolithic server
	+ One server, one database
		+ Node
		+ RethinkDB
	+ Testing `create` has hidden dependencies
		+ Db installed and running
		+ App framework installed
		+ App has to be running
		+ CURL on sys path
		+ Existing database
	+ side effects
		+ local development database is shared with the test database.
		+ So every time you run your integration test, you lose all of your development data 😭.

+ Intergration testing 
	+ Separate dockerfile
	+ Sometimes it’s nice to lose all your data, and when you’re running tests it’s essential. It’s really easy to accomplish this with Docker compose by spinning up your database without a mounted volume for data. This means that when you destroy your container, the data goes along with it.
	+ Here’s an example Docker Compose file that would just spin up an ephemeral database (RethinkDB).
		**integration-test/docker-compose.yml**
		```YAML
		version: '2'
		
		services:
		  rethinkdb:
		    image: rethinkdb
		    expose:
		      - "28015"
		```
	+ App Container
		+ The next step is to containerize the application you’d like to test. It needs to build/run the application, link to the database and expose a port to be used for testing.
	+ Integration Test Container
		+ Now we’ve got our database and application, let’s build the testing container. This container needs to POST against the /create endpoint on my-service and inspect the database for changes. To accomplish this I used tape and request-promise to inspect the endpoint.
	+ Bringing It All Together
		+ With all of the automation in place we need to tie everything together and do some cleanup after the test finishes. To accomplish this we can use Docker wait to block the script and retrieve the exit code of the test. We’ll use that code to output a message (PASS/FAIL) and exit the master script with the same exit code. This is useful because most (if not all) CI environments use an exit code to determine if the tests passed or failed. We’ll also grab the test container logs and print them out to provide context for when things fail. Here’s an (extremely verbose) script that does everything we need to run our integration tests locally or in CI.



# The basic idea:
1.  Create a docker image for each type of service that needs to be run. Databases should be pre-migrated and perhaps with some initial data to speed up the time it takes to run each integration test. Each service will have its own container, and different services can sometimes reuse the same underlying image.
2.  Write mock services for 3rd party services. We do this by putting some basic code into a python file and then running it with a standard lib [python image](https://hub.docker.com/_/python/). The python file can just be mounted into the container when run.
3.  Use [docker-compose](https://docs.docker.com/compose/) to declare the service infrastructure for each test case in a YAML file. This makes describing each test case much more concise, and error cases (where a service) is down are much easier to add.
4.  Expose endpoints for the end to end tests. This allows external testing code to hit the endpoints and check for the expected behavior.
5.  Start up the infrastructure with docker-compose and simply make API requests to the exposed endpoints. Sometimes you may need to add additional checks to make sure the interaction is actually happening.

# Example

I put together a sample integration tests setup [here](https://github.com/tomlinford/docker-integration-sample). It’s a basic integration test, checking an interaction between a sample Django app and [vault](https://www.vaultproject.io/). It’s a simple REST API that allows users to store secrets by making a POST to /secrets/. Secrets can be deleted and retrieved by using the detail endoint, /secrets/{id}/. Each test case takes around 4 seconds to run, which involves setting up the entire infrastructure, running the tests, and tearing it down. Some things to note from the sample integration tests:

-   The end to end tests are written with unittest from the Python standard library. These tests can be written in any language and in any testing framework. Additionally, the tests could even be run from a docker container — you’d just need to use the [docker image](https://hub.docker.com/_/docker/) as a base, install docker-compose and whatever other tools you need, and then mount /var/run/docker.sock.
-   The sample app has a Secret model, which just references the User model and has a primary key, which is used as the key for storing the secret in vault. The Secret model has no additional information, so if the database storing the Secret model is compromised, then the users’ secrets wouldn’t be compromised. However, the value of the secret that the user has stored can be easily fetched through the API, which internally accesses a Python property of Secret which then makes the request to vault.
-   The database for the sample app is just a sqlite database stored in /tmp/, so it isn’t persisted between runs. This does mean that the database needs to be migrated for each test case, which is ok with a small example but would take far too long with the typical monolithic application.
-   The Dockerfile for the sample app is very simple, it pretty much just installs the requirements. With the image created from the Dockerfile, the app can be run. Additionally, if the app had any workers or management commands in the same codebase, they could just reuse the same docker image. Here’s the Dockerfile:

FROM python:3.5.1  
ADD repos/app/requirements.txt /tmp/requirements.txt  
RUN pip install — no-cache-dir -r /tmp/requirements.txt  
EXPOSE 8000  
WORKDIR /app

-   The vault container did not need a custom Dockerfile, as there was already a vault image on docker hub that could be used. All necessary information for the vault container was managed in just a couple of lines:

vault:  
  entrypoint: /bin/bash  
  command: /vault/run.sh  
  image: cgswong/vault:0.3.1  
  expose:  
    — 8201  
  volumes:  
    — ../../docker/vault/:/vault/

-   The configuration files for the vault container are simply stored in docker/vault/, which just gets mounted in the container at /vault/ when the container is run.
-   The app configuration in the docker compose file is equally simple:

app:  
  command: /bin/bash /mnt/run.sh  
  image: integration-app  
  volumes:  
    — ../../repos/app/:/app  
    — ../../docker/app:/mnt  
  ports:  
    — “8000:8000”  
  links:  
    — vault

-   The link to the vault container is listed in the links section, which adds the VAULT_PORT_8201_TCP_(ADDR|PORT) environment variables (since port 8201 is exposed in the vault configuration). Port 8000 is forwarded, which allows access to the API from outside of docker.

# Continuous Integration

These tests can be run in the CI tool of your choice as well. We use Jenkins and have the integration tests setup to run whenever tests for another repo are run, which occurs when new code is pushed to that repo. The command for running the tests is a simple “make test” and with our testing framework (nose) it’s easy to export the tests results into an XML file that Jenkins understands.

# Conclusion

So there it is, a great way to setup integration tests. Quick enough to run often and simple enough to make adding new cases easy.

At Robinhood we take pride in our robust and quality code, and these integration tests are an important component for that. And of course, [we’re hiring](https://jobs.lever.co/robinhood)!