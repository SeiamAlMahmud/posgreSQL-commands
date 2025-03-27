![PostgreSQL](https://upload.wikimedia.org/wikipedia/commons/2/29/Postgresql_elephant.svg)

## Here are the steps to install PostgreSQL on a VPS (Virtual Private Server):

## 1. Install PostgreSQL:

#### 1. Log in to your VPS: SSH into your VPS using the command:

```bash
ssh username@your-vps-ip
```

#### 2. Update your system: Before installing anything, update your system's packages:

```bash
sudo apt update
sudo apt upgrade -y
```

#### 3. Install PostgreSQL: Install PostgreSQL and some additional utilities:

```bash
sudo apt install postgresql postgresql-contrib -y
```

- postgresql installs the core PostgreSQL database system.

- postgresql-contrib installs extra features and utilities.

#### 4. Start PostgreSQL service: After installation, the service should start automatically. You can check its status with:

```bash
sudo systemctl status postgresql
```

If it's not running, you can start it with:

```bash
sudo systemctl start postgresql
```

## 2. Create a PostgreSQL Database:

#### 1. Log in as the PostgreSQL user: PostgreSQL uses a separate user (postgres). Log in as that user:

```bash
sudo -i -u postgres
```

#### 2. Access the PostgreSQL command line: Launch the PostgreSQL command line tool:

```bash
psql
```

#### 3. Create a new database: Create a new database by running:

```bash
CREATE DATABASE your_database_name;
```

#### 4. Create a new user (optional): If you want to create a new user, you can do so with:

```bash
CREATE USER your_username WITH PASSWORD 'your_password';
```

#### 5. Grant privileges to the user: To allow the new user to access the newly created database, grant them privileges:

```bash
GRANT ALL PRIVILEGES ON DATABASE your_database_name TO your_username;
```

#### 6. Exit PostgreSQL: After creating the database and user, exit the PostgreSQL shell:

```bash
\q
```

## 3. Create a PostgreSQL Database:

#### 1. Connect to PostgreSQL using the new user: You can now connect to the database with:

```bash
psql -U your_username -d your_database_name
```

#### 2. Configure PostgreSQL for remote access (optional): If you want to allow remote access to your PostgreSQL server, you need to modify the PostgreSQL configuration files:

- Open **postgresql.conf** (usually located at **/etc/postgresql/12/main/** or **/etc/postgresql/{version}/main/**):

```bash
sudo nano /etc/postgresql/12/main/postgresql.conf
```

Find the line with **listen_addresses** and change it to:

```bash
listen_addresses = '*'
```

- Modify **pg_hba.conf** to allow remote IP access:

```bash
sudo nano /etc/postgresql/12/main/pg_hba.conf
```

Add the following line to allow all IP addresses (or specify a specific range):

```bash
host    all             all             0.0.0.0/0            md5

```

### 2. Restart PostgreSQL service: After making changes, restart the PostgreSQL service to apply the configuration:

```bash
sudo systemctl restart postgresql
```

<br />
<br />
<br />
<br />
<br />

## To log in to PostgreSQL on your VPS and view databases, tables, and data, you can follow these steps:

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
<br />
<br />

# Q. **Fixing PostgreSQL Authentication Issue**

If you're encountering issues logging into PostgreSQL with the postgres user (or any PostgreSQL user), you can reset the PostgreSQL password for the postgres superuser by following these steps:

Step-by-Step to Reset PostgreSQL Password:

### 1. Switch to the postgres user (the PostgreSQL superuser):

Run this command to switch to the postgres user, which has superuser privileges within PostgreSQL:

```bash
sudo -u postgres psql
```

### 2. Change the PostgreSQL postgres user password:

Once you're in the PostgreSQL interactive terminal (psql), you can change the password for the postgres user:

```bash
ALTER USER postgres WITH PASSWORD 'new_password';
```

Replace **<span style="color:red;">new_password</span>** with your desired password.

### 3. Exit PostgreSQL:

To exit the psql prompt, type:

```bash
\q
```

### 4. Test the New PostgreSQL Password:

After changing the password, you can try logging into PostgreSQL again using the new password:

```bash
psql -U postgres -h localhost
```

You should be prompted for the new password you just set.
