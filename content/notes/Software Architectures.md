
1. Backend + SPA
  + Flask using the MVC [[Architecture]]
    + Files are served from backend
    + React app provides interaction with users
    + Cons:
      + Mixed and hard to extend tech
2. Two-Tier Architecture 
  + Decouples React UI from Flask Backend functionally and builds communication via #todo an API exposed by the server.
	  + #todo: Sim the API backend with mock requests
    + Can be deved as separate entities
    + Easier deploy


### 2 Tier React-Flask Flow
+ Flask starts and API is exposed
+ React UI is loaded by browser
+ React initiates login, gets credentials
+ React sends credentials to API server
+ Flask API checks the [[credentials]], issues the JWT token
+ React saves user info and JET token
+ Access to private zone is granted 

+ #todo: CORS middleware
		+ Something to do with cross origin config
		+ SQLAlchemy before Marshmallow
	+ `mange.py` for managing deployment, init db, check shcema changes, migrate to recent version
	+ schemas vs models
		+ Marshmallow simplified making schemas from more well-typed Models
			+ Remember how finicky SQL was to write
			+ Serialisation
	+ Use pydont-env and a `.flaskenv` file to not do the export all the time
	+ config "proxy" to flask port to avoid cross-origin issues
	+ update commands in scripts to start api
		+ stack traces and --no-debugger
	+ add `venv __pycache__` to `.gitignore`. 
		+ `git add .gitignore package.json api
	+ what are Resources
	+ Validation


