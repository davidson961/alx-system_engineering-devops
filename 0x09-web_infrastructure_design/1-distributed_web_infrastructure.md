### Description

This architecture features a distributed web infrastructure designed to mitigate traffic on the primary server by offloading some tasks to a secondary, replica server. This is facilitated through a load-balancing server that allocates workload between the primary and replica servers.

### Infrastructure Details

- **Load Balancing Algorithm**: The HAProxy load balancer employs the Round Robin algorithm, which systematically allocates server requests in a sequential and equitable manner, based on server weights. This dynamic approach allows for real-time adjustments in server weighting.
- **Load Balancer Configuration**: The HAProxy facilitates an Active-Passive configuration, differing from Active-Active setups where workloads are evenly distributed across all nodes. In this scenario, not all nodes are concurrently active, with passive nodes ready to take over should the active node become unavailable.
- **Primary-Replica Database Dynamics**: In this setup, the Primary server handles both read and write operations, while the Replica server is limited to read-only tasks. Synchronization occurs following write operations on the Primary server.
- **Application Role of Nodes**: The Primary node manages all write-related tasks for the site, while the Replica node is tasked with read operations, thereby reducing the read load on the Primary node.