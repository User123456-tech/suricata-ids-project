# Suricata IDS Project

### Date: 2024-09-28

## Overview

This project involves setting up Suricata as an Intrusion Detection System (IDS) on a Raspberry Pi to monitor network traffic and visualize alerts using Kibana.

## Tools Used

- Raspberry Pi OS
- Suricata
- Elasticsearch
- Filebeat
- Kibana

## Setup Steps

1. **Installed Suricata.**
2. **Configured Suricata to monitor traffic on the network interface:**
   - Edited the configuration file located at `/etc/suricata/suricata.yaml`.
3. **Started Suricata** with the command:

   ```bash
   sudo suricata -c /etc/suricata/suricata.yaml --runmode=workers
   
4. Installed and configured Elasticsearch to store Suricata logs:

- Downloaded and installed Elasticsearch.
- Configuration changes made in elasticsearch.yml.

5. **Installed Filebeat and configured it to forward Suricata logs to Elasticsearch:**
   - Command to install Filebeat:
     ```bash
     sudo apt-get install filebeat
     ```
   - Updated the Filebeat configuration file (`filebeat.yml`) to include the paths to Suricata logs. The relevant section of the configuration file looked something like this:
     ```yaml
     filebeat.inputs:
       - type: log
         enabled: true
         paths:
           - /var/log/suricata/*.log
     ```
   - This configuration ensured that all Suricata log files in the specified directory were monitored and forwarded to Elasticsearch.
   - Filebeat automatically handles the transmission of logs to Elasticsearch, making it seamless for visualization in Kibana.


6. **Set up Kibana to visualize Suricata alerts in a user-friendly dashboard:**
   - **Installation:** Downloaded and installed Kibana from the official Elastic website. Followed the installation instructions specific to Raspberry Pi.
   - **Configuration:** 
     - Edited the `kibana.yml` file to set the Elasticsearch URL and adjusted any necessary settings.
     - Set the proper permissions for the Kibana user to ensure it can access the Elasticsearch data.
   - **Creating the Dashboard:**
     - Configured the Kibana index patterns to match the Suricata log formats. This involved defining the correct time filter field name to enable time-based queries.
     - Built custom visualizations based on the Suricata logs, including alert counts, types of detected threats, and timestamps.
     - Arranged visualizations on the dashboard to provide a comprehensive view of network activity.
   - **Testing:**
     - Ran several tests by generating network traffic that would trigger Suricata alerts. 
     - Verified that alerts appeared in the Kibana dashboard in real time, confirming that the entire pipeline from Suricata to Elasticsearch to Kibana was functioning correctly.
     - Analyzed the alerts and visualizations to ensure they accurately represented the network activity, making adjustments as necessary to refine the visualizations.
       
Below is a sample of the Kibana dashboard used to monitor the network:


![Elastic IDS Dashboard](https://github.com/user-attachments/assets/d3e6ab38-11dd-4c1c-8b3a-ed84d5331abb)




## Configuration Changes

Date: 2024-09-28

Change: Updated HOME_NET IP address in suricata.yaml to match my local network.

Reason: Configured to match my local network.

Date: 2024-09-28

Change: Updated Filebeat configuration to include paths to Suricata logs.

Reason: To ensure logs are sent to Elasticsearch for indexing.


## Recent Changes

Updated Suricata rules file (suricata.rules) to include necessary rules for network monitoring.

Verified Suricata configuration, resulting in successful operation.

Ensured Elasticsearch is receiving logs from Filebeat and verified the setup.

Added Kibana as the front-end to visualize logs and alerts through dashboards.


## Commit History

Committed changes to the project on 2024-09-29.
