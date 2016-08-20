Modularized Ionic ES6 tabs starter project with Keycloak
=====================

Based on *kitbrennan90/ionic-babel-browserify-es6* but heavily modified. Uses ES6 with babelify as  transpiler. Controllers and rest services are seperated into their own files with the help of ES6 export/import syntax. One controller/service per file. State definitions are also separated from app.js. Keycloak-js initializes before everything else and logs in the user by default. Auth interceptor is registered on $httpProvider, which injects an Authorization header with OAuth bearer token into every REST call. A real REST mock service is used instead of plain JavaScript mock.

# Setup instructions
1. Install Keycloak and register with an identity provider of your choice. I recommend exposing your Keycloak server on a public domain over HTTPS to avoid problems with identity provider integration and unexpected self-signed certificate troubles. https://keycloak.gitbooks.io/securing-client-applications-guide/content/v/2.1/topics/oidc/javascript-adapter.html
2. Create a public OAuth client. Set Valid redirect URI to http://* and Web Origins to * in order to avoid CORS and redirect problems during development.
3. Place client's keycloak.json into www folder. 
4. Install fake REST server: `npm install -g json-server` and run it with `json-server --host 0.0.0.0 --watch fakerest/db.json`
5. `gulp js` and `ionic serve`

The resulting app is actually something you can start working with in a real world scenario, providing:
-User login
-Actual REST calls with correct Authorization header
-modularized Angular files
-ES6 support (aww yea!)
