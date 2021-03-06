# Start a Django project

pi@raspberrypi:~ $ django-admin startproject weather

pi@raspberrypi:~ $ cd weather

pi@raspberrypi:~/weather $ ls

manage.py  weather

# Start a Django app

pi@raspberrypi:~/weather $ python3 manage.py startapp myapp

pi@raspberrypi:~/weather $ ls

manage.py  myapp  weather

# Create MySQL database

pi@raspberrypi:~ $ sudo mysql -u root -p

Enter password: PASSWORD

MariaDB [(none)]> use mysql

MariaDB [mysql]> create user pi@localhost identified by 'PASSWORD';

MariaDB [mysql]> create database weather;

MariaDB [mysql]> grant all privileges on weather.* to pi@localhost;

MariaDB [mysql]> quit

# Edit settings.py in ~/weather/weather

# Follow ~/iot/lesson4/weather/settings.txt

# Remember to change PASSWORD for MySQL user

pi@raspberrypi:~/weather $ cd weather

pi@raspberrypi:~/weather/weather $ nano settings.py

# Copy urls.py to ~/weather/weather

pi@raspberrypi:~/weather/weather $ cp ~/iot/lesson4/weather/urls.py .

pi@raspberrypi:~/weather/weather $ cd ..

# Copy admin.py, models.py, views.py, and serializers.py to ~/weather/myapp

pi@raspberrypi:~/weather $ cd myapp

pi@raspberrypi:~/weather/myapp $ cp ~/iot/lesson4/weather/admin.py .

pi@raspberrypi:~/weather/myapp $ cp ~/iot/lesson4/weather/models.py .

pi@raspberrypi:~/weather/myapp $ cp ~/iot/lesson4/weather/views.py .

pi@raspberrypi:~/weather/myapp $ cp ~/iot/lesson4/weather/serializers.py .

# Copy index.html and static files

pi@raspberrypi:~/weather/myapp $ mkdir static templates

pi@raspberrypi:~/weather/myapp $ cd templates

pi@raspberrypi:~/weather/myapp/templates $ mkdir myapp

pi@raspberrypi:~/weather/myapp/templates $ cd myapp

pi@raspberrypi:~/weather/myapp/templates/myapp $ cp ~/iot/lesson4/weather/index.html .

pi@raspberrypi:~/weather/myapp/templates/myapp $ cd ~/weather/myapp/static

pi@raspberrypi:~/weather/myapp/static $ cp ~/iot/lesson4/weather/favicon.ico .

pi@raspberrypi:~/weather/myapp/static $ mkdir myapp

pi@raspberrypi:~/weather/myapp/static $ cd myapp

pi@raspberrypi:~/weather/myapp/static/myapp $ cp ~/iot/lesson4/weather/*css .

pi@raspberrypi:~/weather/myapp/static/myapp $ cp ~/iot/lesson4/weather/*js .

pi@raspberrypi:~/weather/myapp/static/myapp $ cd ~/weather

# Copy controller.py to ~/weather

pi@raspberrypi:~/weather $ cp ~/iot/lesson4/weather/controller.py .

# After the first time, skip these three steps if no changes

pi@raspberrypi:~/weather $ python3 manage.py makemigrations myapp

pi@raspberrypi:~/weather $ python3 manage.py migrate

pi@raspberrypi:~/weather $ python3 manage.py createsuperuser

Username (leave blank to use 'pi'):

Email address: EMAIL_ADDRESS

Password: PASSWORD

Password (again): PASSWORD

Superuser created successfully.

# Run Django server

pi@raspberrypi:~/weather $ python3 manage.py runserver

# Open the Chromium browser on Raspberry Pi via VNC Viewer

# At the first time, go to http://127.0.0.1:8000/admin

# Login with Django administration username (pi) and password

# Click location data to add 

# Location Stevens

# Latitude 40.7451

# Longitude -74.0255

# Click SAVE

# Post the following in HTML form:

# 2018-02-11 17:45:00 to the Dt List at http://127.0.0.1:8000/dt

# 20 to the Tmp List at http://127.0.0.1:8000/tmp

# 50 to the Hmd List at http://127.0.0.1:8000/hmd

# Run native controller service on a separate terminal window

pi@raspberrypi:~/weather $ sudo python3 controller.py

# View app at http://127.0.0.1:8000/home
