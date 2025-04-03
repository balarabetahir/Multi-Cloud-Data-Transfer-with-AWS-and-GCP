# Multi-Cloud-Data-Transfer-with-AWS-and-GCP
More and more engineering teams are spreading their resources across different cloud providers. Why? It gives them better redundancy, helps avoid getting locked into one vendor, and often saves money too. 

<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Multi-Cloud Data Transfer with AWS and GCP

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-multicloud-storage)

**Author:** tahirgroot@gmail.com  
**Email:** tahirgroot@gmail.com

---

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s5k4l5m6)

---

## Introducing Today's Project!

In this project, I will demonstrate how to steup storage transfer between multiple cloud providers. I'm doing this project to learn multi-cloud and storage skills so that engineering teams can learn can improve redundancy and avoid vendor lock in.

### Tools and concepts

Services I used were GCP Cloud Storage(GCS), Amazon s3, AWS IAM and Google Storage Transfer Service. Key concepts I learnt include storage transfers, identity federation,  manifest files and how to create a GCS bucket.

### Project reflection

This project took me approximately 1 hour The most challenging part was setting up Identity Federation which required a custom It was most rewarding to see a selective file transfer work after using a manifest file

---

## Setting up Data in S3

I started this project by setting up an s3 bucket, I uploaded 10 files, all documentation of nextwork projects. 

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s1g7h8j9)

---

## Setting up GCP

Google Cloud Platform is another cloud service provider from Google I set up a GCP account to create a destination storage location for today's multi-cloud data transfer.

GCP's free tier includes a suite of 20+ free services (for example, cloud storage, cloud engine for running VMs, or even cloud build and deploy which are similar to CodeBuild and CodeDeploy in AWS I also get credit $300 usd of free credit to use in services not covered by three free teir, but this free credit only lasts 90 days.

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s2g8h9j0)

---

## Storage Transfer

Data transfers are important for setting up backup storage locations in a multicloud architecture setup. Using multiple cloud providers for the transfer has benefits such as redundancy and cases where an application in another cloud service provider's environment needs access to that data, trabsferring the files over to the other cloud service providercan also help with latency.

The transfer is set up using Storage Transfer Service, which is GCP's service for moving data in and out of its storage location/service called GCP cloud storage(GCS) We need this service because it helps with handling the operations of a multicloud transfer. like authentication and automating transfers

There are two different types of transfers you could set up Batch Transfers and event driven transfers. The difference is WHEN these transfers happen -batch transfers are either one off or on a consistent schedule, event driven transfers happen in real-time. i.e. on demand/on the go, whenever there's been an update in the source bucket(i.e. in S3).

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s3k2l3m4)

---

## Granting GCP Access to AWS

To connect AWS and GCP, I'm using identity federation, which works by giving GCP(or GCP's Storage Transfer Service, to be specific). TEMPORARY access to AWS. This is more secure than other methods because it is passwordless.. GCP does not need to store any password or credentials, which also protects  us from any password leaks...What will happen is that AWS will recognize storage Transfer Service as a trusted service, so that  request from STS are accepted and have permissions granted automatically. 

I created a custom IAM role for Storage Transfer Service becuase it needs read only access in order to read and retrieve files to later store it in GCS(GCP Cloud Storage)

Within the IAM role, I needed to write a custom trust policy because AWS will use it to identify the storage Transfer Service based on a subject ID,which is the unique ID of the unique ID of the service account linked with storage transfer service.

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s4k3l4m5)

---

## Transferring from S3 to GCS!

To set up my destination GCS bucket, I needed to set up its region, which means where the data is stored and its storage class, which means how frquently the data will be accessed. I chose a single region(one that's closet to the AWS region) and the standard storage class since we we'll be accessing the storgae class soon.

I verified my data transfer was successful by visting my  GCS bucket when the transfer was finished - and seeing that all the objects I uploaded into my s3 are now inside our GCS bucket.

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_s5k4l5m6)

---

## Transfer with a Manifest

In a project extension, I am doing a selective transfer, which means i am  going to transfer only a SELECT bunch of files from the source. A manifest file is the shopping/instruction list that  store Transfer list service will use  to identify which files to transfer today. 

I verified my data transfer was successful by visting my  GCS bucket when the transfer was finished - and seeing that all the objects I uploaded into my s3 are now inside our GCS bucket.

![Image](http://learn.nextwork.org/radiant_blue_innocent_pawpaw/uploads/aws-multicloud-storage_rththrthrth)

---

## Trial, Error, Success

---

---
