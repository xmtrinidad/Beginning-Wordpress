# Installing WordPress Locally

Two ways:

1.  Install local web server, database server and the WordPress application. (local dev)

2.  Use a web hosting service that has servers already installed and connected to the Internet to immediately share.

## Initial Set-Up Using MAMP

Using MAMP, PHP and a MySQL Database is automatically installed.

With the free version of MAMP, multiple sites can be set-up by putting all the sites in a subfolder; this way site names (domain names) will be listed like a directory.  Another way to have multiple sites is to change the root directory of MAMP to the project folder that is being worked on (MAMP > preferences > web servers)

## Setting up an initial user

From the MAMP application menu, click "Open Webstart page".  When the web page opens go to tools in the nav bar > phpMyAdmin

An interface will open to manage the databases.  Click databases tab and create a new database.

When a new database is created a privileges tab will appear, click on it then click add user account.

Create a new user and generate a password 

Click check all so that the user has global access

There now should be a database and user set up.  The next step is to install WordPress.`
