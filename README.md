# Webhosting
This repo explain in detail step for a simple webpage hosting using AWS S3 and CloudFront. 

Prerequisite:
To follow this tutorial, you will need an AWS account and internet browser. 


Step 1. 
•	Login into the AWS management Console, in the search bar search S3. 
•	![Image1](https://user-images.githubusercontent.com/89212813/210140519-15214112-0a87-4cfc-8314-9ed555fc66f8.jpg)
•	Click on create Bucket. 
![Image2](https://user-images.githubusercontent.com/89212813/210140552-8083e493-4c8e-4668-8e8b-59ed63d19bb5.jpg)
•	Create two different bucket one with www and one without
www![image3](https://user-images.githubusercontent.com/89212813/210140583-94aff0a4-8f71-45de-9f46-c9b6627f5b72.jpg)
•	Give bucket name, here I have gave my bucket as www.naturegallery.click and select the region where you want to deploy your webpage.
•	Uncheck Block all public access button
![Image4](https://user-images.githubusercontent.com/89212813/210140623-b26cde9e-ca5f-4547-b9e1-a1f6b0bf27c7.jpg)

•	Check mark to the I acknowledge button 
![image5](https://user-images.githubusercontent.com/89212813/210140625-1ad9d2f4-cbfa-4591-ab67-95482e2016fc.jpg)

•	Now click on create bucket button. Now you have created a S3 bucket 
![Image6](https://user-images.githubusercontent.com/89212813/210140632-96a14536-65b9-46e0-9bbc-ed5cb17ddc9b.jpg)

•	Create another bucket following same step but bucket name will be without WWW. You have to make your bucket name and website name identical. 

Step 2. 
•	Next you have to upload your static webpage file to the S3 bucket with WWW name convention one. you will leave S3 Bucket without www name empty. 
click on S3 bucket naming WWW one !

•	Click on www.naturegallery.click one 
[Image7](https://user-images.githubusercontent.com/89212813/210140755-fa6f1484-974f-473e-8831-a51a8aadfe69.jpg)

•	Click on add file and choose your file from your local computer 
![image9](https://user-images.githubusercontent.com/89212813/210140783-06b4fd7d-029d-40e5-8398-4c08ece410e8.jpg)


•	Click on choose folder and upload your entire folder

![image10](https://user-images.githubusercontent.com/89212813/210140796-3358908a-23f4-4066-8400-797695726118.jpg)
 Click on upload and save change 

•	Now you have to create the bucket policy click on the S3 WWW.naturegallery.click folder, then click on the permission button.
![image12](https://user-images.githubusercontent.com/89212813/210140850-4728e4ec-9ddf-486b-851a-71ae1fff9cdf.jpg)

•	Click on the edit button 
![image13](https://user-images.githubusercontent.com/89212813/210140860-c536079a-c2eb-4076-ba65-1adc27c68117.jpg)
 
. Click policy generator fill up the the form or you can just clone form my repo, paste it on the box and then save it.
![image14](https://user-images.githubusercontent.com/89212813/210141000-80a1de30-d3d9-48d3-98de-8665279bc456.jpg)
![image15](https://user-images.githubusercontent.com/89212813/210141006-9693c426-a612-456e-999e-7061f3c85c1b.jpg)
![image16](https://user-images.githubusercontent.com/89212813/210141007-189a4d3c-6913-4b8d-8ed6-070d6caa5636.jpg)
![image17](https://user-images.githubusercontent.com/89212813/210141018-fc65ebac-e758-4b7f-a0d1-97b05a59eabd.jpg)
•	Now you are all set with creating S3 bucket upload file, folder and updating the bucket policy. 

Step 3. 

•	You have to enable public setting for our uploaded bucket, for that click in the bucket, first click on www bucket . 

![image19](https://user-images.githubusercontent.com/89212813/210141105-882aaa97-50c7-4de3-9aee-0d72ba756fb7.jpg)


•	Click on permission scroll down if you haven’t disable public access button click on edit and enable the public access. 
![image20](https://user-images.githubusercontent.com/89212813/210141137-15565f32-2743-4712-83f1-b332ce5b07fd.jpg)
Now click edit button of ststic webpage hosting 
![image21](https://user-images.githubusercontent.com/89212813/210141154-daed9eb6-2369-4512-94ac-00335f9b5370.jpg)
Click on enable ststic webpage hosting, put index.html as default value and click on save chnage. 

Step 4
 Now you have to register your domain name using route53. Open new tab search for route53.  
•	On left section of the route53 page click on registered domain. New window will pop up, check your domain availability and confirm your domain name. 

•	One you register domain come back to main page of the route53 You will see this screen 

![image22](https://user-images.githubusercontent.com/89212813/210141428-5ea7cf5f-3296-406a-8d9d-1a88fc9ab2da.jpg)

•	Click on your hosted Zone and click on your domain. You should have two record as default when you register you name. 
<img width="1332" alt="image23" src="https://user-images.githubusercontent.com/89212813/210141482-9b3304c4-7d3e-4513-b59e-feff413bba88.png">


•	Now we have to create two separate records for two buckets. Click on record 

•	Click on Simple routing, then click on next, then click on the define simple record button. Fill the required box as in the picture. Click on define simple record.  
<img width="1354" alt="image24" src="https://user-images.githubusercontent.com/89212813/210141498-a9768811-47f2-4a6a-83e1-4ca319ab8514.png">


•	Create record for both version of the bucket www and non www version of the S3 bucket. 
<img width="1340" alt="image25" src="https://user-images.githubusercontent.com/89212813/210141511-9f92abac-27c0-4ab2-9855-4dfa75ff90a4.png">

![image26](https://user-images.githubusercontent.com/89212813/210141520-0e631603-d431-4e67-9c2f-8aaf200d09c2.jpg)

Click on define simple record.

Step 5:
Now our final step to setup CloudFront which will cache your data for the better performance. 

•	Let setup our CloudFront distribution. For go to certificate manager, click on the get started button. 
![image28](https://user-images.githubusercontent.com/89212813/210141586-6963d1fa-7c2f-44a8-90f3-fc9a11d91c45.jpg)


•	Fill up the form for certificate manager form to create a certificate select DNS validation for validation and confirm . 
<img width="1401" alt="image29A" src="https://user-images.githubusercontent.com/89212813/210141606-effe3b4f-46f2-4964-8d04-557f0711edf1.png">


•	From there click on your domain name button and click on the create record in route53, it will automatically generate the record for you. Make sure you do for the both www and non www. 
•	Click on create button, it might take few minutes to enable. 
![image30](https://user-images.githubusercontent.com/89212813/210141692-69d2e35c-ff16-4bf2-a25a-754590378729.jpg)
![image31](https://user-images.githubusercontent.com/89212813/210142095-c1cc5a9b-20ca-4357-9d3d-d429acc93ab7.jpg)

•	You can validate by checking route53, if it had added two CNAME on your record, you are good to go. 
![image32](https://user-images.githubusercontent.com/89212813/210142395-0e182ae5-7561-4b3f-a47f-d55b387e6697.jpg)

• Now you can go and check your webpage in any browsing it should be display like this. 
![image33](https://user-images.githubusercontent.com/89212813/210144053-795438a8-a754-43fd-8785-2106b2d0397d.jpg)

Happy learning 





