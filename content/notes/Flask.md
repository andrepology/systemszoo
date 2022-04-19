> A [[Backend]] microframwork

+ Flask is increments functionality through **higher-order functions** or **registration with decorators**
	+ Views are url endpoints with logic and rendering in a view function that is bound to the app or blueprint instance (`/register`)
	+ Blueprints group together similar views (`/register`, `/login` etc.) in modules
		+ Keeps code separable and maintainable. 
	+  Views -> Blueprints -> Single App Instance
		+ Generally, we want to separate concerns by grouping functionality in different folders, so blueprints have thier own files
		+ There is good control over the kind of decorators. 
			+ `app.teardown_appcontext(close_db)` closes the database connection after a response. 
			+ For example, to ensure a user is logged in, we use:
		```python
		def login_required(view):
		    #this bit is related to namespace or sthn
		    @functools.wraps(view)
		    def wrapped_view(**kwargs):
		        if g.user is None:
		            # url_for returns the url for a given view function
		            # 'auth.login' -> '/auth/login'
		            return redirect(url_for('auth.login'))
		        return view(**kwargs)
		
		    return wrapped_view
		```
		+ Extending functionality is a matter or composing higher-order functions from primitives
			+ For example, in `db.py`
		
### Folder Structure
```
flaskr /*Project Code*/
	templates
		auth
		blog
	static
		/*for static files (stylesheets)*/
	auth.py
	blog.py
instance
venv /* Dependencies */
```

+ App scope
	+ An app is instanced using an app factory in \__init\__.py. 
	+ It comes with special variables: `g, current_app`  that allow handling in specific contexts
		+ g is assigned the database, the user, and often shares data with `session`
	+ Handling
		+ `abort`
		+ `redirect`

### Jinja Templates
+ Are akin to [[JSX]] and can inject python code into blocks, delimited using `{%block var %}` and `{% endblock %}` syntax.
	+ Supports for and if control flow, but similarly needs delimiting with endfor and endif
	+ We can **extend** base templates through substitution
+ Used by calling `render_template` in the **return** of a view
	
### Storing Data
+ A schema defines the column structure of the sqlite database, which is stored in the instance folder during a session. 
+ schema.sql defines the `user` schema using:
	```sql
	  
	CREATE TABLE user (
	
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	
	username TEXT UNIQUE NOT NULL,
	
	password TEXT NOT NULL
	
	);
	
	```
	+ For each kind of thing we want to store, we need a new schema. 
		+ Defines name and type of data being stored (id INTEGER)
		+ Relationships to other entities
	+ We need to parse it back using `db.executescript(f.read().decode('utf8'))` later in `db.py`
### Reading Data
```Python
g.user = get_db().execute(
            'SELECT * FROM user WHERE id = ?', (user_id,)
        ).fetchone()

```
+ These can be vulnerable to injection attacks. 