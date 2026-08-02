===============================================================================
                           01 - PROMETHEUS BASICS
===============================================================================

Author      : Anurag
Technology  : Prometheus
Level       : Linux Engineer / DevOps
Purpose     : Interview + Production Revision

===============================================================================
WHAT IS PROMETHEUS?
===============================================================================

Prometheus is an Open Source Monitoring and Alerting Toolkit.

- Developed by SoundCloud.
- Now maintained under CNCF (Cloud Native Computing Foundation).
- Collects metrics from servers.
- Stores metrics in Time Series Database (TSDB).
- Supports Alerting using Alert Rules.
- Uses PromQL for querying metrics.

===============================================================================
WHY PROMETHEUS?
===============================================================================

Traditional monitoring only tells whether server is UP or DOWN.

Prometheus provides:

- CPU Usage
- Memory Usage
- Disk Usage
- Filesystem Usage
- Network Traffic
- Load Average
- Processes
- Docker Metrics
- Kubernetes Metrics
- Application Metrics

===============================================================================
PROMETHEUS ARCHITECTURE
===============================================================================

                     +----------------------+
                     |   Linux Server       |
                     |   Node Exporter      |
                     +----------+-----------+
                                |
                           HTTP :9100
                                |
                                |
                     +----------v-----------+
                     |    Prometheus        |
                     |       :9090          |
                     +----------+-----------+
                                |
                         Alert Rules
                                |
                     +----------v-----------+
                     |   Alertmanager       |
                     |       :9093          |
                     +----------+-----------+
                                |
                 Email / Slack / Teams / PagerDuty
                                |
                     +----------v-----------+
                     |      Grafana         |
                     |        :3000         |
                     +----------------------+

===============================================================================
MAIN COMPONENTS
===============================================================================

1. Node Exporter
----------------

Purpose:
- Collect Linux Metrics
- Reads data from /proc and /sys
- Exposes metrics on HTTP

Default Port:

9100

Metrics:

- CPU
- Memory
- Disk
- Filesystem
- Load Average
- Network
- Uptime
- Processes

===============================================================================

2. Prometheus
-------------

Purpose:

- Scrape Metrics
- Store Metrics
- Execute PromQL
- Evaluate Alert Rules

Default Port:

9090

===============================================================================

3. Alertmanager
---------------

Purpose:

- Receive Alerts
- Group Alerts
- Silence Alerts
- Route Alerts
- Send Email
- Send Slack
- Send Teams
- PagerDuty

Default Port:

9093

===============================================================================

4. Grafana
----------

Purpose:

- Dashboards
- Visualization
- Charts
- Reports

Default Port:

3000

===============================================================================
PROMETHEUS DATA FLOW
===============================================================================

Linux Server

↓

Node Exporter

↓

Prometheus Scrapes Metrics

↓

Time Series Database

↓

PromQL Query

↓

Alert Rule

↓

Pending

↓

Firing

↓

Alertmanager

↓

Email / Slack / Teams

↓

Linux Team

===============================================================================
PULL MODEL
===============================================================================

Prometheus uses Pull Model.

Prometheus itself connects to target servers.

Example

Prometheus

↓

GET http://192.168.198.172:9100/metrics

Unlike Push Model where client sends data.

Interview Question:

Q. Prometheus Push karta hai ya Pull?

Answer:

Pull

===============================================================================
TIME SERIES DATABASE (TSDB)
===============================================================================

Prometheus stores

Metric Name

+

Timestamp

+

Value

Example

Metric

node_cpu_seconds_total

Timestamp

2026-08-02 12:30:15

Value

12345.98

===============================================================================
EXPORTERS
===============================================================================

Linux

Node Exporter

--------------------------------

MySQL

mysqld_exporter

--------------------------------

PostgreSQL

postgres_exporter

--------------------------------

Nginx

nginx_exporter

--------------------------------

Apache

apache_exporter

--------------------------------

Docker

cadvisor

--------------------------------

Kubernetes

kube-state-metrics

===============================================================================
IMPORTANT METRICS
===============================================================================

CPU

node_cpu_seconds_total

--------------------------------

Memory

node_memory_MemAvailable_bytes

node_memory_MemTotal_bytes

--------------------------------

Filesystem

node_filesystem_size_bytes

node_filesystem_avail_bytes

--------------------------------

Network

node_network_receive_bytes_total

node_network_transmit_bytes_total

--------------------------------

Load

node_load1

node_load5

node_load15

--------------------------------

Processes

node_procs_running

===============================================================================
DIRECTORY STRUCTURE
===============================================================================

Prometheus

/etc/prometheus/

prometheus.yml

rules/

--------------------------------

Alertmanager

/etc/alertmanager/

alertmanager.yml

--------------------------------

Grafana

/etc/grafana/

grafana.ini

===============================================================================
DEFAULT PORTS
===============================================================================

Prometheus

9090

--------------------------------

Node Exporter

9100

--------------------------------

Alertmanager

9093

--------------------------------

Grafana

3000

===============================================================================
REAL PRODUCTION FLOW
===============================================================================

Linux Server

↓

Node Exporter

↓

Prometheus

↓

Alert Rule

↓

CPU > 80%

↓

Pending

↓

Firing

↓

Alertmanager

↓

Email

↓

Linux Team

↓

Issue Fixed

===============================================================================
PROMETHEUS FEATURES
===============================================================================

✔ Pull Based Monitoring

✔ Time Series Database

✔ PromQL

✔ Alert Rules

✔ Alertmanager Integration

✔ Grafana Integration

✔ Kubernetes Support

✔ Docker Monitoring

✔ Service Discovery

===============================================================================
ADVANTAGES
===============================================================================

- Open Source

- Easy Installation

- Fast Queries

- Powerful Alerting

- Kubernetes Native

- Highly Scalable

- Multi Exporter Support

===============================================================================
LIMITATIONS
===============================================================================

- No Long-Term Log Storage

- Metrics Only

- Logs require ELK/Loki

- Single Node TSDB by default

===============================================================================
INTERVIEW QUESTIONS
===============================================================================

Q1. What is Prometheus?

Open Source Monitoring and Alerting Toolkit.

------------------------------------------------

Q2. Who developed Prometheus?

SoundCloud

------------------------------------------------

Q3. Maintained by?

CNCF

------------------------------------------------

Q4. Database used?

Time Series Database (TSDB)

------------------------------------------------

Q5. Default Port?

9090

------------------------------------------------

Q6. Node Exporter Port?

9100

------------------------------------------------

Q7. Alertmanager Port?

9093

------------------------------------------------

Q8. Grafana Port?

3000

------------------------------------------------

Q9. Prometheus Push or Pull?

Pull

------------------------------------------------

Q10. Prometheus stores what?

Metric

Timestamp

Value

------------------------------------------------

Q11. Which language is used to query metrics?

PromQL

------------------------------------------------

Q12. Does Grafana store metrics?

No

Grafana only visualizes metrics.

Prometheus stores metrics.

------------------------------------------------

Q13. What is Node Exporter?

Exporter that exposes Linux system metrics.

------------------------------------------------

Q14. What is Alertmanager?

Component responsible for sending notifications.

------------------------------------------------

Q15. Difference between Grafana and Prometheus?

Prometheus

Collects + Stores Metrics

Grafana

Visualizes Metrics

===============================================================================
5 MINUTE QUICK REVISION
===============================================================================

Prometheus

↓

Pull Based Monitoring

↓

Node Exporter

↓

Metrics

↓

TSDB

↓

PromQL

↓

Alert Rules

↓

Alertmanager

↓

Email

↓

Grafana Dashboard

Ports

9090 -> Prometheus

9100 -> Node Exporter

9093 -> Alertmanager

3000 -> Grafana

Remember

Prometheus = Collect + Store

Node Exporter = Expose Linux Metrics

Alertmanager = Send Alerts

Grafana = Dashboard

===============================================================================
END OF FILE
===============================================================================
