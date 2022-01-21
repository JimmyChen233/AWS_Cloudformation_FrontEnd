# AWS_Cloudformation_FrontEnd

_IaC for React app Front End_

**Prerequisite**

Register a domain in Route 53. This will create a hosted zone automatically when your registration of doamin is succeeded. We will use that hosted zone in this tutorial. Note that this default hosted zone has exactly the same name servers as our domain. If you create another hosted zone, it will be allocated to random name servers. Name servers for a hosted zone are fixed when generated. Some DNS providers can take 24–48 hours to propagate DNS records.  This can lead to more time spent on acm validation.

Copy your hosted zone id.
![image](https://user-images.githubusercontent.com/57895489/150567797-e4ce1972-2820-49d2-9117-f09ba47101e7.png)


**First, clone the repository and change directory to IaC**
```
git clone git@github.com:SpyralC/AWS_Cloudformation_FrontEnd.git
cd AWS_Cloudformation_FrontEnd/IaC
```
