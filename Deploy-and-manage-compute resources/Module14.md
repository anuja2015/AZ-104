# Module:14 Configure Azure Container Instances

- Container-based virtualization allows to virtualize the operating system.
- This approach lets us run multiple applications within the same instance of an operating system, while maintaining isolation between the applications.
- The containers within a virtual machine provide functionality similar to that of virtual machines within a physical server.


## Container images

- All containers are created from container images.
- A container image is a lightweight, standalone, executable package of software that encapsulates everything needed to run an application. It includes the following components:
1. Code: The application’s source code.
2. Runtime: The environment required to execute the application.
3. System tools: Utilities necessary for the application to function.
4. System libraries: Shared libraries used by the application.
5. Settings: Configuration parameters specific to the application.

- When a container image is created, it becomes a portable unit that can run consistently across different computing environments. These images are the building blocks for containers, which are instances of these images running at runtime.

## Azure container instances

- Azure Container Instances offers the fastest and simplest way to run a container in Azure, without having to manage any virtual machines
- Fast startup times.
- Public IP connectivity and DNS names: Containers can be directly exposed to the internet with an IP address and FQDN (fully qualified domain name).
- Custom sizes: Container nodes can be scaled dynamically to match actual resource demands for an application.
- Persistent storage: Containers support direct mounting of Azure Files file shares.
- Linux and Windows containers: Container Instances can schedule both Windows and Linux containers.
- Virtual network deployment: Container Instances can be deployed into an Azure virtual network.
- Azure Container Instances (ACI) can be managed in several ways. __Azure Container Apps (ACA)__ is one way, and __Azure Kubernetes Service (AKS)__ is another.

## Azure Container Apps 

- a serverless platform that allows  to maintain less infrastructure and save costs while running containerized applications.
- 

__Common uses of Azure Container Apps:__

- Deploying API endpoints
- Hosting background processing jobs
- Handling event-driven processing
- Running microservices

Applications built on Azure Container Apps can __dynamically scale__ based on the following characteristics:

- HTTP traffic
- Event-driven processing
- CPU or memory load
- Any KEDA-supported scaler



## Container group

- A collection of containers that get scheduled on the same host machine.
- The containers in a container group share a lifecycle, resources, local network, and storage volumes.
- Azure Container Instances allocates resources to a multi-container group by adding together the resource requests of all containers in the group.
- two common ways to deploy a multi-container group: Azure Resource Manager (ARM) templates and YAML files.
     ARM template: recommended for other azure services when creating a container instances, such as azure Files file share.
     YAML : recommended when the deployment includes only container instances.
- Container groups can share an external-facing IP address, one or more ports on the IP address, and a DNS label with an FQDN.
- External client access: The port on the IP address is exposed and from the container to enable external clients to reach a container in a container group.
- Port mapping: not supported as container group share a port namespace.
- Deleted groups: When a container group is deleted, its IP address and FQDN are released

