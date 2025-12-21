# Telegraf

Telegraf, a server-based agent, collects and sends metrics and events from databases, systems, and IoT sensors. Written in Go, Telegraf compiles into a single binary with no external dependencies–requiring very minimal memory.

### [**Install from the InfluxData repository**](https://docs.influxdata.com/telegraf/v1/install/#install-from-the-influxdata-repository)

Run the following commands using `apt-get` to install Telegraf from the InfluxData repository:

[**Ubuntu 20.04 LTS and newer**](https://docs.influxdata.com/telegraf/v1/install/#) [**Older than Ubuntu 20.04**](https://docs.influxdata.com/telegraf/v1/install/#)

```jsx
curl --silent --location -O https://repos.influxdata.com/influxdata-archive.key
gpg --show-keys --with-fingerprint --with-colons ./influxdata-archive.key 2>&1 **\**
| grep -q '^fpr:\+24C975CBA61A024EE1B631787C3D57159FC2F927:$' **\**
&& cat influxdata-archive.key **\**
| gpg --dearmor **\**
| sudo tee /etc/apt/keyrings/influxdata-archive.gpg > /dev/null **\**
&& echo 'deb [signed-by=/etc/apt/keyrings/influxdata-archive.gpg] https://repos.influxdata.com/debian stable main' **\**
| sudo tee /etc/apt/sources.list.d/influxdata.list
sudo apt-get update && sudo apt-get install telegraf
```
Now edit Telegraf config: ```sudo vim /etc/telegraf/telegraf.conf```

[global_tags]
  dc = ""
  rack = ""

[agent]
  interval = "3s"
  round_interval = true
  metric_batch_size = 1000
  metric_buffer_limit = 10000
  collection_jitter = "0s"
  flush_interval = "10s"
  flush_jitter = "0s"
  precision = ""
  debug = false
  quiet = false
  logfile = ""
  omit_hostname = false

[[outputs.influxdb]]
  urls = ["http://monitor.osl.team:8086"]
  database = "devops-portal"  
  timeout = "5s"

[[inputs.cpu]]
  percpu = true
  totalcpu = true
  collect_cpu_time = false
  report_active = false

[[inputs.disk]]
  ignore_fs = ["tmpfs", "devtmpfs", "devfs", "iso9660", "overlay", "aufs", "squashfs"]
  
[[inputs.diskio]]

[[inputs.kernel]]
  
[[inputs.mem]]

[[inputs.processes]]

[[inputs.netstat]]

[[inputs.net]]

[[inputs.swap]]

[[inputs.system]]

