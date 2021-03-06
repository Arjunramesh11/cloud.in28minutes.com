---
layout:     post
title:      Amazon S3 Glacier - vs Amazon S3 - AWS Certification
date:       2020-06-06 12:31:19
summary:    Let's get a quick overview of Amazon S3 Glacier from an AWS certification perspective. We will look at important certification questions regarding Amazon S3 Glacier. 
categories:  AWS_CLOUD AWS_STORAGE
permalink:  /aws-certification-amazon-s3-glacier-vs-amazon-s3
---

Let's get a quick overview of Amazon S3 Glacier from an AWS certification perspective. We will look at important certification questions regarding Amazon S3 Glacier and compare it with Amazon S3.

## You will learn
- What is Amazon S3 Glacier?
- When do we use Amazon S3 Glacier?
- How is Amazon S3 Glacier different from Amazon S3?

## AWS Certification - 25 PDF Cheat Sheets + Free Course

Each cheat sheet contains:
- FAQs and Tutorials with 5-20 slides
- Notes to quickly review and prepare for certification exam
- Certification Exam Tips
- Certification and Interview Scenario Questions

<div>
 <a href="https://links.in28minutes.com/cloud-in28minutes-teachable-free-link" target="_blank" class="button instagram">Download</a>
</div>


## Amazon S3 Glacier
![](/images/aws/00-icons/glacier.png)

- In addition to existing as a S3 Storage Class, S3 Glacier is a seperate AWS Service on it own!
- **Extremely low cost storage** for archives and long-term backups:
	- Old media content
	- Archives to meet regulatory requirements (old patient records etc)
	- As a replacement for magnetic tapes
- High durability (11 9s - 99.999999999%)
- High scalability (unlimited storage)
- High security (**encrypted** at rest and in transfer)
- Cannot upload objects to Glacier using Management Console
	- Use REST API, AWS CLI, AWS SDK

## Amazon S3 vs S3 Glacier
 
| Feature |Amazon S3 | S3 Glacier | 
|--|:--|:--|
| Terminology   |  Objects (files) are stored in Buckets (containers)     |    Archives (files) are stored in Vaults (containers)     |
|Keys|Objects keys are user defined|Archive keys are system generated identifiers|
|Mutability|(Default) Allows uploading new content to object|After an archive is created, it cannot be updated <BR/>(Perfect for regulatory compliance)|
|Max size|Each object can be upto 5TB|Each archive can be upto 40TB|
|Management Console|Almost all bucket and object operations supported|Only vault operations are supported. You cannot upload/delete/update archives.|
|Encryption|Optional| Mandatory using AWS managed keys and AES-256. <BR/>You can use client side encryption on top of this.|
|WORM Write Once Read Many Times| Enable Object Lock Policy|Enable Vault lock policy| 

## Retrieving archives from S3 Glacier
![](/images/aws/00-icons/glacier.png)

- **Asynchronous two step process** (Use REST API, AWS CLI or SDK)
	- Initiate a archive retrieval
	- (After archive is available) Download the archive
- Reduce costs by **optionally specify a range, or portion,** of the archive to retrieve
- Reduce costs by **requesting longer access times**
	- Amazon S3 Glacier:
		- Expedited (1 – 5 minutes)
		- Standard (3 – 5 hours)
		- Bulk retrievals (5–12 hours) 
	- Amazon S3 Glacier Deep Archive:
		- Standard retrieval (upto 12 hours)
		- Bulk retrieval (upto 48 hours)
