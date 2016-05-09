# liferay-angular2-hook
Liferay AngularJS 2 Hook 

This hook adds the required dependencies for AngularJS 2 to Liferay, so they can be referenced by portlets without needing to package them inside the war file.

NodeJS and npm will be downloaded when executing the maven build for the first time, after which 'npm install' is run to fetch the required node_modules.
Extra dependencies can be added to src/main/webapp/npm/js/package.json

After deploying the hook the node_modules will be available at "/js/node_modules/" and can be loaded by a portlet by adding these lines in liferay-portlet.xml:

	    <header-portal-javascript>/js/node_modules/es6-shim/es6-shim.min.js</header-portal-javascript>
	    <header-portal-javascript>/js/node_modules/zone.js/dist/zone.js</header-portal-javascript>
	    <header-portal-javascript>/js/node_modules/reflect-metadata/Reflect.js</header-portal-javascript>
	    <header-portal-javascript>/js/node_modules/systemjs/dist/system.src.js</header-portal-javascript> 
	    
	    
This hook is using:
* Maven
* NodeJS
* NPM
* frontend-maven-plugin by Eirik Sletteberg: https://github.com/eirslett/frontend-maven-plugin
* liferay-maven-plugin to easily deploy the hook (requires the liferay maven properties to be set as described here: https://dev.liferay.com/develop/tutorials/-/knowledge_base/6-2/using-liferay-maven-parent-plugin-projects)