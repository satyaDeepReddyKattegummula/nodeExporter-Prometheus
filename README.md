# Monitoring your Mac with Prometheus
Simple node-exporter Prometheus setup for Monitoring your Macbook  

**What is Prometheus?**

Prometheus is an open-source monitoring and alerting toolkit designed for collecting and storing metrics from various sources. It is widely adopted, particularly for monitoring Kubernetes platforms, due to its powerful data model and query language.

One of the key components of the Prometheus ecosystem is the node exporter. The node exporter is a lightweight agent that runs on target systems (such as servers or containers) and collects operating system-level metrics. These metrics include CPU usage, memory utilization, disk I/O, network traffic, and other system-level data.

The node exporter exposes these metrics through a standard /metrics endpoint, which follows the Prometheus exposition format. Prometheus, acting as the central monitoring server, can then "scrape" or retrieve the metrics data from this endpoint at regular intervals, storing it in its time-series database.

By leveraging the node exporter, Prometheus gains visibility into the underlying infrastructure, enabling comprehensive monitoring and alerting capabilities. This integration allows Prometheus to collect and analyze system-level metrics alongside application-level metrics, providing a unified view of the entire monitoring landscape.

**STEP 1**

Install and run Node Exporter 
To download the macOS version of the Prometheus node exporter, follow these steps:

1. Visit the Prometheus downloads page (https://prometheus.io/download/).
2. Locate the section for the node exporter and find the download link for the macOS version, which is labeled as "darwin."
3. Copy the download URL for the desired version of the node exporter.
4. Open a terminal on your macOS system.
5. Use the curl command to download the node exporter binary, replacing <node_exporter_download_url> with the actual download URL you copied in.

example: **$ curl -LO https://example.com/downloads/node_exporter-1.5.0.darwin-amd64.tar.gz**

Unzip the tar file
**$ gunzip -c node_exporter-1.4.0.darwin-amd64.tar.gz| tar xopf -**

To Run The Node Exporter

**$ cd node_exporter-1.4.0.darwin-amd6
$ ./node_exporter**

You can check that it's running by opening a browser at **http://127.0.0.1:9100/metrics**

**STEP 2**

You can use the same approch to download the Prometheus for Mac as of Node Exporter as we did in step 1.

**$ curl -O 'https://github.com/prometheus/prometheus/releases/download/v2.40.1/prometheus-2.40.1.darwin-amd64.tar.gz' -L**

Unzip the file
**$ gunzip -c prometheus-2.40.1.darwin-amd64.tar.gz| tar xopf -**

Before to running Prometheus, you need to configure it to collect metrics from your node exporter.
This process involves adding the node exporter's /metrics endpoint as a "scrape target" in Prometheus's configuration file. 
By specifying the /metrics endpoint as a scrape target, you instruct Prometheus to periodically "scrape" or retrieve all the metrics exposed by the node exporter at that endpoint.

Open **prometheus.yml** file and under scrape_configs modify with below lines:

![Screenshot 2024-06-15 at 8 36 48 PM](https://github.com/satyaDeepReddyKattegummula/nodeExporter-Prometheus/assets/100654557/b0b5c5d2-4b8a-4f33-9073-eaf72a6cce9c)


Ones changes are made save the file and run **$  ./prometheus**

Once Prometheus is running you can view the Prometheus UI from **http://127.0.0.1:9090 **

Go to Status > Targets You can see your node exporter endpoints
![Screenshot 2024-06-15 at 8 40 00 PM](https://github.com/satyaDeepReddyKattegummula/nodeExporter-Prometheus/assets/100654557/b9a02123-f840-4154-b2ea-1059cb9603be)

![Screenshot 2024-06-15 at 8 39 37 PM](https://github.com/satyaDeepReddyKattegummula/nodeExporter-Prometheus/assets/100654557/8f54dfe9-f272-4ecf-a842-f955bfde35c2)
