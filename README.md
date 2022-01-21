# AWS_Cloudformation_FrontEnd

_IaC for React app Front End_

**Prerequisite**

1. aws cli installed and login.

2. Clone the repository 
  ```git clone git@github.com:SpyralC/AWS_Cloudformation_FrontEnd.git```
  
3. Register a domain in Route 53. This will create a hosted zone automatically when your registration of doamin is succeeded. We will use that hosted zone in this tutorial. Note that this default hosted zone has exactly the same name servers as our domain. If you create another hosted zone, it will be allocated to random name servers. Name servers for a hosted zone are fixed when generated. Some DNS providers can take 24–48 hours to propagate DNS records.  This can lead to more time spent on acm validation.

Copy your hosted zone id.
![image](https://user-images.githubusercontent.com/57895489/150567797-e4ce1972-2820-49d2-9117-f09ba47101e7.png)


**Cloudformation**

change directory to IaC
```
cd AWS_Cloudformation_FrontEnd/IaC
```
In file _s3.yml_, customise parameters default values. You should always check parameters before creating a stack. 
![image](https://user-images.githubusercontent.com/57895489/150568433-c71ef335-24fb-4429-955b-12a54f25bd55.png)

run command ```aws cloudformation create-stack --stack-name s3 --template-body file://$PWD/s3.yml```

If you want to delete a stack later, use ```aws cloudformation delete-stack --stack-name s3 ```
Note: stack name must be unique.
![image](https://user-images.githubusercontent.com/57895489/150569354-f5a09b15-0b0e-4814-806f-779775d016cb.png)

In file _r53.yml_, place the hosted zone id with yours.
![image](https://user-images.githubusercontent.com/57895489/150569939-d8a7c8ab-3508-41df-8038-18df17f27b8c.png)

We will create 6 records in this stack: three A Records and three CNAME Records.
run ```aws cloudformation create-stack --stack-name r53 --template-body file://$PWD/r53.yml```

![image](https://user-images.githubusercontent.com/57895489/150570440-5f86412f-7355-4d6d-8319-9cc69016b91e.png)
Here we determinate a route that alias to AWS S3 weisite endpoint. Since the region is fixed to ap-southeast-2(Sydney) in this tutorial, you can get the applicable value using the AWS CLI command ```get-domain-names```, or find the regional hosted zone id here: _https://docs.aws.amazon.com/general/latest/gr/s3.html#s3_website_region_endpoints_



