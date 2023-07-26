Steps

If your NetBox installation uses virtualenv, activate it like this:

source /opt/netbox/venv/bin/activate

Install the plugin.

To ensure plugin is automatically re-installed during future NetBox upgrades, create a file named local_requirements.txt (if not already existing) in the NetBox root directory and list the nextbox-plugin-device-map package:

Option A: if you want to install it from PyPI:

echo netbox-plugin-device-map | sudo tee -a /opt/netbox/local_requirements.txt

Option B: if you manually downloaded the plugin distribution from releases:

wget https://github.com/drygdryg/netbox-plugin-device-map/releases/download/v0.1.3/netbox-plugin-device-map-0.1.3.tar.gz

echo "/path/to/netbox-plugin-device-map-0.1.3.tar.gz" | sudo tee -a /opt/netbox/local_requirements.txt

Then run:

sudo pip3 install -U -r /opt/netbox/local_requirements.txt

to install the plugin.

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/afc71826-df6c-4a40-9e30-c40d50d61921)

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d637a9bf-679b-47ea-ab46-6d6b4bb1a962)

Collect static files:

sudo python3 /opt/netbox/netbox/manage.py collectstatic

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d2e92de4-bf65-42cf-8509-a211e2ed3754)

To enable plugin, add the plugin's name to the PLUGINS list in configuration.py (it's usually located in /opt/netbox/netbox/netbox/) like so:

PLUGINS = [
    'netbox_device_map'
]

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a284eb01-7721-420c-bddd-4275e29cead3)

Restart NetBox WSGI service to apply changes:

sudo systemctl restart netbox
