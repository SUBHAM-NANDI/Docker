# Docker: Service Containers

## Why Are Containers Required?

Containers are essential for modern application deployment and management because they provide:
- **Efficiency**: Containers consume fewer resources compared to virtual machines.
- **Consistency**: Ensures that applications behave the same way across different environments.
- **Portability**: Simplifies application migration between development, testing, and production environments.
- **Scalability**: Enables easy scaling of applications to meet demand.

---

## What Is a Container Image?

A **container image** is a lightweight, standalone package that includes everything needed to run an application:
- **Code**
- **Runtime**
- **System Tools**
- **Libraries**

Key Points:
- A **container** is a running instance of a container image.
- You can run multiple containers from the same image, enabling horizontal scaling and environment replication.

---

## Docker Central Repository: Docker Hub

Docker Hub is a central repository where container images are stored. Developers can:
- Download pre-built images.
- Publish custom images.
- Manage private and public container images.

---

## Starting an Nginx Web Server in Docker

### Start Nginx Web Server:
To run an open-source Nginx web server:
```bash
docker container run --publish <host_port:container_port> <image_name>
```
Example:
```bash
docker container run --publish 8080:80 nginx
```

### Stop Container Foreground Process:
Use the keyboard shortcut:
```plaintext
Ctrl + C
```

### Start Container in Background (Detach Mode):
Run the container in the background:
```bash
docker container run --publish <host_port:container_port> --detach <image_name>
```
Example:
```bash
docker container run --publish 8080:80 --detach nginx
```

---

## Listing and Managing Containers

### List Running Containers:
- Modern command:
  ```bash
  docker container ls
  ```
- Old way:
  ```bash
  docker ps
  ```

### List All Containers (Running and Stopped):
```bash
docker container ls -a
```

### Stop a Running Container:
```bash
docker container stop <container_id>
```

---

## Difference Between `run` and `start` Commands

### `run`:
- Always starts a **new container**.

### `start`:
- Starts an **existing container** that has been stopped.

---

## Naming Containers

Assigning a specific name to a container:
```bash
docker container run --publish 80:80 --detach --name <name> <image_name>
```
Example:
```bash
docker container run --publish 80:80 --detach --name my-nginx nginx
```

---

## Viewing Logs and Processes in Containers

### View Logs of a Specific Container:
```bash
docker container logs <container_name>/<container_id>
```

### View Running Processes Inside a Container:
```bash
docker container top <container_id>
```

---

## Removing Unused Containers

Remove unused containers by specifying their IDs:
```bash
docker container rm <space_separated_container_ids>
```

---

## Containers vs. Virtual Machines

| **Feature**            | **Containers**                 | **Virtual Machines (VMs)**    |
|------------------------|-------------------------------|-------------------------------|
| Virtualization Layer   | Operating System (OS)         | Hardware                      |
| Resource Allocation    | Lightweight and portable      | Resource-intensive            |
| Portability            | Highly portable               | Limited portability           |

### Key Takeaway:
- Containers virtualize the **OS**, while VMs virtualize the **hardware**.
- Containers are ideal for modern, scalable applications.

---

## Resource Management and Monitoring

### View Resource Consumption of Containers:
```bash
docker stats [container_name or container_id]
```

### Get Detailed Information About a Container:
```bash
docker inspect [container_name or container_id]
```

---

## Interactive Containers

### Start a Container in Interactive Mode:
```bash
docker run -it [image_name or image_id] [command]
```

#### Options:
- `-i`: Keeps STDIN open even if not attached.
- `-t`: Allocates a pseudo-terminal (TTY).

Example:
```bash
docker run -it ubuntu bash
```

---

## Running Commands in Running Containers

Execute commands inside a running container:
```bash
docker exec [options] [container_name or container_id] [command]
```

#### Parameters:
- `[options]`: Additional options (e.g., `-it` for interactive mode).
- `[container_name or container_id]`: The name or ID of the running container.
- `[command]`: The command to execute inside the container.

Example:
```bash
docker exec -it my-nginx bash
```

---


