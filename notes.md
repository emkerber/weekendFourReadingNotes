Notes from ng-book: The Complete Book on AngularJS
==================================================

Introduction
------------

* the author of the Forward struggled with Angular at first, but seeing the big picture helped him understand the language
* AngularJS is a front-end framework released by Google


The Basics of AngularJS
-----------------------

### IP addresses and DNS servers

* when on a public WiFi network, your computer shares the same IP address as the other computers on the network
* your individual computer can be reached with your internal IP address
* IP stands for Internet Protocol
* IP address: numerical identifier assigned to each device participating in a network
* two main types of IP addresses: ipv4 and ipv6
* ipv4 are most common
* ipv6 are longer/contain more characters
* when you make a request to your browser to go to a site, the browser passes the request to a DNS server
* the DNS server responds with the IP address of the computer (the website) you're trying to reach, or it passes the request to other DNS servers until the IP address is found and served to your computer
* in the terminal: to see the DNS server response, type "dig <URL>"
* when the DNS server responds with the site's/computer's IP address, it also sends a message to that computer requesting the web page's HTML
* your browser receives the HTML and renders it, lays out the content of the page, and styles the content

### Angular is awesome because...

* jQuery: must know where an element is being appended within the DOM, and use HTML logic inside JavaScript code
* Angular: augments HTML to give it native MVC (Model-View-Controller) capabilities
* the AngularJS source code is available on GitHub and anyone can contribute to it if they follow correct procedures (such as mailing list participation)


Data Binding and Your First AngularJS Web Application
-----------------------------------------------------

* see files created during this chapter: index.html, app.js

### Other frameworks

* in classic web frameworks (example: Rails) the controller combines data from models with templates, producing a single-way view that reflects only the data exposed by the model at the time the view was rendered
* a couple JavaScript frameworks automatically data bind the view and the model
* AngularJS DOES NOT merge data into a template and replace elements on the DOM
* AngularJS DOES create live templates as a view, and individual components of the views are dynamically put together live

### Using Angular to bind data

* we nest an Angular app inside of a web app by including angular.js as a script in our HTML, and by setting the ng-app attribute on an element in the DOM
* the only components affected by Angular are the DOM elements that are declared inside the element with the ng-app attribute
* any time the model is changed on the client side, the view changes to reflect this

### The MVC

* view and controller logic do not have to be separated in the MVC (Model View Controller), which makes testing much easier
* MVC is a software architecture pattern that separates representation from user interaction
* MVC: "model" - application data and functions that interact with it; view - presents data to the user; controller - mediates between the two
* MVC provides a separated presentation that makes a clear division between the web app's objects, so the view just needs to know how to display an object and not how to save it; the model just needs to contain the data and methods to manipulate the view, but doesn't need to interact with it; the controller contains the logic to bind the two
* Angular remembers the value the model contains at any given time

### Dirty values

* a value is "dirty" when it has changed since the last time Angular's event loop ran
* when Angular thinks the value might be changing, it runs an event loop to check if the value is dirty; this event loop is called the $digest() loop
* dirty checking is a relatively efficient approach to checking for changes on a model
* alternative to dirty checking is attaching change listener functions to the change event (example: KnockoutJS); this is much more complex and less efficient
* dirty checking works in every browser and is predictable

### Bling

* in Angular, the $ prepends objects that are internal and built-in library functions; it's completely unrelated to jQuery's $

### More on data binding

* example of data binding: give an input ng-model "name" and then put {{name}} in an h tag below it; in other words, the "name" property was binded to the input field using the ng-model directive on the containing model object
* the "model object" is the $scope object, which is a JavaScript object whose properties are all available to the view and that the controller can interact with
* "bi-directional" means that if the view changes the value, the model observes the change (using dirty checking), and if the model changes the value the view updates to reflect this

### Pieces of Angular code

* the app is named by assigning a value to the ng-app attribute; here we tell Angular which module we want to use
* the function "angular.module()" returns a module
* the function ".controller()" defines a new controller and takes two arguments: a string that defines the name of the controller, and a definition function that defines how the controller will work
* "dependency injection" - a way to require libraries we want to use

### Data binding best practices

* bind references in the views by an object's attribute rather than the object itself
* in the example, use clock.now in HTML, and in JS initialize $scope.clock as an empty object, then $scope.clock.now = new Date()
