# Active Record Design Your Own
 
##Learning Competencies 

* Use Active Record Migrations to create a database
* Use Active Record Queries to query a database


##Summary 

Now that you've had a chance to implement Active Record in a couple of different defined problem spaces, it's time to take over and build from scratch on a problem space of your choice.  The purpose of this exercise is to deepen your learning of Active Record and give you a sandbox to work in for the future. 

The releases have suggested time boxes to keep you moving along.  If you are well over the time suggested, call for help. 

##Releases

###Release 0 : Choose A Problem Space and Requirements (30 min).

####Step 1: Choose a Problem Space
A problem space is just a fancy way of saying choose what you want to work on and explore Active Record in. You can choose whatever you like as long as it meets these basic requirements:

* The data can be represented in a relational database with at least 3 tables and at least one many-to-many and one one-to-many relationship.
* There is data for you to use (like a csv file) or it is easy to create data using `faker`.  
* You can write at least 5 user stories that define the requirements for your problem space.  For example (You can list the senators from a state).  At least 1 of these stories needs to be complex (require some calculation)
* You can succinctly define the problem space in two or three sentences.


####Step 2: Write the Requirements (User Stories)
Requirements or User Stories define how we want our program to act. In this case, how we want our program to interact with the data. Write at least 5 user stories and 1 complex user story.

####Step 3: Design the Schema
Use SQL Designer to design the schema that will meet these requirements. 

####Step 4: Write the README.md
In the `ar-design-your-own` directory, add your 
* Problem Space description
* List of requirements
* Embedded Image of Schema Design

####Step 5: Check Off
Grab a staff member, coach or (if neither of these are available, a student other than your pair) and walk through your README.  Make sure you can describe what you are going to do and that your schema does in fact meet your requirements.  If not, make adjustments as needed.
In the last line of your README add a statement "Checked off by 'bob'".

###Release 1 : Build the Skeleton (1 hour)
Up to this point, you have been building your AR challenges off of an existing skeleton. It's time for you to take ownership of this skeleton by writing on yourself.  The goal of this step is to get you closer to understanding all the code in a skeleton (you may not get all of it which is ok).

####Step 1 : Use Existing Skeleton As A Guide
You will be creating a skeleton that is essentially the same as the [AR Sunlight Legislators](https://github.com/sea-lions-2014/activerecord-congress-database-1-modeling-congresspeople-challenge/tree/master/source) skeleton.  Open this and use it as a guide as you walk through the rest of these steps. **DO NOT COPY AND PASTE**

####Step 2: Create the Directories
Inside your `ar-design-your-own` directory, add the following folders:
* app
* app/models
* db
* db/data (if you have external data files (like CSV))
* db/migrate
* lib
* spec


As you create each directory, discuss with your pair what will be stored here.

####Step 3: Setup Configuration Files.
Many of the files in this skeleton are used to configure your application files and load external files.  As you create each one, try to know why the file is important and what **at least one** line of code does.  If you don't know all lines at this time that is ok, just type them in.  ** DO NOT COPY AND PASTE **  

Create these files in the root directory
* Gemfile
* Rakefile - modify to match your database file names, only add the tasks you will need.
* .gitignore  
* (the .gitkeep file is empty so you don't need it yet)

Create these files in their appropriate sub folders
* db/config.rb 

Remove files and references you are not using.  (ex: 'legislators.csv' )

####Step 4: Up and Running
Make sure your skeleton is configured well by creating the database, a migration and a model

* To create the database, run `rake db:create`
* To create the migration, run `rake db:create_migration`  then edit the migration to add table and fields
* To run the migration, run `rake db:migrate`
* To create a model, add a file to the models folder with a model class and a link to the db/config file.  **Note - there are better ways to link files, but this will work for now**

```ruby
require_relative '../../db/config'

class YourModel < ActiveRecord::Base
# implement your YourModel model here
end

```

You should now be able to work with your model.  To test this, run `rake:console` to open your application in irb. Test it out by running 

* `YourModel.create(creation data here)`
* `YourModel.all - should list all the instances of your model. 

You can also test by opening your database in sqlite3 and verifying your schema and data. 


###Release 2 : Migrations


###Release 3 : Associations


###Release 4 : Validations

###Release 5 : Play (optional)
There are a lot of ways you can experiment with this challenge.  Here are a few:
* Add Rspec tests in the `spec` directory
* Add custom validation methods
* Create methods to query your data in various ways.






In the `db/migrate/20121011144238_create_students.rb` file, you should use ActiveRecord migrations to implement the `change` method. This will allow us to do all of our database schema modifications completely from within code (rather than using SQLite and SQL Designer).  Use the Railsguides [Migration Overview](http://guides.rubyonrails.org/v3.2.13/migrations.html) to get used to the syntax.

#### Test Your Code

Run your migrations using the following command:

```bash
$ rake db:migrate
```

Before submitting this challenge, you must test your code by using the following command:

```bash
$ rspec spec/migrate_create_table_spec.rb
```

All tests should pass.  If the output of the test is confusing, take a look under the hood.  How does the spec file test for expectations?  This is very similar to ruby, see if you can figure it out.

###Release 1 : Your First Object-Relational Model

Create a class called `Student` (in the `app/models/student.rb` file) that meets the following requirements:

#### User Stories

1. Given a `Student` model object, I should be able to easily retrieve her full name via a `name` method.
2. Given a `Student` model object, I should be able to easily know her age (in years) via an `age` method.

Don't overcomplicate this!  From this user story, we can infer that `student.name` would likely be the syntax to access the `name` method. 
What can we infer is needed in the `Student` Class?

#### Test Your Code

Before submitting this challenge, you must test your code by using the following command:

```bash
$ rspec spec/student_spec.rb -e "#name and #age"
```

All tests should pass.

###Release 2 : Validation Magic

Add validations to the `Student` model so that a student cannot be saved unless the following requirements are met:

1. Email addresses must contain at least one `@` character and one `.` character, with at least one character before the `@`, one character between the `@` and first `.`, and at least two characters after the final `.`.
2. Email addresses must be unique across all students.
3. Students must be at least `5` years old.

A great resource for validations is the Railsguides [Validation Overview](http://guides.rubyonrails.org/v3.2.13/active_record_validations_callbacks.html), don't forget to use google too!

#### Test Your Code

Before submitting this challenge, you must test your code by using the following command:

```bash
$ rspec spec/student_spec.rb -e "validations"
```

All tests should pass.


###Release 2 : More Advanced Validations

Add another validation to the `Student` model so that a student cannot be saved unless the following requirement is met:

Phone numbers must contain at least 10 digits, _excluding_ non-numeric characters.

#### Test Your Code

Before submitting this challenge, you must test your code by using the following command:

```bash
$ rspec spec/student_spec.rb -e "advanced validations"
```

All tests should pass. 


##Optimize Your Learning 

##Resources

* [Validation Overview](http://guides.rubyonrails.org/v3.2.13/active_record_validations_callbacks.html)