# **Telegraf-InfluxDB-Grafana Monitoring Stack**

<img width="1919" height="915" alt="Screenshot 2025-12-25 154639" src="https://github.com/user-attachments/assets/c873b3e6-669d-440f-9747-06755fdb13e0" />

<img width="1907" height="904" alt="Screenshot 2025-12-25 154707" src="https://github.com/user-attachments/assets/4f9f576c-c402-42eb-9071-574f5f97c9bf" />


A complete open-source observability stack for collecting, storing and visualizing time series metrics using **Telegraf**, **InfluxDB**, and **Grafana** (the TIG stack). This repository provides setup guides, configuration files, and step-by-step instructions to bring up the stack for system and metric monitoring.

## Overview

The **TIG stack** combines three powerful open-source tools:

- **Telegraf** – Flexible agent to collect metrics from systems, services, and containers. [Telegraf](https://docs.influxdata.com/telegraf/v1)
- **InfluxDB** – Time series database optimized for storing metrics and events. [Influx](https://www.influxdata.com/)
- **Grafana** – Dashboarding and visualization platform to graph and explore metrics. [Grafana](https://grafana.com/docs/)

This stack allows you to monitor CPU, memory, disk, network and custom application metrics in real time.

## Repository Structure

The monitoring stack setup is organized into the following documents:

1. **[InfluxDB Setup](01-influxdb-setup.md)**  
   Installing and configuring InfluxDB for time-series data storage

2. **[Telegraf Setup](02-telegraf-setup.md)**  
   Installing Telegraf and configuring system metric collection

3. **[Grafana Setup](03-grafana-setup.md)**  
   Installing Grafana and connecting it to InfluxDB

4. **[Grafana Panel Queries](04-panel-queries.md)**  
   Importing and managing Grafana dashboards

5. **[Telegraf Configuration](telegraf.conf)**  
   Input, output and plugin configuration example

6. **[Ansible Automation](ansible)**  
   Automated installation and configuration using Ansible

7. **[Grafana Templates](grafana-template/Telegraf-Influx-Dashboard.json)**  
   Reusable Grafana JSON dashboard templates

