1. Update the System Repository

sudo apt update && sudo apt upgrade

2. Install Required Packages
First we have to install necessary dependencies and Python modules for the project:

sudo apt-get install -y git gcc redis python3-setuptools graphviz python3 \
python3-pip python3-venv python3-dev build-essential \
libxml2-dev libxslt1-dev libffi-dev libpq-dev libssl-dev zlib1g-dev

3. Install and create Database
We are going to install PostgreSQL, and create the database. Here we will use, 'netbox' as the username and 'passnetbox' as the password.

sudo apt-get install -y postgresql libpq-dev
sudo -u postgres psql

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/16c1cc23-6e5d-47c7-b71c-ecc22ce3ec5b)

psql (10.15 (Ubuntu 10.15-0ubuntu0.18.04.1))
Type "help" for help.
postgres=# CREATE DATABASE netbox;
CREATE DATABASE
postgres=# CREATE USER netbox WITH PASSWORD 'training';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE netbox TO netbox;
GRANT
postgres=# \q

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6acb2d66-0123-4f7b-a3a9-1037d2b35ed1)

4. Install and test Redis

sudo apt install -y redis-server
sudo systemctl start redis-server
sudo systemctl enable redis-server
sudo systemctl status redis-server

Check the service response

redis-cli ping

PONG

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4167eb00-2319-4f70-a78f-25f30c072e0b)

5. Download NetBox

Clone the netbox repo at /opt directory.

cd /opt
sudo git clone -b master https://github.com/netbox-community/netbox.git

Cloning into 'netbox'...
remote: Enumerating objects: 136, done.
remote: Counting objects: 100% (136/136), done.
remote: Compressing objects: 100% (103/103), done.
remote: Total 58055 (delta 63), reused 65 (delta 33), pack-reused 57919
Receiving objects: 100% (58055/58055), 28.38 MiB | 573.00 KiB/s, done.
Resolving deltas: 100% (45302/45302), done.

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/c74b1ca4-97a4-43d9-871b-2f20dc2abb70)

Create NetBox system user

sudo adduser --system --group netbox
sudo chown --recursive netbox /opt/netbox/netbox/media/

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6392bd0b-8ed0-4bb5-978e-f397b6ede058)

6. Configure and install NetBox service

cd /opt/netbox/netbox/netbox/

sudo cp configuration_example.py configuration.py

We need our focus into 4 part here.

ALLOWED_HOSTS -> we have to put the server hostname or IP; we will use hostname, as we are hosting multiple HTTP service in a single host.

DATABASE      -> fillup the database name, password

REDIS default -> configuration is enough here for the LAB

SECRET_KEY    -> generated in another command terminal

sudo nano configuration.py

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2adc24b6-d3db-4124-95ab-3024c14ff373)

python3 /opt/netbox/netbox/generate_secret_key.py

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/8ec7d7e4-8576-45f1-9b35-f389faf4853e)

CTRL+X

Yes

Now its time to make the run. We will execute the upgrade.sh script. That is going to do few task for us. 

+ It will create a Python virtual environment 

+ All the required Python packages/modules will be installed

+ Database schema will be migrated

sudo /opt/netbox/upgrade.sh

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ec632f96-0412-42ac-a0b0-1a4bb4f5c899)

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4b4d5fb0-86f6-4f00-b0a6-408cdbb166ff)

It will take few minutes to complete the task.

As NetBox doesnt create its user, we have to do it manually. Enter the python environment and use apnic as the user and training as the password.

Type password two times to confirm

source /opt/netbox/venv/bin/activate

cd /opt/netbox/netbox

python3 manage.py createsuperuser

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7defc385-df2a-4666-9d08-b6c545521ad3)

7. Setup the middleware - Gunicorn

For NetBox gunicorn is automatically installed with Django. Next, we are going to setup the service. We will keep the default settings for the LAB.

sudo cp /opt/netbox/contrib/gunicorn.py /opt/netbox/gunicorn.py

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b41312ba-8487-4199-adb2-18a66bc1d220)

8. Startup configuration for NetBox

Copy the systemd files to the respective directory.

sudo cp -v /opt/netbox/contrib/*.service /etc/systemd/system/

sudo systemctl daemon-reload

Restart and check the NetBox services.

sudo systemctl start netbox

sudo systemctl start netbox-rq

sudo systemctl enable netbox

sudo systemctl enable netbox-rq

sudo systemctl status netbox netbox-rq

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/15a4ac5b-0ba8-4b41-a5a7-fcd55ed4db32)

9. Configure the HTTP service

sudo apt install -y apache2

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d16fa115-81af-434c-97d2-951c5fff800b)

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/9b38c500-54bc-453b-9b21-751ecd5ca629)

To avoid the complexity we will use the default configuration file. But make sure you modify the ServerName portion, and put # before the SSL configuration lines and change the default port from 443 to 80 , as we are not using HTTPS in this LAB.

sudo cp /opt/netbox/contrib/apache.conf /etc/apache2/sites-available/netbox.conf

sudo nano /etc/apache2/sites-available/netbox.conf

Este sería el código completo del fichero:

<VirtualHost *:80>
        ProxyPreserveHost On
        ServerName localhost

        # SSLEngine on
        # SSLCertificateFile /etc/ssl/certs/netbox.crt
        # SSLCertificateKeyFile /etc/ssl/private/netbox.key

        Alias /static /opt/netbox/netbox/static

        <Directory /opt/netbox/netbox/static>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Require all granted
        </Directory>

        <Location /static>
                ProxyPass !
        </Location>

        RequestHeader set "X-Forwarded-Proto" expr=%{REQUEST_SCHEME}
        ProxyPass / http://127.0.0.1:8001/
        ProxyPassReverse / http://127.0.0.1:8001/
 </VirtualHost>
 
![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/764cdab8-c057-4444-9b8b-faede9f9226b)

Enable the netbox site, and restart the apache service.
$ sudo a2enmod ssl proxy proxy_http headers
$ sudo a2ensite netbox
$ sudo systemctl restart apache2

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/92be2b8b-a17c-4732-982c-6fdb2dafa1cb)




