Setup & Deployment:

1. Explain the angular application project structure?
A.  1) e2e
    2) node_modules
    3) src
    4) configuration files

2. What are the toplevel configuration files in an Angular application?
A.  1) .editorconfig
    2) .gitignore
    3) angular.json
    4) package.json
    5) package-lock.json
    6) tsconfig.json	
    7) tslint.json
    8) README.md

3. Default app project files?
A.  1) app - components, services, ...etc
    2) assets - images...etc
    3) environments - dev, qa, prod, ...etc
    4) index.html - Landing Page
    5) karma.conf.json - e2e
    6) main.ts - Entry js file for the angular application
    7) polyfills.ts - Provides polyfill scripts for browser support.
    8) styles.css - Global level styles
    9) test.ts - Entry js file for the test cases
    10) tsconfig.app.json  - Inherits from the workspace-wide tsconfig.json file.
    11) tsconfig.spec.json - Inherits from the workspace-wide tsconfig.json file.
    12) tslint.json - Inherits from the workspace-wide tslint.json file. 
    13) facicon.ico - fav icon

4. Default app project e2e files?
A.  1) src
    2) protractor.conf.js
    3) tsconfig.e2e.json

5. Angular offers two ways to compile your application, what are those?
A.  1) Just-in-Time (JIT), which compiles your app in the browser at runtime.
    2) Ahead-of-Time (AOT), which compiles your app at build time.

6. What is the default compilation when you run the ng build (build only) or ng serve (build and serve locally)?
A. JIT compilation

7. How can we tell angular to compile using AOT?
A. For AOT compilation, include the --aot option with the ng build or ng serve command
   ng build --aot
   ng server --aot

8. Which compilation the angular use ydefault when we run a ng build using option prod( ng build --prod)?
A. AOT Compilation.

9. Why compile with AOT?
A. Faster rendering:
With AOT, the browser downloads a pre-compiled version of the application. The browser loads executable code so it can render the application immediately, without waiting to compile the app first.

Fewer asynchronous requests:
The compiler inlines external HTML templates and CSS style sheets within the application JavaScript, eliminating separate ajax requests for those source files.
Smaller Angular framework download size
There's no need to download the Angular compiler if the app is already compiled. The compiler is roughly half of Angular itself, so omitting it dramatically reduces the application payload.
Detect template errors earlier
The AOT compiler detects and reports template binding errors during the build step before users can see them.

Better security:
AOT compiles HTML templates and components into JavaScript files long before they are served to the client. With no templates to read and no risky client-side HTML or JavaScript evaluation, there are fewer opportunities for injection attacks.

10. How can we configure application environments?
A.  1) environment.ts
    2) environment.stage.ts
    3) environment.prod.ts

11. How can we create a build specific to environment?
A. ng build --configuration = prod

12. Why budgets?
A. As applications grow in functionality, they also grow in size. The CLI allows you to set size thresholds in your configuration to ensure that parts of your application stay within size boundaries that you define.

13. How can we configure budgets?
A. Define your size boundaries in the CLI configuration file, angular.json, in a budgets section for each configured environment.

14. How can we proxying to a backend server?
A. You can use the proxying support in the webpack dev server to divert certain URLs to a backend server, by passing a file to the --proxy-config build option. For example, to divert all calls for http://localhost:4200/api to a server running on http://localhost:3000/api, take the following steps.
    1) Create a file proxy.conf.json in the projects src/ folder, next to package.json. 
    2)Add the following content to the new proxy file:
        {
            "/api": {
                "target": "http://localhost:3000",
                "secure": false
            }
        }
    3) In the CLI configuration file, angular.json, add the proxyConfig option to the serve target:
        ...
        "architect": {
        "serve": {
            "builder": "@angular-devkit/build-angular:dev-server",
            "options": {
            "browserTarget": "your-application-name:build",
            "proxyConfig": "src/proxy.conf.json"
            },
        ...
    4) To run the dev server with this proxy configuration, call ng serve.

15. How can we add multiple proxy entries?
A.  You can proxy multiple entries to the same target by defining the configuration in JavaScript.
    Set the proxy configuration file to proxy.conf.js (instead of proxy.conf.json), and specify configuration files as in the following example.
    const PROXY_CONFIG = [
        {
            context: [
                "/my",
                "/many",
                "/endpoints",
                "/i",
                "/need",
                "/to",
                "/proxy"
            ],
            target: "http://localhost:3000",
            secure: false
        }
    ]

    module.exports = PROXY_CONFIG;

16. How can we deploy an Angular application to a production?
A. https://angular.io/guide/deployment

17. 



    
    