# migration-s3bucket-to-gcsbucket

## What is S3 bucket?
Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance. Customers of all sizes and industries can store and protect any amount of data for virtually any use case, such as data lakes, cloud-native applications, and mobile apps. With cost-effective storage classes and easy-to-use management features, you can optimize costs, organize data, and configure fine-tuned access controls to meet specific business, organizational, and compliance requirements.

Reffer this doc:- https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingBucket.html

## What is GCS bucket?
Cloud Storage allows world-wide storage and retrieval of any amount of data at any time. You can use Cloud Storage for a range of scenarios including serving website content, storing data for archival and disaster recovery, or distributing large data objects to users via direct download.

Reffer this doc:- https://cloud.google.com/storage/docs

## Why data migration is needed.
Cloud data migration is the procedure of moving information, localhost applications, services, and data to the distributed cloud computing infrastructure. The success of this data migration process is depending on several aspects like planning and impact analysis of existing enterprise systems. One of the most common operations is moving locally stored data in a public cloud computing environment. This paper, through a multivocal literature review, identifies the key advantages and consequences of migrating data into the cloud. There are five different cloud migration strategies and models prescribed to evaluate the performance, identifying security requirements, choosing a cloud provider, calculating the cost, and making any necessary organizational changes. The results of this research paper can give a road map for the data migration journey and can help decision makers towards a safe and productive migration to a cloud computing environment.

Reffer this doc:-https://www.sciencedirect.com/science/article/pii/S1877050919321921

## Migration market revenue 
![image](https://user-images.githubusercontent.com/63963025/189472009-87a5beda-4908-4a33-ad8f-b2318902a334.png)

Reffer this doc:- https://www.mavenwave.com/blog/trends_cloud_migration_financial_services/

## steps to migrate S3 to GCS 

### Step 1 create a S3 bucket in AWS cloud 
- create bucket 
<img width="1353" alt="image" src="https://user-images.githubusercontent.com/63963025/189472114-a15863e8-ef95-4b17-bf2b-614f8786aa49.png">
- bucket name must be unique 
<img width="819" alt="image" src="https://user-images.githubusercontent.com/63963025/189472158-59836858-61cd-4960-990b-e4085c4e4604.png">

<img width="808" alt="image" src="https://user-images.githubusercontent.com/63963025/189472177-f61eecb2-037b-4b2d-82c6-13b6e20a99de.png">

- make sure your bucket should be private this is best practice your data not get exposed publicly  
<img width="800" alt="image" src="https://user-images.githubusercontent.com/63963025/189472221-c2c1111b-0156-4d18-8102-0c0a2252e588.png">

- encryption is disable we can kms key for encryption now my case this is disable and create bucket 
<img width="800" alt="image" src="https://user-images.githubusercontent.com/63963025/189472319-3b1cbcf2-1579-442a-ad18-fb680962cb4c.png">

- S3 bucket create successful 
<img width="982" alt="image" src="https://user-images.githubusercontent.com/63963025/189472492-216740df-4be5-409f-a78a-dbefe8c75ecb.png">

- Go inside bucket <b> rushabh-s3-migration </b> upload object inside the bucket 
<img width="1050" alt="image" src="https://user-images.githubusercontent.com/63963025/189472540-2dac58c4-2b00-4794-8e20-b981d5415147.png">

<img width="844" alt="image" src="https://user-images.githubusercontent.com/63963025/189472649-a50f338c-0cd7-409f-92f6-bb515173c755.png">

- files uploaded successfully 
<img width="1324" alt="image" src="https://user-images.githubusercontent.com/63963025/189472827-1e9d167f-7689-49e1-935d-6b6bb2faa117.png">

### Step 2 Create GCS Bucket 
- Create bucket 
<img width="1394" alt="image" src="https://user-images.githubusercontent.com/63963025/190841318-44cfc7a5-8136-4ae2-9afb-aca75297964a.png">

- Bucket name 
<img width="554" alt="image" src="https://user-images.githubusercontent.com/63963025/190841349-6d5d1ff7-9466-4f78-9e86-282fb145e02b.png">

- Select regional bucket i am using <b>asia-south1(Mumbai)</b>  
<img width="544" alt="image" src="https://user-images.githubusercontent.com/63963025/190841363-e0a88c66-df78-4494-a0d2-e4c647bf0702.png">

- Select storage Class <b>Standard</b>
<img width="544" alt="image" src="https://user-images.githubusercontent.com/63963025/190841408-eee8a574-01fb-4f8f-b698-bf03aaceb13d.png">

- Control object level permission in my case i am using uniform giving Bucket level permission 
<img width="543" alt="image" src="https://user-images.githubusercontent.com/63963025/190841443-44e7c69a-c9e9-4c6e-a88d-b75c9e370888.png">

- Go to GCP console 
<img width="1377" alt="image" src="https://user-images.githubusercontent.com/63963025/190840749-a2426fd7-e8f7-4aee-a40d-f5f46f471c66.png">

- All default create Bucket 
<img width="1109" alt="image" src="https://user-images.githubusercontent.com/63963025/190841479-242b7409-84c3-45da-8e45-bfc455ee0e03.png">


### Step 3 Create Storage transfer job 

### What is Storage Transfer Service?
Data Transfer Service is a product that enables users to: Move or backup data to a Cloud Storage bucket from other cloud storage providers or on-premises storage. Move data from one Cloud Storage bucket to another to be available to different groups of users or applications

Reffer this doc:- https://cloud.google.com/storage-transfer/docs/overview

- Search for Data transfer
<img width="1108" alt="image" src="https://user-images.githubusercontent.com/63963025/190840871-181fd986-e823-4fc4-a6b0-211a4b735823.png">

- Create Transfer job 
<img width="1390" alt="image" src="https://user-images.githubusercontent.com/63963025/190841133-c5e4ff15-8fe4-4a5c-b844-10346cb91877.png">

- Select source and Destination of bucket
<img width="964" alt="image" src="https://user-images.githubusercontent.com/63963025/190841168-158e44b2-944c-4262-a531-1157ed45edd4.png">

- Now Go to AWS Console IAM --> Create a User --> attach policy --> AmazonS3FullAccess 
<img width="904" alt="image" src="https://user-images.githubusercontent.com/63963025/190842300-ae779c64-b1ff-4007-a85b-20492400d88b.png">


<img width="1033" alt="image" src="https://user-images.githubusercontent.com/63963025/190842332-17ac37e3-085d-4fc2-9bab-4abb50b72d3a.png">


<img width="1063" alt="image" src="https://user-images.githubusercontent.com/63963025/190842408-b44db220-8b08-4796-a501-5cd5a84e0257.png">

- Create user 

<img width="1033" alt="image" src="https://user-images.githubusercontent.com/63963025/190842425-3b9102a3-73a4-4855-8924-a50569e3b51c.png">

- Copy Access-key Secret-key and paste to Data transfer job <b> Do not Share this key to anyone </b>
<img width="997" alt="image" src="https://user-images.githubusercontent.com/63963025/190842472-058c9d26-a2fb-47f1-9b67-c4cd002ef8f6.png">


 <img width="949" alt="image" src="https://user-images.githubusercontent.com/63963025/190842567-c290d064-1000-4ced-99c2-70cd334217f1.png">

- Select Destination Bucket 
<img width="465" alt="image" src="https://user-images.githubusercontent.com/63963025/190842620-0518a85d-10ed-47d1-a4c7-57b4a25a61b0.png">

<img width="557" alt="image" src="https://user-images.githubusercontent.com/63963025/190842636-a067bb82-a9a7-411b-8205-495f7ad6c9c5.png">

- In my case i will Run once you can schedule your job according to your usecase 
<img width="569" alt="image" src="https://user-images.githubusercontent.com/63963025/190842645-b5f773eb-e16b-4bbb-9d08-0be73daeb1cf.png">


- job completed Successfully  

<img width="1125" alt="image" src="https://user-images.githubusercontent.com/63963025/190842733-808241b0-e30a-4ea4-a33e-ab1eb980b058.png">



<img width="1140" alt="image" src="https://user-images.githubusercontent.com/63963025/190842756-e49a522b-70e0-4b19-bfa8-a0e47644f8e1.png">


### We have successfully migrated our data using Data-transfer Service 
