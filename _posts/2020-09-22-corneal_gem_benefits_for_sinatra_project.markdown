---
layout: post
title:      "Corneal Gem Benefits for Sinatra Project"
date:       2020-09-22 12:31:19 -0400
permalink:  corneal_gem_benefits_for_sinatra_project
---


For the Sinatra AR project we we’re given the guidelines to build this app, but once you start diving in, it's like the training wheels you've only ever known are gone and you are completely on your own ..eekk!  This is a scary place to be for any new developer. We were shown how to create a file structure from scratch, however, my technical coach was kind enough to introduce us to the Corneal gem. His advice was ‘your probably want to use this, it’s just going to be so much easier’- and he was 100% right.

Since the entire process of an app is, well, complicated- this added helper takes the sting away from the initial uncertainty of building this project. Once the gem is already installed through your terminal, you can create the file for your project, then create your repo on GitHub for your project. When you change directories into your appropriate file and open it, it’s like a magic wizard came to your rescue.

Below is the basic file structure provided by this gem once you open your file:

```
── config.ru
├── Gemfile
├── Gemfile.lock
├── Rakefile
├── README
├── app
│   ├── controllers
│   │   └── application_controller.rb
│   ├── models
│   └── views
│       ├── layout.erb
│       └── welcome.erb
├── config
│   ├── initializers
│   └── environment.rb
├── db
│   └── migrate
├── lib
│   └── .gitkeep
└── public
|   ├── images
|   ├── javascripts
|   └── stylesheets
|       └── main.css
└── spec
    ├── application_controller_spec.rb
    └── spec_helper.rb
```

		
		
		
The gem provides an already a built in file structure including all of your MVC folders (Models, Views and Controllers), gemfiles, config.ru, environment.rb and database files.  One of the best features of this gem is the already created style sheet. This makes it so that right from the start you are actually seeing a relatively put together front end webpage and not just arbitrary text in a browser.

Below is the pre-built CSS file:

```
@media screen {
  /* --- Reset Styles --- */
  * {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  html, body {
    height: 100%;
    width: 100%;
  }

  /* --- Welcome Page Styles --- */
  body {
    background-color: lightblue;
    color: #333;
    font-family: Sans-Serif;
    line-height: 18px;
  }

  .wrapper {
    background: #fff;
    -moz-box-shadow: 0 0 10px rgba(0,0,0,.3);
    -webkit-box-shadow: 0 0 10px rgba(0,0,0,.3);
    box-shadow: 0 0 10px rgba(0,0,0,.3);
    margin: 16px auto;
    max-width: 960px;
    padding: 2.25%; /* 18px / 800px */
    width: 85%;
  }

  h1 {
    font-size: 36px;
    line-height: 54px;
  }

  h2 {
    border-bottom: 2px solid #ccc;
    font-size: 24px;
    line-height: 36px;
    margin-bottom: 16px;
  }

  h3 {
    font-size: 18px;
    line-height: 36px;
  }

  p {
    margin-bottom: 18px;
  }

  .main {
    overflow: hidden;
  }

  .content {
    float: left;
    width: 60%; /* 480px / 800px */
  }

  .sidebar {
    background: #eee;
    border: 1px solid #ccc;
    float: right;
    padding: 2.08333333333%; /* 5px / 240px */
    width: 30%; /* 240px / 800px */
  }

  .sidebar ul {
    font-size: 14px;
  }

  .branding {
    clear: both;
  }

  footer.branding {
    border-top: 2px solid #ccc;
    margin-top: 20px;
    padding-top: 20px;
  }
}

@media screen and (max-width: 600px) {
  .wrapper {
    -moz-box-shadow: none;
    -webkit-box-shadow: none;
    box-shadow: none;
    width: auto;
  }

  .content, .sidebar {
    float: none;
    width: 100%;
  }

  .sidebar {
    background: transparent;
    border: none;
    border-top: 2px solid #ccc;
    padding: 0;
  }

  h1 {
    font-size: 24px;
    line-height: 36px;
  }

  h2 {
    font-size: 18px;
    line-height: 24px;
  }
}
```

Not only does the folder and file structure appear for you, but the majority of the leg work within some of the pertinent files is also already completed.  This allows a more seamless transition to begin working on your project.

Below is the gemfile layout.  This has essentially everything necessary for a working website- you can add gems as needed while working through your application:

```
gem 'sinatra'
gem 'activerecord', '~> 4.2', '>= 4.2.6', :require => 'active_record'
gem 'sinatra-activerecord', :require => 'sinatra/activerecord'
gem 'rake'
gem 'require_all'
gem 'sqlite3', '~> 1.3.6'
gem 'thin'
gem 'shotgun'
gem 'pry'
gem 'bcrypt'
gem 'tux'

group :test do
  gem 'rspec'
  gem 'capybara'
  gem 'rack-test'
  gem 'database_cleaner', git: 'https://github.com/bmabey/database_cleaner.git'
end
```



Environment.rb with everything you will need:

```
ENV['SINATRA_ENV'] ||= "development"

require 'bundler/setup'
Bundler.require(:default, ENV['SINATRA_ENV'])

ActiveRecord::Base.establish_connection(
  :adapter => "sqlite3",
  :database => "db/#{ENV['SINATRA_ENV']}.sqlite"
)

require './app/controllers/application_controller'
require_all 'app'
```



Below is the set up of the config.ru file- here you will only need to add whatever controllers you are using:

```
require './config/environment'

if ActiveRecord::Migrator.needs_migration?
  raise 'Migrations are pending. Run `rake db:migrate` to resolve the issue.'
end

run ApplicationController
```



Also, the below Rakefile will populate as well:

```
ENV["SINATRA_ENV"] ||= "development"

require_relative './config/environment'
require 'sinatra/activerecord/rake'
```


Ultimately, if you are given the option, this is a great tool to speed up the initial process of creating your app.  It allows you to focus on the MVC structure that will get your application functioning, and you will most likely thank this gem for giving you that extra time back - (you will need it).





