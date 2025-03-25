# To log in to PostgreSQL on your VPS and view databases, tables, and data, you can follow these steps:

## 1. Log in to PostgreSQL

To log into PostgreSQL on your VPS, use the **psql** command. You need to have the **_psql_** client installed on your system. The basic syntax to log in is:

```bash
psql -U postgres -h localhost
```

### Here’s the breakdown:

- **-U postgres:** Specifies the user to log in as (**_postgres_** is the default superuser).

- **-h localhost:** Specifies the host (if you're logging into a local database, **_localhost_** will work).

If your PostgreSQL instance is on a remote VPS, you can use its IP address or hostname instead of localhost.

If you're using a specific database and not the default one, you can specify the database name as follows:

```bash
psql -U postgres -h localhost -d your_database_name
```

It will prompt you for a password if authentication is required.

## 2. List Databases

Once you're logged into PostgreSQL (**psql**), you can list all databases with the following command:

```bash
\l
```

This will display all the databases in your PostgreSQL server.

## 3. Switch to a Database

To switch to a particular database, use the following command:

```bash
\c your_database_name
```

Replace **<span style="color:red;">your_database_name</span>** with the actual database name you want to work with.

## 4. List Tables

To see all the tables in the current database, use the following command:

```bash
\dt
```

This will list all tables in the current database.

## 5. View Table Structure

To view the structure (schema) of a specific table, you can use:

```bash
\d table_name
```

Replace **<span style="color:red;">table_name</span>** with the name of the table you want to inspect. This will show you the columns, types, and any constraints on the table.

## 5. View Data in a Table

To view the data in a table, you can run a SELECT query. For example:

```bash
SELECT * FROM table_name;
```

This will display all rows of data in the specified table. You can also apply filters, like:

```bash
SELECT * FROM table_name WHERE column_name = 'value';
```

## 7. Exit PostgreSQL

To exit the **_psql_** command-line interface, simply type:

```bash
\q
```

## Example Workflow

1. Log in to PostgreSQL:
   ```bash
   \q
   ```
2. List databases:
   ```bash
   \l
   ```
3. Switch to a specific database:
   ```bash
   \c your_database_name
   ```
4. List all tables:
   ```bash
   \dt
   ```
5. View table structure:
   ```bash
   \d your_table_name
   ```
6. View data from a table:
   ```bash
   SELECT * FROM your_table_name;
   ```

### That's it! You should now be able to interact with PostgreSQL, view databases, tables, and the data within them. Let me know if you need more help!

# **For Vps**

## Q.

The error message you're receiving, **_password authentication failed for user "postgres"_**, suggests that there is an issue with either the password you're providing for the postgres user or the authentication method in PostgreSQL. Let's go through the steps to resolve the issue.

## 1. Check the postgres user password

If you're sure that the postgres user password is correct, try to reset it.

To reset the password for the postgres user, follow these steps:
Resetting PostgreSQL postgres user password:

### 1. Log in as the **_postgres_** user:

On your VPS, switch to the **_postgres_** user:

```bash
sudo -u postgres psql
```
This should drop you into the psql command line as the postgres superuser, without requiring a password.
