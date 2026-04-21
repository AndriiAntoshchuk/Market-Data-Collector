# Coinbase Level 2 Data Collector

A simple Python collector for raw Coinbase Exchange Level 2 market data.

The script connects to the Coinbase WebSocket feed, subscribes to the `level2_batch` channel for `ETH-USD`, and stores every received message as raw JSONL for later replay and order-book reconstruction.

## What this project does

- connects to the Coinbase public WebSocket feed
- subscribes to `ETH-USD` Level 2 batched updates
- stores every received message with a local UTC timestamp
- writes data into daily folders
- rotates files when the UTC date changes
- renames files so the filename reflects the session time range

## Output format

The collector writes newline-delimited JSON (`.jsonl`) files into:

```text
data/raw/YYYY-MM-DD/