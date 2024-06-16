# Monitoring your Mac with Prometheus
Simple node-exporter Prometheus setup for Monitoring your Macbook  

**What is Prometheus?**

Prometheus is an open-source monitoring and alerting toolkit designed for collecting and storing metrics from various sources. It is widely adopted, particularly for monitoring Kubernetes platforms, due to its powerful data model and query language.
One of the key components of the Prometheus ecosystem is the node exporter. The node exporter is a lightweight agent that runs on target systems (such as servers or containers) and collects operating system-level metrics. These metrics include CPU usage, memory utilization, disk I/O, network traffic, and other system-level data.
The node exporter exposes these metrics through a standard /metrics endpoint, which follows the Prometheus exposition format. Prometheus, acting as the central monitoring server, can then "scrape" or retrieve the metrics data from this endpoint at regular intervals, storing it in its time-series database.
By leveraging the node exporter, Prometheus gains visibility into the underlying infrastructure, enabling comprehensive monitoring and alerting capabilities. This integration allows Prometheus to collect and analyze system-level metrics alongside application-level metrics, providing a unified view of the entire monitoring landscape.
