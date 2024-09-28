# Suricata IDS Project

## Date: 2024-09-28

### Overview
This project involves setting up Suricata as an Intrusion Detection System on a Raspberry Pi to monitor network traffic.

### Tools Used
- Raspberry Pi OS
- Suricata

### Setup Steps
1. Installed Suricata.
2. Configured Suricata to monitor traffic on the network interface.
3. Started Suricata with the command:
   ```bash
   sudo suricata -c /etc/suricata/suricata.yaml --runmode=workers

## Configuration Changes
### Date: 2024-09-28
- **Change:** Updated `HOME_NET` IP address in `suricata.yaml` to match my local network.
- **Reason:** Configured to match my local network.
