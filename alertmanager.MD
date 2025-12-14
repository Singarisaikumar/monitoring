 # alert manager configuration

# run with sudo access

```
cd /opt
```
```
wget https://github.com/prometheus/alertmanager/releases/download/v0.30.0-rc.0/alertmanager-0.30.0-rc.0.linux-amd64.tar.gz
```
# Untar file

```
tar -xf alertmanager-0.30.0-rc.0.linux-amd64.tar.gz
```
# rename the folder (optional but easy to use)

```
mv alertmanager-0.30.0-rc.0.linux-amd64 alertmanager
```
# create systemctl folder

```
vim /etc/systemd/system/alertmanager.service
```
# alertmanager systemctl service

```
[Unit]
Description=Alertmanager
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
WorkingDirectory=/opt/alertmanager/
ExecStart=/opt/alertmanager/alertmanager --config.file=/opt/alertmanager/alertmanager.yml

[Install]
WantedBy=multi-user.target
```
# daemon reload

```
systemctl daemon-reload
```
# start service

```
systemctl start alertmanager
```
# status of service 

```
systemctl status alertmanager 
```
# enable service

```
systemctl enable alertmanager
```