
NVM
.npmrc


retire.js
Node Security Platform
-------------------------
npm install nsp -g
nsp check


**When to run security check ?**

Manually => Easy to forget
npm install => May be issue later
production build => expensive to change
pull request => expensive to change
npm start => Slows start slightly (Recommended) 


**Alternate to development server**
1. http-server
2. live-server(support live reload)
3. express ( competitors koa and hapi )
4. budo
5. webpack dev server (supports hot reload)
6. Browsersync(Dedicated Ip for sharing work on LAN, All interactions remain in sync, 
	Great for cross device testing, integrates with webpack, gulp, Browserify)
	However Browsersync doesn't expose a public IP for testing outside of your local network.
	
	
**Sharing work-in-progress** 

	1. localtunnel
	Easy share work on your local machine.
	Offers an elegant way to expose your local host via public url
	It punches hole in firewalls so that ur local machine can operate as a web server
	 i.npm install localtunnel -g
	 ii. start ur app
	 iii. lt --port 3000 --subdomain abhishek
	 not fully Secure
	
	2. ngrok
	Secure tunnel to ur local machine
	i. Signup
	ii.Install ngrok
	iii. Install authtoken
	iv. Start ur app
	v. ./ngrok http 80
	
	3. surge
	4. now
	Quickly deploy ur app to cloud
	
	i. npm install -g now
	ii. create start script
	iii. now 
	
	**Automation**
	1. Grunt
	2. Gulp
	3. npm scripts
	
	 	Grunt is the first task runner which uses configuration over code via grunt file. It is basically a big chunk of JSON that configures grunt to work with plugins. Grunt is file oriented, it writes files to disk after each step in an automation process. So its reads from disk as input to subsequent steps.
		
		Gulp focuses on in-memory streams which gulp calls pipes. In short, with gulp you don't have to write to disk after each step in task. Instead we simply pipe the o/p of previous step to the next step in memory. This is why Gulp is faster than Grunt. code over configuration.
		
		
	npm scripts
	--------------
	If we write a script called **pre start**, then by convention it will run out start script.
	npm scripts support convention based **pre** and **post** hooks. So any scripts that you prefix with the word **pre** will run before the script with the same name and **post** will run after the script with the same name.
	
	
	**Popular Transpilers**
	--------------
	1. Babel
	2. TypeScript
	3. Elm
	
	
	**Bundling**
	-----------------
	npm packages uses commonJS pattern node can handle this. But browser don't understand it.
	So you need to bundle npm packages into a format that the browser can consume.
	But bundlers aren't just for apps that run in the browser. You ay use a bundler to package any Javascript into single file or into separate files for different portions of your app. Allow to create separate bundler allows the user only to download the relevant js for the page for initial load. This saves bandwidth and speeds page load.
	
	You can use bundler for node also since node's require is slow. But bundling your code for node, you can compile away the require calls, which can improve performance.
	1. Browserify
	The first bundler to reach mass adoption
	Bundle npm packages for the web 
  Large plugin ecosystem, adding functionality via minification, linting, and transpiling and so on via plugin.
	
	2. Webpack
	Use loaders to handle ur css,images,fonts and more intelligently. Webpack can import all these files  types just like js files.Built-in hot reloading web server. 
	3. Rollup
	4. JSPM
	
	
	**Different module format**
	-------------
	1. IIFE (past)
	2. AMD (past)
	3. CommonJS(standard)
	4. UMD (combination of AMD & CommonJS)
	5. ES6/ES2015 (standard & future)
	
	Why ES6?
	1. They are standardized
	2.  Can't declare them dynamically, statically analyzable.
			Improved autocompletion support.
			Intelligent refactoring.
			Fails fast and easy to debug.
			Tree shaking(Dead code elimination)
	3. Easy to read than AMD, UMD
	
	
	
	**SourceMap**
	Once we start bundling, minifying and transpiling our code, we create a new problem. Oure code become impossible to read when it is running in the browser. So how to debug? The solution is sourcemap. SourceMap maps the bundled, minified and transpiled code back to the original source. This means what when we open our browser developer tool and try inspect our code we'll see the original ES6 source code. U might be wondering how minifying the code actually save any bandwidth, if we have to generate a big map back to the original source? The beauty of SourceMap is they are only downloaded if you open the developer tool. This way users won't even download the sourcemap, but they'll be available for u in case of an issue arises.
