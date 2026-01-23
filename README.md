# Raspberry Pi IDS: Network Traffic Analysis & Threat detection 
This is a custom Suricata IDS running on a Raspberry Pi 4. This project focuses on learning defensive strategies and identifying attack surfaces on a common home network.

## Hardware & Environment
- **Platform:** Raspberry Pi 4 (4GB of RAM)
- **Storage:** External High-Speed Samsung T7 Shield SSD (logging)
- **OS:** Raspberry OS Lite (64-bit) 
- **Engine:** Suricata 7.0 (Custom compiled/Tuned)

## Current Monitoring Scope: DNS Security 
The IDS is currently configured as a passive DNS monitor. Since the individual devices aren't connected directly to the switch(but through the router). 
- **DNS tunneling:** detecting non-standard dns query load

## Topology 

graph TD
    Internet((Internet)) --- Switch[Managed Switch]
    
    subgraph Core Infrastructure
        Switch --- Pi[Raspberry Pi 4 - IDS]
        Switch --- Router[Home Router - Port 8]
    end

    subgraph SSD Storage
        Pi --- SSD[(External SSD)]
    end

    subgraph User Devices
        Router --- Laptop[MBP used to configure and manage homelab]
        Router --- IoT
        Router --- Other personal devices
    end

    style Pi fill:#f96,stroke:#333,stroke-width:2px
    style SSD fill:#bbf,stroke:#333
    style Switch fill:#eee,stroke:#333

## Disclaimer
This project is for educational and home-lab purposes only. Signatures are tuned for specific device behavior and may require adjustment for different network environments. 
