# virtualmeter

This script can be used to replace the standard external power meter for the Soyo Source brand inverter 
allowing more flexibility and features than the original. 

It allows the user to control the Soyo Source inverter power output using either an MQTT or JSON data source. The script supports multiple inverters and allows a maximum output amount (to prevent excessive load on batteries, for example). Features could be extended to allow time of day, or state of charge changes depending on users requirements.

This software is provided for free with ABSOLUTELY NO GUARANTEE. Misuse or untested use could result in very bad things happening.

Please conduct your own testing before deployment.

This script was based on original code written by MasterTH out of a discussion on the following forum post:

https://secondlifestorage.com/showthread.php?tid=7631

Please join the thread if you need further support.

INSTALLATION:

There are two python scripts in this repo and a service file to allow the script to be run as a system service.

The difference between the two python scripts is due to the system logging commands, there's no print commands in the service, as information is sent to the journal instead of stdout.

To run locally:
Edit and then move the script to a location of choice and run it: sudo python3 virtualmeter.local.py. You might need to install some dependancies.

To run as system service:
Edit the virtualmeter.service.py script and move it to a location of choice. 
Update the location reference in virtualmeter.service file and move it to /etc/systemd/system/

You can then use a tool like webmin to start the script or you can start it manually with:
sudo systemctl enable virtualmeter.service
sudo systemctl start virtualmeter.service
sudo systemctl status virtualmeter.service

View running state of the service with: journalctl -b -n 50 -u virtualmeter.service




