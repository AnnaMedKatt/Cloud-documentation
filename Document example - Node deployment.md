## **Laboratory work №3: Installation**  

*version 10.2022*

### **Goals, assumptions and initial states** 

- The main purpose is to introduce students to the 3rd *"Box"* installation;  
- The result should be a deployed, working environment with all services (from OpenStack to billing and PaaS);  
- Use **distribution ver. 3.0.7**;  
- Installation configuration has to use **Fixed** IPs, names (UI - overcloud.private.infra.cloud.ru) in order to simplify preparation of variables, inventory and etc. Any differences will lead to major change of inventory and variables;  
- Stand is deployed in [public](http://cloud.cloud.ru/app) with following quotas:  
    - *instances*: 13 units (12 are required);  
    - *disks*: 20 units (18 are required);  
    - *Virtual CPU*: 120 units (102 is required for instances);  
    - *HDD*: 2 TB storage (1.2 TB is required);  
    - *High IOPS SSD*: 5 units (total volume 500 GB) - each instance is connected with High IOPS SSD disk and requires 150 GB memory for the root file system;  
        - 6 floatings IPs (2 for RS1 and deploy);
        - 2 Neutron security groups;  
    - 10 networks and subnets (6 are required);  
    - Cloud_Flavor_Lab-8-12;  
- 5 internal networks, 1 external network:  

    | Network            | IP-adress   |  
    | :-----------       | :---------- |
    | box3-cloudexternal | 10.x.x.x/16 |  
    | box3-portal        | 10.x.x.x/28 |  
    | box3-management    | 10.x.x.x/24 |
    | box3-cephexternal  | 10.x.x.x/26 |  
    | box3-cephinternal  | 10.x.x.x/26 |
    | shared             | 10.x.x.x/24 |  

- Internal networks (10.x.x.x./124) are used as mgmt/storage/internal/external. External network will be used as cloud-external network for the instances launched in the future overcloud;  
- The partners will receive already launched BM and Deploy-BM, on which all required files and resources for deploying are already uploaded, unpacked and sorted, repository service Nexus is also launched. 

### **Preparing node deployment, Nexus launch and preparing all other nodes** 

Nexus is already launched on the deploy host with a script:

> /home/centos/box-3.0.0/nexus-box-3.0.0/run_nexus.sh  

This script contains admin password for Nexus:

> $ tail -3 /home/centos/box-3.0.0/nexus-box-3.0.0/run_nexus.sh  
> echo ========================================================
> echo NEXUS ADMIN PASSWORD IS: ************  
> echo ========================================================