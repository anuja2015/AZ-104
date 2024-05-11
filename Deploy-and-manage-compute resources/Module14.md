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
- There is no manual or automated scaling in Azure container instances. Only option is to redeploy a new ACI.
- Scaling is possible with the use of container groups or AKS.

<img width="959" alt="Screenshot 2024-05-11 075903" src="https://github.com/anuja2015/AZ-104/assets/16287330/fea64b16-012f-4c26-8b8d-f4b5086dabf8">

<img width="944" alt="Screenshot 2024-05-11 075921" src="https://github.com/anuja2015/AZ-104/assets/16287330/a849f106-a668-4d37-b7b2-eb62d929f016">

<img width="959" alt="Screenshot 2024-05-11 075943" src="https://github.com/anuja2015/AZ-104/assets/16287330/1ac56136-698a-4ea2-bbf3-10806c7cbbf7">

<img width="959" alt="Screenshot 2024-05-11 080036" src="https://github.com/anuja2015/AZ-104/assets/16287330/2154436c-2cac-4910-b895-a2b35822d016">

<img width="959" alt="Screenshot 2024-05-11 080107" src="https://github.com/anuja2015/AZ-104/assets/16287330/80c17637-9b3e-4d1b-b75b-44b153c13d30">

<img width="951" alt="Screenshot 2024-05-11 080313" src="https://github.com/anuja2015/AZ-104/assets/16287330/af02b517-edd9-496c-8b5b-4c53635d9644">

<img width="959" alt="Screenshot 2024-05-11 080345" src="https://github.com/anuja2015/AZ-104/assets/16287330/115edd00-77cd-4b12-8703-96cbf5e43074">

## Container group

- A collection of containers that get scheduled on the same host machine.
- The containers in a container group share a lifecycle, resources, local network, and storage volumes.
- Container group is analogous to a pod in K8s. 
- Azure Container Instances allocates resources to a multi-container group by adding together the resource requests of all containers in the group.
- two common ways to deploy a multi-container group: Azure Resource Manager (ARM) templates and YAML files.
     ARM template: recommended for other azure services when creating a container instances, such as azure Files file share.
     YAML : recommended when the deployment includes only container instances.
- Container groups can share an external-facing IP address, one or more ports on the IP address, and a DNS label with an FQDN.
- External client access: The port on the IP address is exposed and from the container to enable external clients to reach a container in a container group.
- Port mapping: not supported as container group share a port namespace.
- Deleted groups: When a container group is deleted, its IP address and FQDN are released

![Untitled](https://github.com/anuja2015/AZ-104/assets/16287330/c4a666d2-9189-4b74-8f79-2fb7eebc6867)

### Create a container group using YAML

#### 1. create a file deploy-aci.yaml

<img width="959" alt="Screenshot 2024-05-11 102627" src="https://github.com/anuja2015/AZ-104/assets/16287330/058e5731-3e93-43a0-b2fa-d67e0726b58d">


               apiVersion: 2019-12-01
               location: East US
               type: Microsoft.ContainerInstance/containerGroups
               name: myContainerGroup
               properties:
                 containers:
                   - name: aci-demo-app
                     properties:
                       image: mcr.microsoft.com/azuredocs/aci-helloworld:latest
                       resources:
                         requests:
                           cpu: 1
                           memoryInGb: 1.5
                       ports: 
                       - port: 80
                       - port: 8080
                   - name: aci-demo-sidecar
                     properties:
                       image: mcr.microsoft.com/azuredocs/aci-tutorial-sidecar
                       resources:
                         requests:
                           cpu: 1
                           memoryInGb: 1.5
                   osType: Linux
                   ipAddress:
                     type: Public
                     ports:
                     - protocol: tcp
                       port: 80
                     - protocol: tcp
                       port: 8080
               tags: {Tag: aci-demo}

#### 2. create a resource group for the container group.

          az group create --name azContainerRG --location EastUS     

<img width="876" alt="Screenshot 2024-05-11 104724" src="https://github.com/anuja2015/AZ-104/assets/16287330/60696ed4-8a85-4cf6-8af6-de6bedbdf588">

#### 3. create the container group

          az container create --resource-group azContainerRG --file deploy-aci.yaml

<img width="959" alt="Screenshot 2024-05-11 105556" src="https://github.com/anuja2015/AZ-104/assets/16287330/5e848900-f400-4017-85e2-a17b711c1bbc">

<img width="956" alt="Screenshot 2024-05-11 105617" src="https://github.com/anuja2015/AZ-104/assets/16287330/9a526b7d-0957-4c61-8464-45010639a639">

#### 4. View the deployment status

          az container show --resource-group azContainerRG --name myContainerGroup --output table

<img width="959" alt="Screenshot 2024-05-11 110116" src="https://github.com/anuja2015/AZ-104/assets/16287330/2b5d7b04-d46a-4aac-9f79-e033f1d01f97">

#### 5. View the logs

          az container logs --resource-group azContainerRG --name myContainerGroup --container-name aci-demo-app
          az container logs --resource-group azContainerRG --name myContainerGroup --container-name aci-demo-sidecar

![image](https://github.com/anuja2015/AZ-104/assets/16287330/bf5a7182-edcd-4393-b406-cc0775310c2a)


![image](https://github.com/anuja2015/AZ-104/assets/16287330/8aa270b8-e740-4cfc-9e78-0c61d6cf05c1)

#### 6. view container group in Azure portal

![image](https://github.com/anuja2015/AZ-104/assets/16287330/7de9edbc-c499-48f7-ae83-167fd72535c7)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/30f07898-861b-40a6-b8ab-5aecbe08d673)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/e0431b90-6ec8-4e36-acea-7cc694986def)

#### 7. View the running application using the public Ip.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/901ce1bb-05ec-4813-9822-56a12b0eee7a)



## Azure Container Apps 

- a serverless platform that allows  to maintain less infrastructure and save costs while running containerized applications.
  

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

## Azure Container Registry

- allows to build, store, and manage container images and artifacts in a private registry for all types of container deployments.
- Pricing tier : Basic (development use) , Standard (most Production scenarios) and Premium (geo replication and private access)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f52c733e-f27c-4191-abed-d8c5d345b8bb)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/797dd5b0-3be3-4b6f-b267-8aa72f32da77)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/ba23f24f-85fe-4a71-81ee-461b359d8ff0)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/19d22d62-70ed-43c9-a058-a6c12832663f)




