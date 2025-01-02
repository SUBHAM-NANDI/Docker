### **Dockerfiles and Docker Images**

A Dockerfile is a text document containing instructions to build Docker images. These images consist of read-only layers, each layer corresponding to a Dockerfile instruction. Docker can automatically create images by interpreting these instructions. The following command is used to build an image from a Dockerfile:

```
docker build -f <dockerfile_path>
```

### **Dockerfile Instructions**

#### **1. FROM**
The `FROM` instruction initializes a new build stage and sets the base image for subsequent instructions. A valid Dockerfile must begin with a `FROM` instruction. The base image can be any valid image.

**Syntax:**
```
FROM <Image_name>:<Image_tag>
```

#### **2. LABEL**
The `LABEL` instruction adds metadata to an image, helping to organize images by project or record licensing information. Each label is defined as a key-value pair.

**Examples:**
```
LABEL com.example.version="0.0.1-beta"
LABEL vendor1="ACME Incorporated"
```

#### **3. RUN**
The `RUN` instruction executes commands in a new layer on top of the current image and commits the results. The resulting image serves as the base for the next step.

**Example:**
```
FROM ubuntu:14.04
RUN apt-get update
RUN apt-get install -y curl
```

#### **4. CMD**
The `CMD` instruction specifies the default command to run in the container. Only one `CMD` instruction is allowed per Dockerfile; the last `CMD` overrides any previous ones.

**Syntax:**
```
CMD ["executable", "param1", "param2"]
```

#### **5. EXPOSE**
The `EXPOSE` instruction specifies the ports on which the container listens for connections.

**Syntax:**
```
EXPOSE <port>
```

#### **6. ENV**
The `ENV` instruction sets environment variables for the container. It can also update the `PATH` variable to make software easier to run.

**Example:**
```
ENV PATH /usr/local/nginx/bin:$PATH
```

#### **7. ADD**
The `ADD` instruction copies files, directories, or remote URLs from the source to the specified destination within the image.

**Example:**
```
ADD hom* /mydir/  # Adds all files starting with “hom”
```

#### **8. VOLUME**
The `VOLUME` instruction designates storage areas, such as database files or configuration storage, that should be persisted outside the container.

#### **9. WORKDIR**
The `WORKDIR` instruction sets the working directory for subsequent `RUN`, `CMD`, and `ADD` instructions.

---
