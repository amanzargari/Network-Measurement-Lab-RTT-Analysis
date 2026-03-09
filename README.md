# Network Measurement Lab — RTT Analysis

First assignment of the Network Measurement Lab.

## Goal

Measure the **Round Trip Time (RTT)** to a set of selected servers by sending
**ICMP Echo Request** packets (the same protocol used by the Unix `ping`
utility) and recording the time until the corresponding **ICMP Echo Reply** is
received.

## Contents

| File | Description |
|------|-------------|
| `RTT_Analysis.ipynb` | Main Jupyter / Google Colab notebook |

## What the notebook does

1. **Implements ICMP ping in pure Python** using raw sockets and the packet
   structure defined in RFC 792 (type, code, checksum, identifier, sequence).
2. **Probes a configurable list of servers** — by default:
   `google.com`, `cloudflare.com`, `amazon.com`, `github.com`, `microsoft.com`.
3. **Computes summary statistics** per server:
   minimum, maximum, mean, standard deviation, median RTT, and packet-loss %.
4. **Visualises the results** with four plots:
   - Line plot of RTT per probe (with packet-loss markers)
   - Box plot of RTT distribution
   - Empirical CDF of RTT
   - Mean RTT bar chart with standard-deviation error bars
   - Packet-loss bar chart

## How to run

### Google Colab (recommended)

1. Open [Google Colab](https://colab.research.google.com/).
2. Choose **File → Upload notebook** and upload `RTT_Analysis.ipynb`.
3. Run all cells (**Runtime → Run all**).  
   Colab already runs as `root`, so raw sockets work without any extra setup.

### Local Jupyter

Raw sockets require root privileges on most operating systems.

```bash
sudo pip install jupyter matplotlib numpy
sudo jupyter notebook RTT_Analysis.ipynb
```

Then run all cells.

## Configuration

Edit the **Configuration** cell in the notebook to customise:

```python
TARGET_SERVERS = ['google.com', 'cloudflare.com', ...]  # servers to probe
NUM_PROBES     = 20   # ICMP echo requests per server
PROBE_DELAY    = 0.5  # seconds between consecutive probes
TIMEOUT        = 2    # seconds to wait for each reply
```

## Requirements

- Python 3.10+
- `matplotlib`
- `numpy`
- Root / administrator privileges (for raw ICMP sockets)
