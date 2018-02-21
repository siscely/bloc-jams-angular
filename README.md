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


