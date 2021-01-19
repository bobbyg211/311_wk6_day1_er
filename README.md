# Creating an ER Diagram from the Sakila Database

## Setup

You should already have MySQL installed from last week but if you don't, please [install it now](https://dev.mysql.com/downloads/mysql/).

## Instructions

##### Disable Binary Logging (Google Cloud)

We need to alter a setting in our cloud database in order to import the dataset that we need. This setting has to do with "triggers" which we have not learned about directly but that you will look for more practice with later.

1. Navigate to cloud.google.com and make sure you are logged in.

2. Navigate to your SQL instance (Cloud SQL)

3. Under the "configuration" tab on the right side of your screen, select "edit configuration"

4. Under "Enable auto backups" DESELECT "Enable Point-in-Time Recovery"/"_enable binary logging_"

5. Save and restart the instance

##### Import data

We are going to use a sample schema given to use by MySQL.

1. Download the zip directory and extract it

- https://dev.mysql.com/doc/sakila/en/sakila-installation.html
- The DB is called "sakila" under the Example Databases section

2. cd into that directory

- Likely `cd ~/Downloads/sakila-db`

3. Run the connect command followed by `< sakila-schema.sql` to load that database

- `mysql -u root -h <HOST IP FROM WORKBENCH> -p < sakila-schema.sql`

4. After the operation is complete (may take a couple mins) you should have automatically been exited from the `mysql` command

5. Pull up MySQL Workbench so that we can work with a familiar interface

6. You should see an "sakila" database on the left hand side

7. Double-click that database

8. Open a new query and run `select * from actor;`

9. Did you see any data? If not that's ok. The schema is more important here

10. You should see many tables under this database

##### Create ER Diagram

1. With MySQL Workbench open, click the "Database" tab

2. Select "Reverse Engineer"

3. Make sure your connection information is correct and then click "continue"

4. Under "Select the schemas you want to include:" chose "sakila"

5. DESELECT everything except "Import MySQL Table Objects"

6. Click "Execute"

7. You should see a pretty comprehensive ER diagram consisting of 16 tables

8. Answer the following questions about this diagram

##### ER Diagram Diagnosis

1. What is the relationship between the "actor" and "film_actor" tables?

The relationship from "actor" to "film_actor" is one to many. An actor can be on one or more films. The relationship from "film_actor" to "actor" is one and only one. A film can have only one actor. The "film_actor" table seems to be a bridge table between the "actor" and "film" tables.

2. What does the blue diamond next to the "last_update" column on the "inventory" table represent?

This means the attribute "inventory is a simple attribute and is a part of no key. However the diamond is also filled in which means the value cannot be NULL.

3. How many foreign keys does the "payments" table have? How can you tell?

The payments table has three foreign keys. I can tell because three of the table attributes have red symbols next to them, indicating they are foreign keys. There are also three cardinal relationship lines to other tables.

##### ER Diagram upload

1. Take a screenshot of the ER diagram you created and name it "wk6_er_diagram"

2. Copy the screenshot to this directory and upload it (git push) along with this README
