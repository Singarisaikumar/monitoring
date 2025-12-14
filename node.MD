
# Node configuration

# run with sudo access

```
cd /opt
```
```
wget https://github.com/prometheus/node_exporter/releases/download/v1.10.2/node_exporter-1.10.2.linux-amd64.tar.gz
```
# Untar file

```
tar -xf node_exporter-1.10.2.linux-amd64.tar.gz
```
# rename the folder (optional but easy to use)

```
mv node_exporter-1.10.2.linux node_exporter
```
# create systemctl folder

```
vim /etc/systemd/system/node_exporter.service
```
# node_exporter systemctl service

```
[Unit]
Description=Node Exporter
After=network-online.target

[Service]
Restart=on-failure
ExecStart=/opt/node_exporter/node_exporter

[Install]
WantedBy=multi-user.target
```
# daemon reload

```
systemctl daemon-reload
```
# start service

```
systemctl start node_exporter
```
# status of service 

```
systemctl status node_exporter 
```
# enable service

```
systemctl enable node_exporter
```
# connecting with prometheus with node ,perform this prometheus server (not in node)

# open prometheus.yml in prometheus server

```
vim prometheus.yml
```
# update the below configuration the prometheus.yml file 
# Replace with your ip address while updating 

```
# my global config
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - localhost:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  - "alert-rules/*.yaml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "prometheus"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
      - targets: ["localhost:9090"]
        labels:
          name: prometheus

  - job_name: "nodes"
    static_configs:
      - targets: ["172.31.3.75:9100"]
        labels:
          name: node
```
# daemon reolad

```
systemctl daemon-reload
```