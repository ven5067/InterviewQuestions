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

Angular:

17. What is Angular?
A. Angular is a Javascript framework which allows us to create reactive single page applications(SPAs).

18. What is the difference AngularJS, Angular 1, Angular 2, ..., Angular 6, Angular7?
A. Angular 1 was intially released in 2010. Angular 2 is complete re-write of Angular 1 and it was released intially in 2016. It has nothing in common with Angular 1 except the core team that developed it. If we know the Angular 1 unfortunately that knowledge will not help us much and the other other hand we also don't need to know the Angular 1.

On the other hand, The Angular 3, ..., Angular 6, Angular 7 are just Angular. And, the Angular 1 is now called as AngularJS. These two are seperate frameworks.

Angular2+ are really just incremental improvements (Bug fixes, Minor Improvements..etc), No Complete Re-Writes! The syntax is completely same for all the version of Angular.

19. How can we create new Angular application using AngularCLI?
A. ng new application-name

20. What is Typescript?
A. Typescript is a superset of Javascript. It offers more features than the Vanilla JS (e.g. Types, Classes, Interfaces). It gives the strong Typing. So, we can define a certain variable is string/number/etc, we don't do it in vanillaJS there we have a dynamic typing.

However, the Typescript doesn't run in the browser, it's compiled to Javascript in the end. And, this compilation is handled by the CLI. One of the reason why we do need the CLI and why we need project management tools like CLI.

21. How the Angular application gets loaded and started?
A. main.ts file is the entry point to the Angualr application. There we define which Module has to bootstrap first. And, in the module we define which component has to load.

E.g. main.ts -> AppModule -> AppComponent

22. What are Components?
A. The Components are the key features in Angular application. Wwe built our whole application by composing it from the couple components.

23. How can we create a Component using CLI?
A. ng generate component component-name (or)ng g c component-name

24. What are Decorators?
A. The Decorators are the Typescipt feature which allows us to enhance our classes. The Decorators are always attached with the @ sign before it's name.

25. On which package the angular core Decorators are available?
A. @angular/core

26. What @NgModule decorator does?
A. This is where we configure all the components which are belongs to the particular module.

@NgModule({
    declarations: [
        Component 1,
        Component 2,
    ],
    imports: [
        BrowserModule,
        FormsModule,
        HttpModule
    ],
    providers: [
        Service1,
        Service2
    ],
    bootstrap: [AppComponent]
})

27. Difference between template and templareUrl?
A. The template property allows us to write the inline HTML code. Where as, the templateUrl property points to the view file (HTML file).

28. How many types of selectors does Angular supports?
A.  1) element 'element-name'
    2) attribute [element-name]
    3) class .element-name

29. Difference between the styles and styleUrls property?
A. The styles property allows us to define the inline css. Where as, the stylesUrls property allows us to point to the different css files.

30. What is databinding?
A. The communication between the HTML(Template) file and the Typescript code(Bussiness Logic).

31. Difference types of communication in Angular?
A.  1) String interpolation
    2) Property binding

32. What is String Interpolation?
A. If we want to output the data from the typescript code to the HTML code we use string interpolation. E.g. {{ data }}

33. What is Property binding?
A. Property data binding is one-way databinding. Property databinding is performed with the component property. Component property binding is used for communication between the parenent and the child components. E.g. [property]="data"

34. What is Event binding?
A. If we may want to trigger some Typescript code from the HTML we use this EventBinding. E.g. Lets suppose we want to trigger something in the Typescript code when we click on a button on the HTML page. E.g. (event) = "expression"

35. What is two-way data binding?
A. Combination of both property binding and event binding is called two-way databinding. 
E.g. [(ngModel)] = "data"

36. Difference between string interpolation vs property binding?
A. Whatever the thing we pass between {{}} these brackets the string interpolation converts that to a string. Property binding does the convert the value to string.











    
    