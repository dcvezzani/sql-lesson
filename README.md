## Sql Lesson Outline

### Relational databases
- store data in categorized fashion
- combine tables to present data in desired fashion

#### [Install postgresql](https://www.postgresql.org/download/windows/) on your windows laptop

Log in through terminal.  When postgresql was installed, it should have created a user using your Window's username.  If no username is provided when logging in, the default user created during installation should be used.
```
psql
```

Perhaps the most popular use of a database (even more than for learning SQL!) is to provide data storage for an application.  That being the case, ou will likely want to create a new Postgres user account to be associated with a given application.  In this way, you can limit what the user can do with the database.

Since this is a "learning" walk through, we will give this new user access to... well, everything with `grant all privileges`, but we will only do so for the scope of the `myDatabase_admin` database.  As you can create multiple databases for a given Postgres installation, this will prevent `myDatabase_admin` from touching databases that are not his.

#### Create new database and user
```
create database myDatabase;
create user myDatabase_admin with encrypted password 'mypass';
grant all privileges on database myDatabase to myDatabase_admin;
```

Log in through terminal, connecting to the database just created, using the user that was also just created
```
psql --username myDatabase_admin -h localhost myDatabase --port 5432 --password
```

Postgres can be a little cryptic on commands that are not SQL.  This one can be used to show what tables are currently available in your database.
```
\dts
```

#### Useful commands
- `\?` can be used to show all of the non-sql Postgres commands that can be used to show stats for the database, lists of tables, indexes, sequences, etc.  Don't worry if you don't know what all of those terms are.  You will.
- `\h` can be used to show all of the sql commands that are available in Postgres

### Determine the data that needs to be stored

Ok.  So you have a database set up.  Now what?  It would be useful to start storing data in the database, right?  

- Storage: You need to store data somewhere that can be retrieved
- Availability: There could be many people saving/fetching data from this database at the same time.
- Data integrity: We want to make sure that integers are stored as integers, longs and longs, etc.  And, of course, we'll have strings too

#### Walk-through
The next step is determining a data schema for a table we want to store data in and later on fetch.

Here is a [walk-through](https://www.tyler-wright.com/mysql-exercise-music-database/) of how you might design a db schema for your music collection.  While this walk-through's context is MySQL, the syntax provided should be the same as what is used for Postgres SQL.

### Share your work

To share your works, questions, etc., use this git repo as follows:
```
# pull the latest code (in case someone else committed content
git pull origin master

# add your updates
git add . # add everything

# commit your updates
git commit -m "adds my updates"

# push updates to the remote repo
git push origin master
```
