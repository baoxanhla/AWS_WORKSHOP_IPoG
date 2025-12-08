---
title: "Week 6 Worklog"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Understand AWS relational (SQL) and non-relational (NoSQL) data storage services based on storage needs.
* Know how to deploy, operate, and optimize databases on AWS.
* Understand Amazon ElastiCache for accelerating data access.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Learn about Amazon RDS and Aurora <br>&emsp; + Engines: MySQL, PostgreSQL... <br>&emsp; + Multi-AZ Availability <br>&emsp; + Read Replicas Performance <br>&emsp; + Automated Backups and Restoration | 10/13/2025 | 10/13/2025 | <https://cloudjourney.awsstudygroup.com/>|
| Tue | - **Practice**: <br>&emsp; + Prepare environment for RDS instance: Create VPC, EC2, RDS Security Group, DB Subnet Group <br>&emsp; + Create EC2 Instance <br>&emsp; + Create RDS Database Instance in Private Subnet connected to EC2 <br>&emsp; + Deploy application <br>&emsp; + Automated Backup and Restore <br>&emsp; + Resource cleanup | 10/14/2025 | 10/14/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Learn Amazon DynamoDB: NoSQL <br>&emsp; + Core components <br>&emsp; + Primary key and Sort key <br>&emsp; + Read/Write Capacity with On-demand or Provisioned <br> - **Practice**: Use AWS Console and Cloudshell to: <br>&emsp; + Create table <br>&emsp; + Write, read, and update data <br>&emsp; + Query data <br>&emsp; + Create global secondary index <br>&emsp; + Query secondary index | 10/15/2025 | 10/15/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Learn AWS SDK Python packages (for Python) <br>&emsp; + Botocore <br>&emsp; + Boto3 <br> - **Practice**: <br>&emsp; + Configure AWS CLI with Boto3 library <br>&emsp; + Use Python to develop with DynamoDB: Create Table, write, read, update, delete data, Load sample data, Query, scan data, and delete table <br>&emsp; + Resource cleanup. | 10/16/2025 | 10/16/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - Learn Amazon ElastiCache <br>&emsp; + ElastiCache for Redis: Clusters <br>&emsp; + ElastiCache nodes <br>&emsp; + ElastiCache for Redis shards <br> - **Practice:** <br>&emsp; + Create IAM User Access Keys to configure AWS CLI + Use AWS Console and CLI to create ElastiCache cluster <br>&emsp; + Use AWS SDK to write and read data on ElastiCache: <br>&emsp;&nbsp;&nbsp; + Create and connect to Clusters <br>&emsp;&nbsp;&nbsp; + Set and Get strings <br>&emsp;&nbsp;&nbsp; + Set and Get a hash with multiple items <br>&emsp;&nbsp;&nbsp; + Publish (write) and subscribe (read) <br>&emsp;&nbsp;&nbsp; + Write and read from a stream | 10/17/2025 | 10/17/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 6:

* Understanding of Relational Databases: Amazon RDS & Aurora
  * Grasped RDS architecture and database engines (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora).
  * Understood the Multi-AZ Deployment mechanism.
  

[Image of AWS RDS Multi-AZ architecture]

  * Learned how to optimize reads using Read Replicas.

* Practical RDS System Deployment
  * Self-deployed an architecture including: VPC, Subnet Groups, Security Group, EC2 Bastion Host, RDS Private Instance.
  * Connected EC2 to RDS via security groups.
  * Deployed an application connecting to RDS.
  * Performed backup/restore and resource cleanup.

* Understood and used Amazon DynamoDB (NoSQL)
  * Understood core concepts:
    * Tables, Items, Attributes, Partition key, Sort key.
    
    * RCU/WCU, On-demand vs Provisioned.
    * Global Secondary Index (GSI), Local Secondary Index (LSI).
  * Learned how to optimize queries through proper key design.
  * Practiced CRUD operations, Query, Scan, and GSI Query.

* Able to use AWS SDK for Python (Boto3)
  * Configured AWS CLI & credentials to work with Boto3.
  * Wrote Python code to:
    * Create DynamoDB tables.
    * Write / read / update / delete data.
    * Scan data and Perform Conditional Queries.
    * Delete tables and release resources.
  * Understood Boto3 API structure and error handling.

* Understood and deployed Amazon ElastiCache for Redis
  * Grasped ElastiCache architecture: node, shard, cluster, primary/replica.
  
  * Understood cluster mode enabled / disabled.
  * Created ElastiCache Redis cluster using Console and CLI.
  * Used AWS SDK to:
    * Set/Get key-value.
    * Set/Get hash.
    * Publish/Subscribe.
    * Work with Redis Streams.
  * Understood the role of caching in application optimization.