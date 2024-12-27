#### Docker Networking: Connecting Containers and the Host Machine

Docker provides a variety of networking features to ensure that containers can communicate with one another and with the host machine. Containers and services do not need to be aware of where they are deployed, which makes them portable and scalable.

##### Docker Network

- **Bridge Network**: By default, Docker uses the bridge network for container communication. This virtual private network isolates containers within the same cluster but prevents communication between containers in different clusters unless additional configurations are applied.
  
- **Overlay Network**: This allows communication between containers across different Docker hosts. Technologies like VXLAN or IPSec are often used to create virtual networks that span multiple hosts.

- **Container Network Interfaces (CNI)**: CNI is a specification that defines how container runtimes interact with networking plugins. This allows you to combine different container runtimes with various networking solutions for greater flexibility.

#### Connecting Containers to Networks

When you start a container, Docker automatically connects it to the default bridge network. However, you can create custom networks for specific purposes.

- **Example**: For a MySQL and PHP application, you can create a network called `sql_php_nwt` and for MongoDB and PHP, a network called `mongo_nwt`.
  
This ensures that the containers within each network can communicate with each other efficiently and securely.

#### Docker Commands for Networking and Communication

Here are some essential Docker commands for managing and inspecting Docker networks and containers:

1. **Start a container with port mapping**:
   ```bash
   docker container run -p <host_port>:<docker_port> -d <image>
   ```
   This command allows you to expose a port from the Docker container to the host machine, making the container's service accessible externally.

2. **Inspect container ports**:
   ```bash
   docker port <container_id>
   ```
   Use this command to find the ports and protocols associated with a container.

3. **Find the IP address of a container**:
   ```bash
   docker inspect <container_id>
   ```
   This command retrieves detailed information about a container, including its IP address.

4. **Show all Docker networks**:
   ```bash
   docker network ls
   ```
   This command lists all the networks available on the Docker host.

5. **Filter networks by type**:
   ```bash
   docker network -f driver=bridge
   ```
   This command filters and lists networks with the `bridge` driver.

6. **List network IDs and drivers**:
   ```bash
   docker network ls --format "{{.ID}}: {{.Driver}}"
   ```
   Use this command to display the network ID and driver type for all available networks.

7. **Inspect a specific Docker network**:
   ```bash
   docker network inspect <network_name>
   ```
   This command provides detailed information about a particular network, including the containers connected to it.

#### DNS in Docker Containers

Docker containers use DNS to communicate with each other, rather than relying on IP addresses. DNS makes it possible for containers to use easy-to-remember hostnames instead of complex IP addresses, simplifying container communication.

- Docker automatically provides DNS functionality for containers by allowing containers to communicate with each other using the container name or the service name (if using Docker Compose).
- Containers in the same network can resolve each other’s names using Docker's built-in DNS service.



