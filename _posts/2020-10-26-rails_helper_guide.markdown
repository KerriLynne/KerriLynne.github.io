---
layout: post
title:      "Rails Helper Guide"
date:       2020-10-26 18:39:52 -0400
permalink:  rails_helper_guide
---


When we first started working with Rails after learning all of Sinatra, it's easy to be a bit thrown and out of your comfort zone. We had just learned most of the basic concepts coming out of Sinatra but there were so many differences and I was grasping to try and find a better way to comprehend the newness.  
After working through some labs and lessons, the one thing I learned (quickly) was that a cheat sheet was going to be my friend here.  There are many commands that you need to know to be able to function in a Rails development environment.  Below are some basics and tips that I kept at hand to help move me through the process.


Generators- generators are used to build out standard features of certain parts of your rails application.  For all generators, you will type ```rails g``` or ```rails generator``` followed by your command.  Your commands will differ depending on what you're working on, what you will need and what has already been created.  

Resource generator- a great command to begin with that does alot for you; creates a new model, corresponding database table, controller, and an empty views folder:
```
rails g resource ModelName column_name:datatype column_name2:datatype
```

Migration Generators:
Creating a migration - used to create just a table and columns/ data types within:
```
rails g migration CreateTable name_of_column:datatype name_of_column2:datatype
```

Adding a column- used to add a new column with a data type to an existing table:
```
rails g migration add_name_of_column_to_table_name name_of_column:datatype
```

Removing a column- used to remove an existing column from an existing table:

```
rails g migration remove_name_of_column_from_table_name name_of_column:datatype
```

Model generator- used to create just a model with a corresponding table:

```
rails g model NameOfModel column_name:datatype column_name2:datatype 
```

Controller generator- used to create just a controller but can add in a method like 'new' or 'index' and the specified methods will be auto created:

```
rails generate controller Controller_name method
``` 


Routes- Creating routes is a new experience when moving to rails, below is some syntax for resources that cover most of your bases:
This syntax is used to provide all routes for a controller:

```
resources :controller_name
```

This syntax will provide specific routes that you choose (you might not need all given routes for everything):

```
resources :controller_name, only: [:new, :create]
```

This syntax will provide nested routes expressing a dependent relationship:

```
resources :parent_controller_name do 
resources :child_controller_name end
```

This syntax is used for custom routes based on your methods in your controllers. You can specify the route the method should go to:

```
get '/login', to: 'sessions#new'
```

Remembering the exact paths to all of your routes can get challenging during a project.  The below command will list out all of the routes available to you so you can review all of the paths, verbs, URI patterns or controller actions each route is linking to:

```
rails routes
```

You can also view the route info on your server which is usually larger and more readable:

http://localhost:3000/rails/info/routes

To view the routes only belonging to one resource, use this command in your terminal:

```
rake routes | grep resource_name
```


You might accidentally run another server while working in your application and your server will no longer work:
This command will show you the additional servers that are running:

```
lsof -wni tcp:3000
```

Use the PID number that the above command will return, and then run this command:

```
kill -9 PID
```


Hopefully this will save you from doing extra googling or looking back to your notes.  Having necessary rails notes at hand are perfect for moving you through at least your first project.
