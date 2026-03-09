# Network Measurement Lab: RTT and Distance Analysis

This project analyzes the relationship between geographic distance and network latency (Round Trip Time) across various servers worldwide. It uses ICMP packets to measure RTT from a local machine in Taipei, Taiwan, to a distributed set of target servers.

## Project Overview

The core objective of this repository is to:

* Identify the local machine's geographic coordinates.
* Ping multiple servers across different countries and continents.
* Calculate the geographic distance between the source and each destination.
* Analyze and visualize the correlation between physical distance (km) and network RTT (ms).

## Repository Structure

* `NML_Assignment_1.ipynb`: The main Jupyter Notebook containing the Python implementation for IP geolocation, network measurement using `scapy`, data processing with `pandas`, and visualization.
* `servers.csv`: A list of target hostnames and their corresponding countries used for testing.
* `results.csv`: The output data file containing hostnames, distances in kilometers, and average RTT in milliseconds.

## Key Features

* **IP Geolocation**: Automatically detects the local IP and retrieves latitude/longitude coordinates for distance calculation.
* **Automated Ping Suite**: Uses the `scapy` library to send ICMP requests and measure RTT for a predefined list of global servers.
* **Distance Correlation**: Employs `geopy` to calculate the great-circle distance between the user and targets.
* **Data Visualization**: Includes plots to visualize the distribution of server locations and the relationship between distance and latency.

## Prerequisites

To run the analysis, you will need the following Python libraries:

* `scapy`: For network packet manipulation and ICMP measurement.
* `geopy`: For calculating geographic distances.
* `pandas` & `numpy`: For data analysis.
* `matplotlib`: For generating plots.
* `urllib` & `json`: For interacting with geolocation APIs.

## Analysis Results

The collected results (available in `results.csv`) demonstrate typical network behaviors, where closer regional servers (e.g., in Taiwan or Japan) show significantly lower RTT compared to transcontinental connections (e.g., Chile or Sweden).

| Country | Hostname | Distance (km) | Avg RTT (ms) |
| --- | --- | --- | --- |
| Taiwan | mirror.twds.com.tw | ~25 | ~3.67 |
| Japan | kantei.go.jp | ~12,667 | ~3.65* |
| Chile | nic.cl | ~18,512 | ~260.91 |
| Italy | garr.it | ~9,628 | ~210.94 |

**Note: Some RTT values may be influenced by specific routing or CDN acceleration.*