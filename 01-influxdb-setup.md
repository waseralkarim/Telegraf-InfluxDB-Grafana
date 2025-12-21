# InfluxDB

InfluxDB is a time series database (TSDB) developed by the company InfluxData. It is used for storage and retrieval of time series data in fields such as operations monitoring, application metrics, Internet of Things sensor data, and real-time analytics. It also has support for processing data from Graphite.

### Influxdb V1 Setup

### Ubuntu/Debian:

```bash
# Add the InfluxData repository
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/lsb-release
echo "deb https://repos.influxdata.com/ubuntu ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list

# Update and install
sudo apt update
sudo apt install influxdb

# Start and Enable the Service
sudo systemctl enable influxdb
sudo systemctl start influxdb
```
