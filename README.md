# reactInertiaLaravelDemo
A tutorial on the setting up for a React frontend and Laravel backend application, with an Inertia.js as middleman, using local PostgreSQL as RDBMS for my Cloud Computing groupmates.

## Setting up

Install PHP, Composer, and the Laravel installer.

For Windows, run as administrator:
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://php.new/install/windows/8.4'))
```

For MacOS:
```
/bin/bash -c "$(curl -fsSL https://php.new/install/mac/8.4)"
```

For Linux:
```
/bin/bash -c "$(curl -fsSL https://php.new/install/linux/8.4)"
```


## Create an application

Run the command:
```
laravel new app-name
```

When prompted for a starter kit to install, enter 'none'.

When prompted for a testing framework, enter '1'.

Enter 'no' when asked to install Laravel Boost.


## Installing Laravel Breeze

Navigate into the application folder, e.g.:
```
cd app-name
```

Run the commands:
```
composer require laravel/breeze --dev
php artisan breeze:install
```

When asked for Breeze stack, select React with Inertia by entering 'react', and press enter when asked for optional features.

Again, enter '1' for testing framework.


## Installing PostgreSQL with pgAdmin 4 and making a database

Install PostgreSQL locally and ensure the pgAdmin 4 checkbox is checked for installation too:
<a>https://www.enterprisedb.com/postgresql-tutorial-resources-training-1?uuid=867f9c7f-7be7-44ed-b03f-103a0a430d51&campaignId=postgres_rc_18</a>

Set the password for PostgreSQL and open pgAdmin4.

Expand the 'Servers' menu and select the PostgreSQL menu inside.

With PostgreSQL selected, open the 'Object' dropdown menu and create a database.

Call the database 'cloud_computing', leave the owner as 'postgres' and save.


## Configuring the database (a continuation from this repo's current code and file structure)

You will currently have a file in the application's root folder called '.env.example'.

Rename the file to '.env'. (This helps protects the database details you will be adding in the next step.)

Open the .env file and change the following fields to the values according to your already existing PostgreSQL database:

```
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=cloud_computing # call your database this!!!!
DB_USERNAME=postgres
DB_PASSWORD=<your_database_password>
```

After doing so, run the command:
```
php artisan migrate
```


## Running the application

Open a terminal in VS Code and run the following command:
```
php artisan serve
```

Open another terminal and run:
```
npm run dev
```

After running `npm run dev`, there will be red text showing the Laravel version, and underneath, a link to the application's URL.

Click the `APP_URL` to access the application via your local host.
