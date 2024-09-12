# POX-based Routing with Mininet Topology

This project demonstrates using the POX OpenFlow controller for custom routing in a Mininet network topology.

## Files
- **`pox_controller.py`**: Implements routing logic using OpenFlow.
- **`mininet_topology.py`**: Defines the Mininet topology.

## Features
- **Dynamic Routing**: Routes packets based on source/destination IPs.
- **Packet Analysis**: Handles TCP, UDP, and ICMP traffic.
- **Flow Management**: Adds flow entries dynamically to minimize load.
- **Subnet Matching**: Routes packets based on destination subnet.
- **Default Drop**: Drops unrecognized packets.

### Example Routing Logic
- Switch `4`, destination IP `200.20.2.8` → Forward to port `48`.
- Switch `1`, subnet `200.20.3.x` → Forward to port `14` or `15`.

## Topology Overview
1. **Core Switch**: Connects department switches.
2. **Sales**: Hosts (`laptop1`, `printer`) on Switch 4.
3. **OT**: Hosts (`ws1`, `ws2`) on Switch 1.
4. **IT**: Hosts (`ws3`, `ws4`) on Switch 2.

## Running the Project

1. **Start Mininet**:
    ```bash
    sudo mn --custom mininet_topology.py --topo final_topo --controller=remote --ip=127.0.0.1 --port=6633
    ```

2. **Start POX Controller**:
    ```bash
    ./pox.py forwarding.pox_controller
    ```

3. **Test Connectivity**:
    ```bash
    mininet> pingall
    ```

## Dependencies
- **Mininet**: Network emulator.
- **POX**: OpenFlow controller.
- **Python**: For scripting.
