- #Dev-Notes #Database
-
- Description : Liquibase notes
-
- ## Introduction
	- Open source database migration tool
	- Track, version, deploy database schema changes
	- Uses commands and **Change Types** (changes to database schema) to specify what is needed to do and how would it be done
	- Uses **ChangeLogs** and Tracking Table to determine what is deployed to the database after the commands have been run
	- Creates and executes rollback
- ## Supported Databases
	- Oracle
	- PostgreSql
	- Mssql
	- H2
	- Db2
	- MariaDb
	- MySql
	- SqlLite
	- Informix
	- Apache Derby
	- Snowflake
	- CockroachDb
	- SyBase
	- Cassandra
	- MongoDb
	- Sap Hana
	- Amazon Aurora
	- Amazon RDS
- ## Schema Changes
	- Fundamental unit of change in Liquibase
	- Schema changes are written using SQL statements that create, modify, or drop database objects
	- Typical schema changes are create table, add index, and drop column
	- In XML, YAML, or JSON, the same schema changes are modeled as Liquibase **Change Types**
	- ### ChangeLog
		- Changes are written in **ChangeLog**
		- In most cases, there should be one file per application release
		- Supported formats : XML, JSON, YAML, SQL
		- One or more **ChangeSets** are contained in a **ChangeLog**
		- **ChangeLogs** are text files containing schema changes. They should be stored and versioned in the preferred source control tool
		- **ChangeLog** can inlcude other **ChangeLogs**. This allows multiple teams to each work on their own **ChangeLogs** so they can work independently
	- ### Change Types
		- One or more schema changes are grouped into a **ChangeSet**
		- The best practice is to limit each **ChangeSet** to only one **Change Type**
	- ### ChangeSet
		- **ChangeLogs** contains **ChangeSets**
		- Unit of change
		- One logical change per change set
		- Identified by the author name and id
# Tracking Tables
- Used to track, version, and deploy database schema changes
- If the database does not contain a tracking table, Liquibase will create one
## DatabaseChangeLogs
- Tracks each **ChangeSet** in the **ChangeLog** by id, author, and the file where the **ChangeSet** resides
- The composite of id, author, and filename is unique across all rows of the table
## DatabaseChangeLogLock
- Ensures only one instance of Liquibase is running at one time
- It locks others out to prevent multiple Liquibase commands from being executed at the same time which could cause database conflict
- Ensures in keeping other devs, dba, or teams from overwriting changes accidentally
# Liquibase Lifecycle
1. Use the **ChangeLog** to write changes using **ChangeSets**
2. Push the changes to the database with the Liquibase commands
3. Tracks changes with a **DatabaseChangeLog Tracking Table**
4. Protects changes with the **DatabaseChangeLogLock** so that other teammates will not override the changes
# Liquibase Commands
## update
- Applies to all unrun changes
## rollback
- Reverts changes the have made in the database
## snapshot
- Used to quickly compare changes in the database or keep a record of the current database state
## dbDoc
- Generates database change documentation
## diff
- Compare two database of the same type or different types to one another
## diffChangeLog
- Used to create a deployable **ChangeLog** to synchronize multiple database
## generateChangeLog
- Creates a **ChangeLog** file that has a sequence of **ChangeSets** which describes how to re-create the current state of the database
## rollbackOneChangeSet
- reverts one non-sequential **ChangeSet** made during previous change to the database
## rollbackOneUpdate
- reverts all **ChangeSets** releted to a specific **deploymentId** made during a previous change to the database
## rollbackOneUpdateSql
- A helper command that allows inspecting the SQL Liquibase that will run (revert all **ChangeSets** associated with the **deploymentId** specified in the rollbackOneUpdate command)
## rollbackOneChangeSetSql
- A helper command that allows inspecting the SQL Liquibase that will run (revert the **ChangeSet** specified in the rollbackOneChangeSet command)
## history
- A helper command that lists out all the **deploymentIds** and all **ChangeSets** associated with each **deploymentId**
# liquibase.properties File
- If file was named differently or was stored else where, use --defaultFile option in CLI
## changeLogFile
- Path to **ChangeLog**
## driver
- Class name to target database
## url
- Target database
## username
- Username for the target database
## password
- Password for the target database
## referenceDriver
- Driver class name for the source database
## referenceURL
- Starting point or source database and basis for the comparison
## referenceUsername
- Username for the source database
## referencePassword
- Password for the source database
## liquibaseProLicenseKey
- For pro users
## classpath
- Path for the database driver
# ChangeSet Common Attributes
## stripComments
- Set true to remove any comments in the SQL before executing, otherwise false. Defaults to true if not set
## splitStatements
- Set to false to not have Liquibase split statements on ;'s and GO's. Defaults to true if not set
## rollbackSplitStatements
- Same as splitStatement but for rollback SQL
## endDelimiter
- Delimiter to apply to the end of the statement. Defaults to ";", may be set to ""
## rollbackEndDelimiter
- Same as endDelimiter but for rollbackSQL
## runAlways
- Executes the **ChangeSet** on every run, even if it has been run before
## runOnChange
- Executes the change the first time it is seend and each time the **ChangeSet** has been changed
## context
- Executes the change if the particular context was passed at runtime. Any string can be used for the context name and are checked case-insensitively
- Can be specified using AND, OR, !, and parentheses in the **ChangeSet**. Without the parentheses the order of operations are !, AND, and then OR
- Using "," to separate contexts works like an OR operation but with the highest precedence
## logicalFilePath
- Use to override the file name and path when creating the unique identifier of **Changesets**
- Required when moving or renaming **ChangeLogs**
## labels
- Are a general-purpose way to categorize **ChangeSets** like contexts, but working in the opposite way
- Instead of defining a set of contexts at runtime and then a match expression in the **ChangeSet**, defined a set of labels in the context and a match expression at runtime
## runInTransaction
- Should the **ChangeSet** be run as a single transaction. Defaults to true
- **Warning:** If set to false and an error occurs partway through running a **ChangeSet** containing multiple statements, the Liquibase **DatabaseChangeLog** table will be left in an invalid state
## failOnError
- Should the migration fail if an error occurs while executing the **ChangeSet**
## dbms
- The type of a database which that **ChangeSet** is to be used for
- When the migration step is running, it checks the database type against this attribute