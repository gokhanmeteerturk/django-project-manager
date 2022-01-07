# django-project-manager
![status](https://img.shields.io/badge/Project%20Status-%2520-yellow) 
![python](https://img.shields.io/badge/python-v3.9-blue) 
![django](https://img.shields.io/badge/Django-v4.0-red)

A complete project management app built with Django and Python.

---
### Setup:
1. Clone project by HTTPS or CLI


2. Install django and other requirements:
    >pip install -r requirements.txt
   

3. Check Django version:
   > python -m django --version

   
4. Create project:
   > django-admin startproject pm_project

5. Move to the project directory:
   > cd pm_project

6. Create app:
   > python manage.py startapp pm_app

7. Edit `settings.py` from the project directory, add this string to
   the `INSTALLED_APPS` list:
   > 'pm_app.apps.PmAppConfig'
   > 
8. Again, edit `settings.py` file. This time, configure database connection
   with your own credentials:
   ```
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.mysql',
           'OPTIONS': {
               'read_default_file': '/etc/my.cnf',
           },
           'HOST': '127.0.0.1',
           'NAME': 'YOUR_DATABASE_NAME_AS_STRING',
           'PASSWORD': 'YOUR_DATABASE_USER_PASS',
           'USER': 'USERNAME_OF_YOUR_DATABASE_USER'
       }
   }
   ```
9. You should skip this step if you already setup a db, a db user and your
   settings.py as in step 8.
   
   If you are not familiar with SQL or databases in general, here is
   how to setup a basic db connection for MySQL or MariaDB (assuming
   you've mysql or mariadb installed already):

   ###### (edit YOUR_USERNAME and YOUR_PASS as you like)
   
   1. Create db user:
      
      `CREATE USER 'YOUR_USERNAME'@'%' IDENTIFIED WITH mysql_native_password BY 'YOUR_PASS';`
   
   2. Create a database scheme:
      
      `CREATE DATABASE pm_db;`
      
   3. Grant permission on this new scheme to your new user:
      
      `GRANT ALL ON pm_db.* TO 'YOUR_USERNAME'@'%';`
      
   4. Reload the permissions table so they will take effect immediately:
      
      `FLUSH PRIVILEGES;`
   

10. Migrate initial db setup:
   > python manage.py migrate

11. Create an admin user for the admin app (and follow the steps):
   > python manage.py createsuperuser