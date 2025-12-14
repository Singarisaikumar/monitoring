## grafana installation

```
sudo yum install -y https://dl.grafana.com/grafana/release/12.3.0/grafana_12.3.0_19497075765_linux_amd64.rpm
```
# daemon reoload

```
systemctl daemon-reload
```
# start service

```
systemctl start grafana-server
```
# status of service 

```
systemctl status grafana-server 
```

# login using saime public ip  if prometheus and grafana is installed in same server 
# first time only create new password
```
username: admin
password: admin 
----