> Uber-simple flask app. 

+ As some exes of mine know, **I love it when things are done three ways**.
	+ Plainban
		+ A simple refactor of the one I worked on in class. 
	+ Plantban
		+ Garden of Tasks
	+ Templeban
		+ Temple of Self Interest


### Folder Structure
```
- kanban
	- frontend
		- src
			- server.js
			- components
				- App.js
				- App.css
		- node_modules
		- public
		- package.json
	- backend
		- venv
		- app.py
		- requirements.txt
	- sql
		- schemas/models
```


#worklog 
+ [[2022-03-20]]: time has floated by. To take this to completion.
	+ #pulse : time has really floated by. Emotional whiplash has been experienced. And I continue to experience it.
	+ [x] add delete
	+ [ ] refactor API to be RESTful and only work with HTTP defaults at URIs
		+ `tasks/<id>` 
			+ PUT
			+ DELETE
			+ GET
	+ [x] add move
	+ That was fast. like an hour. theres some inelegence but it works! congrats on first app.

+ [[2022-03-03]]: layering in draganddrop and physics
	+ Trying to ante up with dev speed #principle : there is no reason to wait
		+ Going to start with focusing on adding physics, experiment with state
		+ Target the boundaries of kanban boards. 
			+ self.getWidth ? Might need a declarative query
				+ document.body.clientWidth
					+ Remember the DOM trail with M&D
				+ first instance of the `useRef` [[React State]] hook
					+ #todo: what is this doing. 
		+ Reward yourself by reimplementing with new design.
			+ #idea: work on Ujeza's case game. Call it [[casesensitive]]
	+ Linting setup would be great.
	+ Put a baseline handle over it. 

+ [[2022-03-01]]: Tying the bow with React-Kanban
	+ [x] Sort out CORS issue by proxying to dev port
	+ [x] Fetch time from API and load into TODO
		+ using `axios`
			+ makes XHTTP requests with min repetition compared to alternative `fetch`
				+ `X`  , just like in `curl` , placeholds request types (POST, GET etc)
					+ Extremely straightforward API request/then: `axios.get(url).then()`
				+ defaults to JSON
					+ no need to specify `application/json` like with fetch
				+ error handling for each code is set under the hood
					+ Essential part of [[RESTful APIs]]
				+ ```const client = axios.create({ baseURL: "https://jsonplaceholder.typicode.com/posts"});```
					+ averts baseURl embedding
	+ [x] Set up database, load sample data, populate the boards
		+ [x] Fetch all data from db
			+ [x] Fetch a list of titles
			+ [x] Render in React
	+ [ ] Support deletions and moving, perhaps with icons attached to the thing?
		+ [x] Time to bring in anima + the twilio thing
			+ [x] Right arrow
			+ [x] Left Arrow 
			+ [x] Delete
		+ [x] "Batteries included" components and libraries
			+ [x] 2 lines -> Draggable over the screen
			+ [x] log state
	+ [x] Replace `fetch` with axios


+ [[2022-02-27]]: Connecting to React
	+ [x] Fetch time from flask API
		+ So, you ask if for a JSON object, and render it when the component is added as an effect
	+ [x] Render kanban HTML with time
		+ This was straightforwards, now need to reconfig API urls for each component? 
			+ Maybe this is how I should intro to Conext or Redux
	+ [x] Refactor form to controlled state
		+ Figuring out how to handle form data for react: don't use the DOM. Handle it in component state. So, first refactor the Kanban Form component, and get practice with callbacks. 
		+ controlled state means that the value and onChange of the form elements are managed with stat
		+ Manage form state with onChange
	+ [ ] Comms with the team
	  + #idea: understanding View frameworks (React) as a departure from templates
	+ [ ] Connect the kanban, potentially using marshmallow to setup the schema
	+ [x] #idea brutalban && templeban && posterbam
+ [[2022-02-26]] : Reading about connecting to React
	+ Moved notes out to (where?)
+ [[2022-02-25]]:  Connections to React and a Deeper Dive
	+ [x] For starters, installing the database
		+ Notes on current draft
			+ Posts and refreshes, with state stored on server. violate [[The 12 Factor App]] principles lol
				+ Does not append tasks, but replaces, defaults to TODO 
				+ controlled state is vital
		+ Use template schema from blog
		+ [x] Add <select> </select>  and re-render according to input
		+ [x] Config database
			+ SQLite is so fucking annoying. I missed a comma in the schema and that komked the whole thing. Bad tracing as well. but, I understand the script execution stuff better. Instead of a file, can just use a string. 
			+ This is what SQLAlchemy does: write in Python, let it handle the SQLite querying
		+ [x] Delete!
		+ [x] Do PCW
		+ [x] How does one-hot reloading work in Flask?
			+ Simply redirect to a string literal
	+ [x] Connect to React
	+ [ ] Begin styling/storybook? Let's see how this goes
+ [[2022-02-23]] : Quickstart Flask!
	+ Going to start with a form that simply adds to one of the few boards
	- [x] Set up venv in `kanban` folder
	- [x] Create \__init\__.py
		- [x] Config location and key
		- [x] Register basic view at '/': Kanban here soon!
		- [x] Register db
	- [x] Set up index view with 3 columns
		+ Boards
			+ To Do
			+ In Progress
			+ Done
		- [x]  New Task: `<HTML form>`
			+ taskName: string
			+ location: ENUM	
				{
				TO DO
				IN PROGRESS
				DONE
				}
		+ Task Schema
			+ taskName : string
			+ location: ENUM
			+ (creationDate) : Date
		
		 - [x]  app_factory
			+ init_db
			+ get_db
	- [x] board template
			+ for task in tasklist
				+ `<ul>` task `</ul>`
		
		
		+ /board
			+ fetch data from sql
			+ return kanban_template
		+ /create, POST