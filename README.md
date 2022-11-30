# Containerized Laravel App
This applications was built using [Laravel](https://laravel.com) as the web application framework, [php](https://www.php.net/) as the programming language, [NGINX](https://www.nginx.com/) as the web server, and [Docker](https://www.docker.com/) as the development environment. 

The application has the functionability of:
- Creating an user account with an email and password,
- Creating a listing/job posting,
- Manage past listings/job postings,
- Search by tags, titles, places.


### To run this application in your machine:
- Make sure [Docker Desktop](https://docs.docker.com/get-docker/) is installed,
- Make sure to have [Git](https://git-scm.com/downloads) installed,
- Have a [code editor](https://code.visualstudio.com/).

**1.** Use the following command to clone the laravel-app code from my [GitHub repository](https://github.com/ncalderon94/feedback-form.git) into your machine.

```
git clone https://github.com/ncalderon94/laravel-app.git
```

Note: Make sure to run the ``` git clone ``` command on the directory that you would like the app to be downloaded.  

**2.** Modify the user and password for the database in the docker-compose.yml file.

- Open the docker-compose.yml file and edit the ```MYSQL_USER:``` and ```MYSQL_PASSWORD:``` values to the username and password that you would like to use when using the database. These values are going to be used by phpmyadmin to administrate the database. 

- Change the values and save the document. 

**3.** Run the application 

- ```docker-compose up``` will run the containers and ``` -d ``` will allow the process to run in the back and will let you use the terminal in the process.

```
docker-compose up -d
```

Note: To confirm that the app is running in your machine, simply type *localhost:port* in the url of the web browser of your choice. See table below for ports.

|Service    |Port          |
|:---       |:----:        |
|web server | 8080 and 443 |
|phpMyAdmin | 80           |


The services can use any port. You can modify the ports in the *docker-compose.yml* file. If you modify any of the ports after running the previous command:
1. Save the .yml file changes,
2. Run ```docker-compose down```
3. Then ```docker-compose up -d``` to see the changes.

### Play with the app using artisan commands

All commands are to be started using ```docker-compose exec app```. In where **app** is the name of the service stated in the ```docker-compose.yml```

Using your text editor and terminal...

**1.** You can generate fake users. 

- Go to: ```database/seeders/DatabeseSeeder.php``` and edit the quantity of users that you would like to generate in **line 19**. Save the document and run this command:

```
docker-compose exec app php artisan db:seed
```

This is asking artisan to **seed** the database using the *factories* as a guide from ```UserFactory.php``` file. It will generate the quantity stated in **line: 19**.  

**2.** You could install *Clockwork* on the web server.

Clockwork is a development tool for php within your browser. 
- Install the *Clockwork* web browser extension. Then run the following command on your terminal.
```
docker-compose exec app composer require itsgoingd/clockwork
```
With the help of composer, you just installed Clockwork. 

---

**Would like to add the following features:**
- [ ] Reset your password functionality.
- [ ] Owner of listings: delete multiple listings at once.
