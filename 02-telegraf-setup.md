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
