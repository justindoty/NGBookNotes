###How Is It different? 
 		AngularJS, on the other hand, augments HTML to give it native Mode View-Controller (MVC) capabilities. This choice, as it turns out, makes building impressive and expressive client-side applications quick and enjoyable. It enables you, the developer, to encapsulate a portion of your entire page as one application, rather than forcing the entire page to be an AngularJS application. This distinction is particularly beneficial if your workflow already includes another framework or if you want to make a portion of the page dynamic while the rest operates as a static page or is controlled by another JavaScript framework.

###Introducing Data Binding in AngularJS

AngularJS takes a different approach. Instead of merging data into a template and replacing a DOM element, AngularJS creates live templates as a view. Individual components of the views are dynamically interpolated live.

Automatic data binding gives us the ability to consider the view to be a projection of the model state. Any time the model is changed in the client-side model, the view reflects these changes without writing any custom code. It just works.

When Angular thinks that a value might change, it will run its own event loop to check if the value is dirty.

A value is considered dirty if it has changed since the last time the event loop ran. This is how Angular is able to track and respond to changes in the app

###Simple Data Binding
The model object that we are referring to is the $scope object.

The $scope object is simply a JavaScript object whose properties are all available to the view and with which the controller can interact
So notice something here: in our javascript code in MyController we assigned a value to $scope.clock. But in our view we specified clock to read the value (not $scope.clock). This is because the “scope” is implied in the view.


###Best Data Binding Practices
Due to the nature of JavaScript itself and how it passes by value vs. reference, it’s considered a best-practice in Angular to bind references in the views by an attribute on an object, rather than the raw object itself.


###Modules
In JavaScript, placing functional code in the global namespace is rarely a good idea. It can cause collisions that are tough to debug and cost us precious development time.

In Angular, a module is the main way to define an AngularJS app. The module of an app is where we’ll contain all of our application code. An app can contain several modules, each one containing code that pertains to specific functionality.

###Using modules gives us a lot of advantages, such as:
	•	Keeping our global namespace clean 

	•	Making tests easier to write and keeping them clean so as to more easily target isolated  functionality 

	•	Making it easy to share code between applications 
	•	Allowing our app to load different parts of the code in any order 
	.	When writing large applications, we’ll create several different modules to contain our logic. Creating a module for each piece of functionality gives us the advantage of isolation in which to write and test large features.
   
###Properties
Angular modules have properties that we can use to inspect the module.

####name (string)
The name property on the modules gives us the name of the module as a string. requires (array of strings)

####The requires property contains a list of modules (as strings) that the injector loads before the module itself is loaded.

###Scopes
Scopes are the source of truth for the application state.

Because of this live binding, we can rely on the $scope to update immediately when the view modifies it, and we can rely on the view to update when the $scope changes.

$scopes in AngularJS are arranged in a hierarchical structure that mimics the DOM and thus are nestable: We can reference properties on parent $scopes.

This $scope object is a plain old JavaScript object. We can add and change properties on the
$scope object however we see fit.

This $scope object is the data model in Angular. Unlike traditional data models, which are the gatekeepers of data and are responsible for handling and manipulating the data, the $scope object is simply a connection between the view and the HTML. It’s the glue between the view and the controller.
Creation

When a controller or directive is created, Angular creates a new scope for us and passes this on to the new scope when it runs the controller constructor function at runtime. We don’t need to worry about how it is created, we can just depend upon it being created for us.

###Linking
When angular starts running, all of the $scope objects are attached or linked to the view.

All functions that create $scope objects attach themselves to the view as well. These scopes will register functions that run when things change in the context of the angular app.

These functions are called $watch functions, which is how Angular knows when to start the event loop.

###Updating
When the event loop is running, which usually executes on the top-most $scope object (called the $rootScope), every child scope performs it’s own dirty checking. Every watch function is checked for changes. If any changes are detected, then the $scope object will fire the callback.

###Destruction
When a $scope object is no longer needed in the view, the scope itself will be cleaned up and destroyed.

Although we’ll never need to clean up the scope directly as angular handles this for us, it’s useful to know that whomever created the scope will clean up the scope for us using a method on the $scope called: $destroy().

###Directives and Scopes
Directives, which are used all throughout our Angular apps, generally do not create their own $scopes, but there are cases when they do. For instance, the ng-controller and ng-repeat directives create their own child scopes and attach them to the DOM element.

###Controllers
When we create a new controller on a page, Angular passes it a new $scope.

 This new $scope is where we can set up the initial state of the scope on our controller. Since Angular takes care of handling the controller for us, we only need to write the constructor function.

To bind buttons or links (or any DOM element, really), we’ll use another built-in directive, ng- click. The ng-click directive binds the mouseup browser click event to the method handler, which calls the method specified on the DOM element (i.e., when the browser fires a click event on the DOM element, the method is called).
