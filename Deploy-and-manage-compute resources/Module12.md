# Module:12 Configure Azure App Service plans

## Azure App Service Plans.

- defines a set of compute resources needed to run a web application.
- one or more applications can be configured to run on same App service plan (on same compute resources).
- Each App Service plan defines three settings:
  
    i. Region: The region for the App Service plan, such as West US, Central India, North Europe, and so on.
  
   ii. Number of VM instances: The number of virtual machine instances to allocate for the plan.
  
  iii. Size of VM instances: The size of the virtual machine instances in the plan, including Small, Medium, or Large.
  
- When an App service plan is created for a region, a set of compute resources are created in the region.
- The applications run and scale in a different manner depending on the App service pricing tiers.

__1. Free tier__

- application run by receiving CPU minutes on shared VM instance.
- cannot scale out.

__2. Standard, Basic, Premium or Isolated tier__

- Applications run on all VMs configured in the plan.
- Multiple applications in the same plan share the same VM instances.
- all deployment slots run on the same virtual machine instances if there are multiple deployment slots.

| Feature | Free | Shared | Basic | Standard | Premium | Isolated |
| ------- | ---- | ------ | ----- | -------- | ------- | -------- |
| Usage   | Development and Testing | Development and Testing | Dedicated Development and Testing | Production workloads | Enhanced Scale, Performance | High Performance Security |
|Disk Space | 1 GB | 1 GB | 10 GB | 50 GB | 250 GB | 1 TB |
| Autoscale | na | na | na | supported | supported | supported |
| Deployment slots | 0 | 0 | 0| 5 | 20 | 20 |
| Max Instances | na | na | upto 3 | upto 10 | upto 30 | upto 100 | 


