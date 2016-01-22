# Hack-the-Series-Challenge-1
Basic guide for beginners on how to create a webpage using the Ruby on Rails framework.




<h1>How to Create a Website using Rails</h1>
This guide has been created for those interested in building a Rails application from scratch. 

<h2>Things to Know before we start:</h2>
It is best to have some knowledge of Ruby, a popular programming language known best for its web applications. It is an object-oriented scripting language that can be used with the Rails framework. 
There are a variety of tutorials available to help you understand the basics of Ruby:
https://www.codecademy.com/learn/ruby
https://www.ruby-lang.org/en/documentation/quickstart/

Rails is a web application development framework that has been written in Ruby. It follows the model-view-controller (MVC) framework and gives default structures for a database, a web service, and pages. Rails established conventions for easier management.

A model manages the basic behaviors and data of an application. You can request information from it or change the information. The model in the Ruby on Rails framework maps to a table in a database, and a Ruby file.

A view is the user interface section. It takes the data and puts it in the appropriate format. The view does not collect information.
The view is in the erb file, which means it’s essentially a HTML file embedded with Ruby.

A controller takes the user input and accordingly calls to the models or views to respond appropriately.
The controller takes requests from the web server to the application, by determining which files to render.

<h2>Prerequisites</h2>
1.	Download Ruby for your operating system (at least version 1.9.3):
https://www.ruby-lang.org/en/documentation/installation/
2.	A packaging system is a group of tools that makes the instillation, uninstallation, and upgrading process easier for an operating system. Get the RubyGems packaging system:
https://rubygems.org/pages/download
To learn more about RubyGems: 
http://guides.rubygems.org/
3.	SQLite is a relational database engine. A relational database is a collection of data organizes in tables. 

Alternatively, you can follow the instructions through this website: ```http://installrails.com/```.


<h2>Starting the Project</h2>
Make sure that you have a current version of Ruby installed (at least 1.9.3).
```
$ ruby – v
```
This should return something like  ```ruby 2.3.0p0```

Some operating systems come with SQLite3. Windows users and others can download from the following link. Scroll to the precompiled binaries for your OS, and download the zip file:
https://www.sqlite.org/download.html


The following command should show the version installed.
```
$ sqlite3 --version
```

Install Rails using the RubyGems command (this could take a while).
```
$ gem install rails
```

Make sure that everything has installed correctly. This should return Rails and a version number.
```
$ rails --version
```

<h2>Creating the Application</h2>
Open your terminal and navigate to a directory where you want to store your project (ex. in Documents/Projects).

Create the Rails application called Site in a site directory.
```
$ rails new site
```

Use cd to move to the site application.
```
$ cd site
```

In this folder, you can see many default files that make up the basis of a Rails application. For this tutorial we will focus on the app/ folder that contains all controllers, models, views, and other tools.

There is a basic, default, functional Rails application already set in place. We will now start a web server, WEBrick (default from Ruby), to see it:
```
$ bin/rails server
```

Now, open your browser and go to ```http://localhost:3000/``` to see the project. You will initially see the Rails default information page.

Use Ctrl+C to stop the web server running at any time.

<h2>Say "Hello, World!"</h2>
Let’s start by getting Rails to say “Hello, World!”. To do this, we need to create a controller and a view. Remember, a controller will take requests from the application. 

A process called routing determines which controller will receive which requests. The router will look at the HTTP verb and the URL that is being requested to match it with the appropriate router. If the router can’t find an appropriate route, it will throw an error.

The routes are all found in the ```config/routes.rb``` folder. The routes will tell Rails how it can direct any incoming ```get```, ```delete```, ```post```, and ```put``` requests. 



Create a new controller by running the “controller” generator and naming it “welcome” with an action called index.
```
$ rails generate controller welcome index
```

You will see many files created. The controller will be app/controllers/welcome_controller.rb and the view will be app/views/welcome/index.html.erb
It will also create a view and a html page where you can input the necessary code.
 
Use a text editor and open app/views/welcome/index.html.erb
Replace the code inside with:
```
<h1>Hello, World!</h1> 
```

Now, we have to tell Rails to navigate to our “Hello, World!” page because the default page is currently seen.

Use a text editor to open config/routes.rb
Uncomment the line with 
```
root ‘welcome#index’
```
This line tells Rails to map requests to the welcome controller’s index action. The line 
```
get ‘welcome/index’ 
```
tells Rails to map requests to ```http://localhost:3000/welcome/index``` so that will open

Type in 
```
$ rails server
```
Launch the web server again if you had stopped it before. You should see the page say hello world. 

<h2>Making a another page</h2>
You'll probably want multiple pages on your website, so here's how to add another static page.
Have the html of your page saved in the ```app/views/pages``` directory with an ```html.erb``` extension.

Start by creating a controller for the pages.
```
$bin/rails generate controller pages --skip--assests
```
Then, change directories to the ```app/controllers/```. Open the pages_controller.rb file and add the following:
```
class PagesController < ApplicationController
  def show
    render template: "pages/#{params[:page]}"
  end
end
```
The show action will now create a page template under the name of the parameter that is passed in.

Now, go to the ```routes.rb``` file and add the following.
```
Rails.application.routes.draw do
  get "/pages/:page" => "pages#show"
end
```

Now, any URL with ```/pages``` in it will be redirected to the approriate controller (ex. ```/pages/home```).

<h2>Now what?</h2>
At this point, you have learned the basics on how to set up a web project using rails. Take this knowledge to make your own project!



