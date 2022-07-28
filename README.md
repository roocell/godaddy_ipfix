# fix IP address for domain on godaddy.
if your ISP gives you a new IP address when your router reboots,
this will automatically update the DNS on godaddy so your domain works again.

# set up service
```
sudo vi /etc/systemd/system/ipfix.service
[Unit]
Description=ipfix
After=network-online.target
[Service]
ExecStart=/home/pi/godaddy_ipfix/godaddy_ddns.py %/home/pi/godaddy_ipfix/roocell_ddns.config
[Install]
WantedBy=multi-user.target
```
# add shebang to app.py (#!/usr/bin/python3)
```
chmod +x ~/godaddy_ipfix/godaddy_ddns.py
```
# start
```
sudo systemctl daemon-reload
sudo systemctl enable ipfix
sudo systemctl restart ipfix
sudo systemctl status ipfix.service
```
