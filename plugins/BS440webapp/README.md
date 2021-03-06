# Description
* BS440 plugin BS440plot.py
	Generate charts from CSV file to HTML file whenever BS440flask.py requires it
* BS440 plugin BS440flask.py
	Run a web server at [local_machine_IP]:[port] where port is 5440 by default.
	Provide access from local network to charts generated by BS440plot.py 
	Execute the following command to find out [local_machine_IP] if you're unsure:
		/sbin/ifconfig eth0 | grep 'inet ad' | cut -d: -f2 | awk '{ print $1}'

# Requirements
* BS440 plugin BS440csv.py

# Dependencies:
* pandas
		sudo apt-get install python-pandas
* plotly
		sudo -H pip install --upgrade plotly
* flask
		sudo -H pip install flask

# Tested on
* Intel NUC5i3RYB operating x86_64 Ubuntu 16.04.2 LTS
* Raspberry Pi 3 Model B operating armv7l Raspbian GNU/Linux 8 (jessie)

# Preferences
Before using this app, personalize your settings in the file _BS440webapp.ini_.

# Setup
* Make the web app run in background at boot
	Open /etc/rc.local
		sudo nano /etc/rc.local
	Add the following line before 'exit 0' (replace <user> and /path/to/BS440)
		su -l <user> -c "/path/to/BS440/plugins/BS440webapp/BS440webapp.sh >/dev/null 2>&1 &"

	Mark scripts as executables
		sudo chmod 764 /path/to/BS440/plugins/BS440webapp/BS440flask.py
		sudo chmod 764 /path/to/BS440/plugins/BS440webapp/BS440webapp.sh

* Firewall
	You may need to open a port through your firewall to get access to the web app from your local network. 
	With default port 5440 and UFW firewall, you can use the following command:
		sudo ufw allow 5440

# Disclaimer
This software is build out of personal interest and not related to 
Medisana AG in any way.
