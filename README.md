## Bloc Frontend Project Starter

A starter application for student projects in Bloc's [Frontend Web Development Course](https://www.bloc.io/frontend-development-bootcamp).

## Pull Down the Code

Start by cloning the repository:

```
$ git clone https://github.com/Bloc/bloc-frontend-project-starter.git <your-frontend-project-name>
```

## Reset Git

This will be your personal project. So all of the past commit history that we used to build this starter app aren't needed. Also you will want to be able to push/pull code from your personal remote (Github) repository and NOT Bloc's remote (Github) repository.

Remove the existing local Git repository:

```
$ rm -r -f .git
```

Initialize a new Git repository, add all of these existing files, and commit them:

```
$ git init
$ git add .
$ git commit -m "initial commit"
```

Go to Github and create a new repository. Add that new repository as the proper remote. Then push your initial commit.

```
$ git remote add origin <URL TO NEW GITHUB REPO>
$ git push origin master
```

## Configuration

The project uses Node to run a JS server in development. This will be important when we want to use urls /album or /collection instead of the basic album.html or collection.html. It may  help to review [our resource on NPM and `package.json` files](https://www.bloc.io/resources/npm-and-package-json).

Install the project dependencies by running:

```
$ npm install
```

## Run the Application

Run the application server:

```
$ npm start
```

The server will start up. To stop the server, press `cntrl + c`.


## Use in Brackets Live Preview

To use the application with the Live Preview functionality of the Brackets text editor, go to __File > Project Settings__ and add `http://localhost:3000` to the Base URL field.

![Screenshot of project settings URL in Brackets](https://bloc-global-assets.s3.amazonaws.com/images-frontend/screenshots/bloc-frontend-project-starter/live_preview_project_settings.png)

The text in the application will not update on every keystroke, but changes will automatically push when you save the file.

## Directory Structure

```
├── LICENSE
├── README.md
├── app
│   ├── assets
│   │   └── images
│   │       └── bloc-logo-white.png
│   ├── pages
│   │   └── index.html
│   ├── scripts
│   │   └── app.js
│   ├── styles
│   │   └── style.css
│   └── templates
│       └── home.html
├── package.json
└── server.js
```


### Assets/Images

Add images to the `app/assets/images` directory. To reference images in HTML, use the path `/assets/images/<image file name>.jpg`. For example, to include the image called `bloc-white-logo.png`, the path for the `src` attribute in the HTML would be:

```html
<img src="/assets/images/bloc-white-logo.png">
```

__Note:__ A sample image has been added to `app/images`. To remove the image from the application, run the following command from the root of repo:

```bash
$ rm -f app/assets/images/bloc-white-logo.png
```

To reference any other assets, like the music in Bloc Jams, use the path `assets/<asset-type>/<asset-file-name>`.

### Difference between Pages and Templates

The `templates` directory should hold any HTML files used as templates in Angular states configured by UI Router. All other HTML files belong in the `pages` directory.

## Bloc-Jams-Angular
## Description
In this project you'll rework Bloc Jams to use the Angular JavaScript framework.

### Install NodeJS

Setup the Application
On GitHub, fork the Bloc Jams AngularJS Starter. Forking a project makes a copy and adds it to your own GitHub account. This is an important step, because your work will need be on your GitHub account and not Bloc's.

Rename your forked repository to bloc-jams-angularjs in GitHub (available under the Settings tab of your repository).

Open your terminal, cd into your ~/bloc directory, and clone your repository.
```
$ cd ~/bloc
$ git clone https://github.com/{username}/bloc-jams-angularjs.git
```
Make sure to replace {username} with your GitHub username.

Change into the directory: $ cd bloc-jams-angularjs.
Run $ npm install to download/install the needed dependencies
Start the node server: npm start.
Open a web browser, go to http://localhost:3000, and verify that you see the Bloc Jams landing page.
You can press ctrl + c at any time to stop the server.

You'll want to keep the server running whenever you're working on your project.

Include Angular
Follow the steps below to initialize an Angular application.

1. Reference the Angular Script File
Include Angular the same way we include a library like jQuery, by adding a script source to the HTML document. Add a link to the Angular source in index.html and make sure that the link is above your other script tags:

app/index.html
```
 ...
     <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
     <script src="scripts/app.js"></script>
 </body>
 ...
 ```
### Declare an Angular Module
The root Angular module will act as a container for different parts of our application. In app.js, define a module with angular.module:

app/scripts/app.js
angular.module('blocJams', []);
The first argument passed, blocJams, is the prescribed name of the module. The empty array, passed as the second argument, injects dependencies into an application. For now, there are no dependencies to inject, but we'll cover dependency injection in the next checkpoint.

### Bootstrap the Application
To link the blocJams module to the application, Angular needs to know the root element of the application, which is typically the <html> or <body> element. In  index.html, link the root module to the <html> tag:

app/index.html
```
 ...
 <!DOCTYPE html>
 <html>
 <html ng-app="blocJams">
 <head lang="en">
 ...
 ```
At this point, we've wired Angular to the application. The next steps are to configure the module and create a controller, which we'll cover in the following checkpoints.

Check your work
To ensure that Angular is up and running, add a simple Javascript expression inside double curly brackets {{ }}to your index.html file.

app/index.html
```
<!DOCTYPE html>
<html>
  ...
  <body>
    {{ 2 + 2 }}
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
  </body>
</html>
```
Then switch to your terminal. Start the server with: $ npm start. Open a new web browser window and navigate to: http://localhost:3000. You should see the expression evaluated on the webpage. So assuming you did 2 + 2 inside double curly brackets, you would see a white webpage with just the number 4 on it.

Once you have verified that Angular is up and running on your app, you can remove the {{ 2 + 2 }} from index.html

Git
Commit your work in Git. 

## Create Templates for Bloc Jams
index.html will act as the global file for Bloc Jams. Add <ui-view></ui-view> to the global file:
```
~/bloc/bloc-jams-angular/app/index.html
 ...
 <body>
     <nav class="navbar">
         ...
     </nav>

     <ui-view></ui-view>

     <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
     <script src="/scripts/app.js"></script>
 </body>
 </html>
 ```
The Landing, Collection, and Album templates will consist of content unique to each template.

Create a landing.html file in the app/templates directory:

~/bloc/bloc-jams-angular/app/templates/landing.html
```
 <section class="hero-content">
     <h1 class="hero-title">Turn the music up!</h1>
 </section>
 
 <section class="selling-points container clearfix">
     <div class="point column third">
         <span class="ion-music-note"></span>
         <h5 class="point-title">Choose your music</h5>
         <p class="point-description">The world is full of music; why should you have to listen to music that someone else chose?</p>
     </div>
     <div class="point column third">
         <span class="ion-radio-waves"></span>
         <h5 class="point-title">Unlimited, streaming, ad-free</h5>
         <p class="point-description">No arbitrary limits. No distractions.</p>
     </div>
     <div class="point column third">
         <span class="ion-iphone"></span>
         <h5 class="point-title">Mobile enabled</h5>
         <p class="point-description">Listen to your music on the go. This streaming service is available on all mobile platforms.</p>
     </div>
 </section>
 ```
When we view the landing page, we see that the selling points don't display. This is because bloc-jams/scripts/landing.js animated those elements to display with jQuery. In this project, we won't refactor the animation. In  bloc-jams-angular/app/styles/landing.css, change the opacity of .point from 0 to  1 and remove the transition properties.

To display the Collection view with Angular, we'll need to move the template from  collection.js back to HTML. Create a collection.html file in the app/templates directory:

~/bloc/bloc-jams-angular/app/templates/collection.html
```
 <section class="album-covers container clearfix">
     <div class="collection-album-container column fourth">
         <img src="/assets/images/album_covers/01.png"/>
         <div class="collection-album-info caption">
             <p>
                 <a class="album-name" href="album.html">The Colors</a>
                 <br/>
                 <a href="album.html">Pablo Picasso</a>
                 <br/>
                 X songs
                 <br/>
             </p>
         </div>
     </div>
 </section>
 ```
For the Album view, create an album.html file in the app/templates directory. Similar to the Collection view, move the song row template from album.js and place it back in the HTML:

~/bloc/bloc-jams-angular/app/templates/album.html
```
 <main class="album-view container narrow">
     <section class="clearfix">
         <div class="column half">
             <img src="/assets/images/album_covers/01.png" class="album-cover-art">
         </div>
         <div class="album-view-details column half">
             <h2 class="album-view-title">The Colors</h2>
             <h3 class="album-view-artist">Pablo Picasso</h3>
             <h5 class="album-view-release-info">1909 Spanish Records</h5>
         </div>
     </section>
     <table class="album-view-song-list">
         <tr class="album-view-song-item">
             <td class="song-item-number">1</td>
             <td class="song-item-title">Blue</td>
             <td class="song-item-duration">3:31</td>
         </tr>
     </table>
 </main>
 ```
### Routing
To display these templates in the view, Angular uses routing, which is organized around URL routes. Angular has a built-in router, but many developers don't use it.

Instead, developers use UI-Router because it is more flexible and features behaviors not found in the Angular tools. With UI-Router, an application can be in different states that determine what to display when a user navigates to a specific route.

UI-Router will take care of replacing the contents of <ui-view></ui-view> with a template when a user navigates to the proper route. Each template can be unique, while the shared code is kept in the global file. Since UI-Router uses JavaScript to switch the views, the browser won't load a new HTML document when a user navigates to a new route.

### Add an External Module to an Angular Application
The Angular development community has useful external modules that makes adding more robust functionality to Angular applications easy. To add these external modules, we must do at least two things:

1. Include the script source in the application, below the Angular source.
1. Inject the module into the application's declaration.
1. Include the UI-Router Source
UI-Router is a separate module from the Angular source script. To include it in an application, add its source script after the Angular source. With a global file that contains all the subviews, we only need to add the source once:

~/bloc/bloc-jams-angular/app/index.html
```
 ...
 <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
 <script src="https://cdnjs.cloudflare.com/ajax/libs/angular-ui-router/0.4.2/angular-ui-router.min.js"></script>
 <script src="/scripts/app.js"></script>
 ...
 ```
UI-Router is an extension of Angular so it must come after the Angular source or the application will throw a Reference Error.

Inject the UI-Router Module

~/bloc/bloc-jams-angular/app/scripts/app.js
```
angular.module('blocJams', []);
The second argument, the empty array, is the list of external modules that blocJams depends on, known as dependency injection. After we add an external module's script source, we can inject the module into the application by adding it to the array:

~/bloc/bloc-jams-angular/app/scripts/app.js
```
 angular.module('blocJams', []);
 angular.module('blocJams', ['ui.router']);
 ```
The blocJams module can now make use of the UI-Router module. We can add additional modules as strings in the array.

Configure the Module with Providers
With UI-Router, we need to set up state configuration using an Angular provider. Providers are services used by Angular modules to either configure or define default behavior for a certain Angular module. For Bloc Jams, we'll use two providers:

$stateProvider: to configure the state behavior
$locationProvider: to configure how the application handles URLs in the browser
To make sure the providers are accessible throughout the application, inject them using the config block on the application's root module. Write a config function to pass into the config() function:

~/bloc/bloc-jams-angular/app/scripts/app.js
```
 (function() {
     function config($stateProvider, $locationProvider) {
     }
 
 angular.module('blocJams', ['ui.router']);
     angular
         .module('blocJams', ['ui.router'])
         .config(config);
 })();
 ```
This style of module declaration is based on the Opinionated Angular Styleguide.

Configure Paths with $locationProvider
$locationProvider, which is part of Angular's core, configures an application's paths. By default, Angular prefixes routes with #!, known as Hashbang mode. This is a convention for showing that a page load is triggered by JavaScript.

For example, if we navigate to a state with the path /album, the full URL will read  localhost:3000/#!/album instead of localhost:3000/album. It doesn't look nice, but we can disable it. Add the following code to the config function:

~/bloc/bloc-jams-angular/app/scripts/app.js
```
 function config($stateProvider, $locationProvider) {
     $locationProvider
         .html5Mode({
             enabled: true,
             requireBase: false
         });
 }
 ...
 ```
By setting the html5Mode method's enabled property to true, the hashbang URLs are disabled; that is, users will see clean URLs without the hashbang. Setting the  requireBase property to false is unrelated to the hashbang issue, but is one way to avoid a common $location error.

Configure States with $stateProvider
$stateProvider, a component of UI-Router, will determine a number of properties for a state. For Bloc Jams, we'll need to know how to configure at least four aspects of a state: its name, URL route, controller, and template.

$stateProvider calls .state(), which takes two arguments: stateName and  stateConfig. For example:

$stateProvider.state(stateName, stateConfig)
stateName is a unique string that identifies a state and stateConfig is an object that defines specific properties of the state. For Bloc Jams, create a state named landing and add an accompanying URL and template to the stateConfig object:

~/bloc/bloc-jams-angular/app/scripts/app.js
```
 function config($stateProvider, $locationProvider) {
     $locationProvider
         .html5Mode({
             enabled: true,
             requireBase: false
         });

     $stateProvider
         .state('landing', {
             url: '/',
             templateUrl: '/templates/landing.html'
         });
 }
 ...
 ```
With this state configuration, when we navigate to localhost:3000 or localhost:3000/, the ui-view directive in the global file (index.html) will load the template associated with the landing state.

Because $stateProvider.state() returns $stateProvider, we are able to call state() again without having to reference the $stateProvider variable. With no arguments passed to the state() call, this would look like $stateProvider.state().state(). This is called method chaining. It's common to chain state() calls instead of calling them individually on $stateProvider. Add another state, named album:

~/bloc/bloc-jams-angular/app/scripts/app.js
```
 ...
     $stateProvider
         .state('landing', {
             url: '/',
             templateUrl: '/templates/landing.html'
         });
         })
         .state('album', {
             url: '/album',
             templateUrl: '/templates/album.html'
         });
 ...
 ```
With this configuration the album state, when we navigate to localhost:3000/album, the ui-view directive in the global file will load the album template.

### Trigger a State
Instead of using anchor tags (<a>) with an href (short for "hyperlink reference"), UI-Router triggers states by attaching a ui-sref directive (short for "user interface state reference") in place of the href.

For example, instead of <a href="album.html">, a link refers to a state name like so:  <a ui-sref="album">, where album is the name of the state to trigger.

To trigger a state change (display a different view) when using UI-Router, use ui-sref instead of href. For external page links or an internal anchor, continue to use href.

We've established the basic views for Bloc Jams. The song list in the Album view, however, is missing hover behavior. We're also missing a crucial aspect of our application: the player bar.

Consider this jQuery code:
```
var $previousButton = $('.main-controls .previous');
var $nextButton = $('.main-controls .next');

$(document).ready(function() {
    setCurrentAlbum(albumPicasso);
    $previousButton.click(previousSong);
    $nextButton.click(nextSong);
});
```
This code designates what should happen when a user clicks the $previousButton and $nextButton objects. The DOM elements are identified in the JavaScript. Angular, on the other hand, declares this code in the HTML:
```
<div class="main-controls">
    <a class="previous" ng-click="previousSong()">
        <span class="ion-skip-backward"></span>
    </a>
    <a class="next" ng-click="nextSong()">
        <span class="ion-skip-forward"></span>
    </a>
</div>
```
The functions previousSong and nextSong exist in the JavaScript, but Angular's  ng-click syntax more clearly shows the elements that trigger some action when a user interacts with the application.

### ngClick and ngShow Directives
The section above shows a use case for the ngClick directive. It is Angular's declarative equivalent of jQuery's .click() method.

Similarly, the ngShow directive is Angular's declarative equivalent of jQuery's  .show() method. (Angular has an inverse of ngShow named ngHide.) From the documentation:

The ngShow directive shows or hides the given HTML element based on the expression provided to the ngShow attribute. The element is shown or hidden by removing or adding the .ng-hide CSS class onto the element. The .ng-hide CSS class is predefined in AngularJS and sets the display style to none (using an !important flag).

Here is an ngShow example from the Angular documentation:

```
<!-- when $scope.myValue is truthy (element is visible) -->
<div ng-show="myValue"></div>

<!-- when $scope.myValue is falsy (element is hidden) -->
<div ng-show="myValue" class="ng-hide"></div>
Refer to the MDN documentation for a refresher on truthy and falsy.

Update the Album View Template
Instead of using jQuery's imperative view manipulation to create onHover and  offHover functions (as shown here), we'll declare this functionality in the view using Angular's ngShow directive.

Before we can add this declarative code, however, we need to decide what to show and when to show it:

What to Show	When to Show It
1. Song number	When the song is not playing and the mouse is off hover
1. Play button	When the song is not playing and the mouse is on hover
1. Pause button	When the song is playing
When a user first visits the Album view, each song row should display the song's number. When a user hovers over a song row, the song number should change to a play button if the song is not already playing. When a user clicks the play button, it should change to a pause button.

Using ngShow, we'll write some "wishful coding" with variables that we haven't yet declared. Update album.html with the following changes:

~/bloc/bloc-jams-angular/app/templates/album.html
```
 ...
 <td class="song-item-number">1</td>
 <td class="song-item-number">
     <span ng-show="!playing && !hovered">1</span>
     <a class="album-song-button" ng-show="!playing && hovered"><span class="ion-play"></span></a>
     <a class="album-song-button" ng-show="playing"><span class="ion-pause"></span></a>
 </td>
 ...
 ```
We can incorporate the hovered variable using the straightforward ngMouseover and  ngMouseleave directives. Add these directives to the table row:

~/bloc/bloc-jams-angular/app/templates/album.html
```
 ...
 <tr class="album-view-song-item">
 <tr class="album-view-song-item" ng-mouseover="hovered = true" ng-mouseleave="hovered = false">
 ...
 ```
Both directives evaluate an expression. In this case, we assign the hovered variable a value of true or false.

At this stage, we should be able to see the play button appear on mouseover. We'll be able to display the pause button once we start to work on playing music in a later checkpoint.

### Create a Template for the Player Bar
We'll use Angular to create a player bar template and include it in the Album view. For the time being, the player bar controls will not work – we'll implement the player bar functionality using Angular in a later checkpoint.

### Create a file named player_bar.html in the app/templates directory. Copy the player bar markup from bloc-jams/album.html and paste it into the new file:

~/bloc/bloc-jams-angular/app/templates/player_bar.html
```
 <section class="player-bar">
     <div class="container">
         <div class="control-group main-controls">
             <a class="previous">
                 <span class="ion-skip-backward"></span>
             </a>
             <a class="play-pause">
                 <span class="ion-play"></span>
             </a>
             <a class="next">
                 <span class="ion-skip-forward"></span>
             </a>
         </div>
         <div class="control-group currently-playing">
             <h2 class="song-name"></h2>
             <h2 class="artist-song-mobile"></h2>
             <h3 class="artist-name"></h3>
             <div class="seek-control">
                 <div class="seek-bar">
                     <div class="fill"></div>
                     <div class="thumb"></div>
                 </div>
                 <div class="current-time"></div>
                 <div class="total-time"></div>
             </div>
         </div>
         <div class="control-group volume">
             <span class="icon ion-volume-high"></span>
             <div class="seek-bar">
                 <div class="fill"></div>
                 <div class="thumb"></div>
             </div>
         </div>
     </div>
 </section>
 ```
Include the Template in the Album View
Angular has a directive for including external templates called ngInclude. Like an  <img> tag, ngInclude has an src attribute that defines the path of the asset – in this case, a template.

Use the ngInclude like an element tag at the bottom of the Album view template:

~/bloc/bloc-jams-angular/app/templates/album.html
```
 ...
 <main class="album-view container narrow">
     ...
 </main>

 <ng-include src="'/templates/player_bar.html'"></ng-include>
 ...
 ```
Because the player bar now has its own template, it could be added to any view using  ngInclude. Add the player bar template to the Landing and Collection views to try it out. After we've gotten the player bar to display on multiple views, be sure to remove it from the Landing view – we don't actually want a player bar to display there.
