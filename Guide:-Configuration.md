So you got Sails.JS installed now and its loading up your awesome new project.  What? thats not good enough? OK, lets see what we can configure to make it better for your needs!!!

# Overview of Configurations
One of the major advantages of Sails.JS that makes it such a powerhouse MVC is the fact that is incredibly flexable.  As with most porgrams now days, Sails.JS has configurations files.  Below is a list and short explination of each.

* <a href="#adapters.js">adapters.js</a>      (This file handles database/datasource adapters)
* <a href="#application.js">application.js</a>   (This file handles General settings for your application)
* <a href="#assets.js">assets.js</a>        (This file handles the asset settings for CSS/Js/styles and other resources)
* <a href="#bootstrap.js">bootstrap.js</a>     (This file holds code that needs to be run before the app launches)
* <a href="#locales">locales</a>          (Folder that holds locale specific settings)
	* <a href="#english.js">english.js</a>   (This file handles translated strings for Locale use)
* <a href="#local.js">local.js</a>         (This file is included in the `.gitignore` and won't be pushed up to your git repository.  It handles any LOCAL overrides needed)
	* <a href="#local.ex.js">local.ex.js</a>      (This is an example file of local.js)
* <a href="#policies.js">policies.js</a>      (This file defines policies that are used to grant or deny access to users)
* <a href="#routes.js">routes.js</a>        (This file contains all the user specified routes for the system.  The system will attempt dynamic routing if this is blank)
* <a href="#views.js">views.js</a>         (This file handles all view related settings, such as the view engine and layout)

<span id="adapters.js"></span>
# adapters.js
The adapters.js file is where you will specify your database options for the entire app.  Lets take a look at the file and get familiar with all the parts.

```javascript
// Configure installed adapters
// If you define an attribute in your model definition, 
// it will override anything from this global config.
module.exports.adapters = {

	// If you leave the adapter config unspecified 
	// in a model definition, 'default' will be used.
	'default': 'disk',
	
	// In-memory adapter for DEVELOPMENT ONLY
	// (data is NOT preserved when the server shuts down)
	memory: {
		module: 'sails-dirty',
		inMemory: true
	},

	// Persistent adapter for DEVELOPMENT ONLY
	// (data IS preserved when the server shuts down)
	disk: {
		module: 'sails-dirty',
		filePath: './.tmp/dirty.db',
		inMemory: false
	},

	// MySQL is the world's most popular relational database.
	// Learn more: http://en.wikipedia.org/wiki/MySQL
	mysql: {
		module		: 'sails-mysql',
		host		: 'YOUR_MYSQL_SERVER_HOSTNAME_OR_IP_ADDRESS',
		user		: 'YOUR_MYSQL_USER',
		password	: 'YOUR_MYSQL_PASSWORD',
		database	: 'YOUR_MYSQL_DB'
	}
};
```

OK, so the first thing you may have noticed is the _default_ setting.  This is set to _disk_ by default.  Disk means that the data is stored on the local file system instead of in a database.  You can change this to any of the other definded options below that.  This is the default that will be used throughtout your entire app.  If you need to override this on a per model basis, you can do that inside the model itself.  See [Models](Models).

momery:  This is an option for _'default':_ .  Memory stores all data in memory.  This memory is erased when the server is shutdown.

disk:  This is an option for _'default':_ .  Disk stores all data on disk in the .tmp folder.  This is persisted through restarts.

mysql:  This is an option for _'default':_ .  Mysql stores all data in a MySQL Database.  This is persisted through restarts.  This requires the setup of a Mysql server either locally or remote.

### Future
As more adapters are created, they will be added to this guide.  Sails.JS plans to support a wide viriaty of data source adapters.

<span id="application.js"></span>
# application.js
The application.js file hold all the generalized configuration options for an application.  This means that everything that doesn't have its own file can be found here.

<span id="assets.js"></span>
# assets.js

<span id="bootstrap.js"></span>
# bootstrap.js

<span id="locales"></span>
# Locales

<span id="english.js"></span>
## english.js

<span id="local.js"></span>
# lacal.js

<span id="local.ex.js"></span>
### local.ex.js

<span id="policies.js"></span>
# policies.js

<span id="routes.js"></span>
# routes.js

<span id="views.js"></span>
# views.js