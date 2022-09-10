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


### Step 2 Create Storage transfer job 

### What is Storage Transfer Service?
Data Transfer Service is a product that enables users to: Move or backup data to a Cloud Storage bucket from other cloud storage providers or on-premises storage. Move data from one Cloud Storage bucket to another to be available to different groups of users or applications

Reffer this doc:- https://cloud.google.com/storage-transfer/docs/overview

- Go to GCP console 


