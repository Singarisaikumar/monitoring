# Prometheus configuration
run with sudo access

```
wget https://github.com/prometheus/prometheus/releases/download/v3.8.0/prometheus-3.8.0.linux-amd64.tar.gz
```

# Untar file

```
tar -xf prometheus-3.8.0.linux-amd64.tar.gz
```
# create systemctl folder

```
vim /etc/systemd/system/prometheus.service
```
# prometheus systemctl service

```
[Unit]
Description=Prometheus Server
Documentation=https://prometheus.io/docs/introduction/overview/
After=network-online.target

[Service]
Restart=on-failure
ExecStart=/opt/prometheus/prometheus --config.file=/opt/prometheus/prometheus.yml

[Install]
WantedBy=multi-user.target
```
# start service

```
systemctl start prometheus
```
# status of service 

```
systemctl status prometheus 
``