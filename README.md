# **Telegraf-InfluxDB-Grafana Monitoring Stack**

A complete open-source observability stack for collecting, storing and visualizing time series metrics using **Telegraf**, **InfluxDB**, and **Grafana** (the TIG stack). This repository provides setup guides, configuration files, and step-by-step instructions to bring up the stack for system and metric monitoring.

## Overview

The **TIG stack** combines three powerful open-source tools:

- **Telegraf** – Flexible agent to collect metrics from systems, services, and containers. [GitHub](https://github.com/odennav/grafana-telegraf-metrics-monitoring-system?utm_source=chatgpt.com)
- **InfluxDB** – Time series database optimized for storing metrics and events. [Medium](https://medium.com/%40linnyk.oleh/telegraf-influx-grafana-stack-7ce905f68e09?utm_source=chatgpt.com)
- **Grafana** – Dashboarding and visualization platform to graph and explore metrics. [Wikipedia](https://en.wikipedia.org/wiki/Grafana?utm_source=chatgpt.com)

This stack allows you to monitor CPU, memory, disk, network and custom application metrics in real time.

---

## Repository Structure

```
.
├── 01-influxdb-setup.md        # Guide to provisioning and configuring InfluxDB
├── 02-telegraf-setup.md        # Guide to configuring Telegraf agent
├── 03-grafana-setup.md         # Guide for Grafana setup and dashboards
├── telegraf.conf               # Production-Grade Telegraf configuration file
├── LICENSE                     # MIT License
└── README.md                   # This file

```
