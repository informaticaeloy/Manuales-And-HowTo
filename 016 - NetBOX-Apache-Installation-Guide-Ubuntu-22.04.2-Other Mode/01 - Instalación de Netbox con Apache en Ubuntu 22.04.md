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

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2adc24b6-d3db-4124-95ab-3024c14ff373)
