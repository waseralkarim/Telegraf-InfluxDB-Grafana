# Grafana Panel Queries (Telegraf + InfluxDB)

<img width="1919" height="915" alt="image" src="https://github.com/user-attachments/assets/f269c440-7c6c-4050-8b81-a29826749b8e" />

**Datasource:** InfluxDB

**Host:** `telegraf-server-2`

**Retention policy:** `default`

---

## Memory – Used & Available (Stat Panel)

### Used Memory

```sql
SELECTlast("used")
FROM "mem"
WHERE "host"='telegraf-server-2'
AND $timeFilter

```

### Available Memory

```sql
SELECTlast("available")
FROM "mem"
WHERE "host"='telegraf-server-2'
AND $timeFilter

```

## Disk Usage – Root (`/`) (Pie Chart)

```sql
SELECT
  mean("free")AS "Free",
  mean("used")AS "Used"
FROM "disk"
WHERE "host"='telegraf-server-2'
AND "path"='/'
AND $timeFilter
GROUPBYtime($__interval)
FILL(null)

```

---

## CPU Usage Over Time (Timeseries)

> Telegraf reports usage_idle, converted to usage %
> 

```sql
SELECT
100- mean("usage_idle")AS "CPU Usage"
FROM "cpu"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime($__interval)
```

---

## Current CPU Usage (Gauge)

```sql
SELECTlast(100- "usage_idle")AS "CPU Usage"
FROM "cpu"
WHERE "host"='telegraf-server-2'
AND $timeFilter

```

---

## Network Traffic – Current (Stat Panel)

### Incoming (bps)

```sql
SELECT non_negative_derivative(mean("bytes_recv"),1s)*8AS "IN"
FROM "net"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime($__interval)
FILL(null)
```

### Outgoing (bps)

```sql
SELECT non_negative_derivative(mean("bytes_sent"),1s)*8AS "OUT"
FROM "net"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime($__interval)
FILL(null)
```

---

## Network Traffic – History (Timeseries)

```sql
SELECT
  non_negative_derivative(mean("bytes_recv"),1s)*8AS "IN",
  non_negative_derivative(mean("bytes_sent"),1s)*8AS "OUT"
FROM "net"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime($__interval)
FILL(null)
```

---

## Open TCP Connections (Timeseries)

```sql
SELECT mean("tcp_established")AS "Ports"
FROM "netstat"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime(10s), "host"
FILL(null)

```

---

## Current Open TCP Connections (Stat)

```sql
SELECTlast("tcp_established")AS "Open Ports"
FROM "netstat"
WHERE "host"='telegraf-server-2'
AND $timeFilter
```

---

## Disk Read / Write Throughput (Bytes/sec)

### Disk Read

```sql
SELECT non_negative_derivative(mean("read_bytes"),10s)AS "Disk Read"
FROM "diskio"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime(10s)
FILL(null)
```

### Disk Write

```sql
SELECT non_negative_derivative(mean("write_bytes"),10s)AS "Disk Write"
FROM "diskio"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime(10s)
FILL(null)

```

---

## Disk IOPS – Read / Write

### IOPS Read

```sql
SELECT non_negative_derivative(mean("reads"),10s)AS "Disk IOPS Read"
FROM "diskio"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime(10s)
FILL(null)
```

### IOPS Write

```sql
SELECT non_negative_derivative(mean("writes"),10s)AS "Disk IOPS Write"
FROM "diskio"
WHERE "host"='telegraf-server-2'
AND $timeFilter
GROUPBYtime(10s)
FILL(null)
```
