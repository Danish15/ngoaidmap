#NGO FRONT APP + API

## Table of Contents

1. [Ruby Version](#ruby-version)
2. [Rails Version](#rails-version)
3. [Install System Dependencies](#install-system-dependencies)
4. [Install the App](#install-the-app)
5. [Front-End Build Tools](#front-end-build-tools)
6. [Running Tests](#running-tests)
7. [Deploying](#deploying)


### Ruby Version

Ruby version is specified in both the `Gemfile` and `.ruby-version`. As of this writing, the Ruby version used is 2.2.1.


### Rails Version

Rails version is specified in the `Gemfile`. As of this writing, the Rails version used is 4.2.1.


### Install System Dependencies

#### Install Homebrew:
Ensure you have [Homebrew](http://brew.sh/) installed on your machine. We'll use this to install further dependencies.

#### Install PostgreSQL:
```
  brew install postgresql
```

#### Install Redis:
```
  brew install redis
```

#### Install rbenv:
```
  brew install rbenv
  rbenv init
```
It is recommended that you double-check the [installation instructions](https://github.com/rbenv/rbenv#homebrew-on-mac-os-x) for installing rbenv with Homebrew. Theres is also a git alternative to installing rbenv.

#### Install NVM:
It is recommended that you use [NVM](https://github.com/creationix/nvm) to install and manage your [Node](http://nodejs.org/) and corresponding npm versions. There is no Homebrew option for installing NVM.

Install NVM per the directions in the [linked repo](https://github.com/creationix/nvm). The node version is documented in `.nvmrc`.  As of this writing, the Node version has been set to 5.11.0.


### Install the App

#### Repo
To get started, clone this repo:

```
  git clone git@github.com:vigetlabs/bozzuto.git
```

#### Ruby
Install Ruby `2.2.1` with rbenv:
```
  rbenv install 2.2.1
```

#### Bundler
Install Bundler for gem dependencies:
```
  gem install bundler
```

Then run install to fetch the dependencies:
```
  bundle install
```

#### PostgreSQL
Start PostgreSQL:
```
  brew services start postgreql
```

Later, you may need to restart or stop PostgreSQL:
```
  #Restart PostgreSQL
  brew services restart postgresql

  #Stop PostgresQL
  brew services stop postgresql
```

#### Redis
Start redis:
```
  brew services start redis
```

Later, you may need to restart or stop redis:
```
  #Restart Redis
  brew services restart redis

  #Stop Redis
  brew services stop redis
```

#### Config files
Some application configuration should not be checked into source control. You need to create copies to run the app locally.

For the database:
```
  cp config/database.yml.sample config/database.yml
```
After copying the file, leave `database.yml` as-is and don't bother setting up a local database. We'll use `rake` to do that automatically soon.

For your environment:
```
  cp .env.sample .env
```
Fill in this file as necessary.


#### Setup the database
We'll use `rake` to setup the database. This dependency should have been installed when you ran `bundle install` earlier on.

```
  bundle exec rake db:create
  bundle exec rake db:migrate
  bundle exec rake db:seed
```

#### Install Bower and Grunt Dependencies
We'll use Bower to manage our Grunt and asset build tool dependencies. However, first we need to install Bower with npm. As of this writing, we are using Bower version 1.7.9. The current version is recorded in `package.json`.

```
  npm install bower@"1.7.9"
```

Then install Bower dependencies:
```
  npm run bower install
```

**NOTE:**  In this repository, node modules and dependencies are currently checked into the repository in the `node_modules` directory, so you may get some git diffs after installing your local setup.


#### Run the app
At this point, the application should be ready to run locally. Start the server:
```
  bundle exec rails s
```
Visit [http://localhost:3000](http://localhost:3000) in the browser. 🚀

If you ever need to access the Rails console while working, start that with:
```
  bundle exec rails c
```


### Front-End Build Tools
TBD

### Running Tests
TBD

### Deploying
TBD
