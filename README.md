# Small Office LAN: Client-Server Network in Cisco Packet Tracer

A mini project that builds and tests a single-subnet LAN (192.168.1.0/24) in Cisco Packet Tracer and demonstrates client-service communication over HTTP.

**Author:** Philip Mawuli Wemegah (Group Alpha)

## Network architecture and device roles

| Device | Role |
|---|---|
| PC0, PC1 | **Clients.** End-user workstations that request services (HTTP) and send ICMP echo requests. |
| Server0 | **Server.** Hosts web content over HTTP and responds to requests on the LAN. |
| Switch0 (2960) | Layer 2 device that connects all endpoints and forwards frames by MAC address. |
| Router0 | Layer 3 default gateway (192.168.1.1) for the local subnet. |

## IPv4 addressing

| Device | Interface | IPv4 Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | FastEthernet0 | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |
| Server0 | FastEthernet0 | 192.168.1.100 | 255.255.255.0 | 192.168.1.1 |
| Router0 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 | N/A |

Also available as [addressing-table.csv](addressing-table.csv).

## Tasks

### Task 1: Identify and place network devices
Placed 1 router, 1 switch (2960), 2 PCs (PC0, PC1) and 1 server (Server0) in the Packet Tracer workspace.

### Task 2: Build a simple LAN
Connected the PCs, server and router to the switch (FastEthernet0/1 to 0/4) using copper straight-through cables. All link indicators turned solid green.

![Topology](images/task1-2-topology.png)

### Task 3: Configure IPv4 addressing
Assigned static IPs, subnet masks and the default gateway on PC0, PC1 and Server0, and enabled the router interface from the CLI (see [configs/router0.txt](configs/router0.txt)).

![Router CLI](images/task3-router-cli.png)
![Switch port status](images/task3-switch-port-status.png)

### Task 4: Test network connectivity
From PC0, pinged PC1 (192.168.1.20) and Server0 (192.168.1.100). All 4 packets were sent and received with 0% loss.

![Ping test](images/task4-ping-test.png)

### Task 5: Demonstrate client-server communication
Verified the HTTP service on Server0, then opened `http://192.168.1.100` in PC0's web browser. The server's page loaded, showing the client requesting a service and the server responding.

![HTTP in web browser](images/task5-web-browser-http.png)

## Repository structure

```
.
├── README.md
├── addressing-table.csv
├── configs/
│   ├── router0.txt
│   └── verification-commands.txt
└── images/
    ├── task1-2-topology.png
    ├── task3-router-cli.png
    ├── task3-switch-port-status.png
    ├── task4-ping-test.png
    └── task5-web-browser-http.png
```

## Skills demonstrated
Cisco Packet Tracer, IPv4 addressing, Cisco IOS CLI, LAN design, connectivity testing (ping), client-server architecture, HTTP.

## Possible next steps
Add more PCs, a second switch, a second LAN on another router interface, DHCP/DNS services, and static routing between two routers.
