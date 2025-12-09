---
title: "Blog 3"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Group database tables under AWS Database Migration Service tasks for PostgreSQL source engine
by **Manojit Saha Sardar** and **Chirantan Pandya** | on **September 05, 2025** | in **Amazon Aurora**, **AWS Database Migration Service**, **Expert (400)**, **PostgreSQL compatible**, **RDS for PostgreSQL**, Technical How-to | Permalink

In large-scale data migration projects using **AWS DMS** (Database Migration Service), properly **grouping source tables** into tasks is crucial for ensuring high performance and avoiding latency during the **full load** or **CDC** phases. In this article, the authors demonstrate how to analyze the PostgreSQL source database to determine optimal task sizing and table grouping, helping you plan the migration in a way that minimizes latency and maximizes throughput.

---

## Background & Motivation
During migration, certain tasks may run slowly or become bottlenecks due to suboptimal grouping — for example, combining too many small tables or mixing extremely large tables with smaller ones.  
Delays can arise during both **full load** and **CDC** because of resource contention, I/O bottlenecks, or uneven load distribution.  
By analyzing table characteristics and system metrics, you can make well-informed decisions regarding the number of DMS tasks, grouping strategy, and identifying tables that should be isolated.

---

## Solution Overview
The approach combines metadata from the source database (catalogs, statistical views) with information about hardware and workload to:

1. Determine the appropriate number of DMS tasks  
2. Group tables into balanced tasks  
3. Isolate “special” tables (for example: very large tables, tables with LOBs) to avoid cross-impact  

Proposed workflow:

1. Create a **control table** on the source database  
2. Populate metadata (size, partitions, indexes, LOB presence, DML statistics)  
3. Monitor daily changes/growth  
4. Classify tables by step/priority  
5. Group tables into tasks  
6. Execute migration based on these groups  

This method helps minimize latency and provides a more accurate estimation of task size.

> *The following diagram illustrates the solution architecture.*

![Image](/images/2-Proposal/table.png)

---

## Prerequisites
You need:
* Knowledge of **AWS DMS** (Database Migration Service)  
* A PostgreSQL source database and the ability to run SQL / PL/pgSQL scripts to collect metadata  

---

## Step 1: Create the control table
On the PostgreSQL source database, create a table (for example, `TABLE_MAPPING`) to store metadata for each candidate table:

CREATE TABLE TABLE_MAPPING (
  OWNER             VARCHAR(30),
  OBJECT_NAME       VARCHAR(30),
  OBJECT_TYPE       VARCHAR(30),
  SIZE_IN_MB        NUMERIC(12,4),
  STEP              INTEGER,
  IGNORE            CHAR(3),
  PARTITIONED       CHAR(3),
  PART_NUM          INTEGER,
  SPECIAL_HANDLING  CHAR(3),
  PK_PRESENT        CHAR(3),
  UK_PRESENT        CHAR(3),
  LOB_COLUMN        INTEGER,
  GROUPNUM          INTEGER,
  TOTAL_DML         INTEGER
);

This table stores one row for each table (or each partition), containing metrics such as table size, number of partitions, presence of PK/UK, number of LOB columns, total DML, and more.

---

## Step 2: Populate the control table
Use PostgreSQL system catalogs and statistical views (such as pg_tables, pg_partitioned_table, pg_inherits, and statistical views) to collect:

* Table size and partitioning information
* Number of indexes, and whether primary / unique keys exist
* Number of LOB columns
* Amount of DML (insert / update / delete)
* Partition statistics (min, max, average size)

This provides a metadata + workload “snapshot” to guide your table grouping decisions.

---

## Step 3: Monitor the change level
Track the amount of DML activity on each table over time. This helps determine which tables are “hot” (frequently changing) and which are more static, which should be taken into account during grouping.

---

## Step 4: Classify tables / assign step numbers
Based on table size, change frequency, special handling needs (LOB, missing PK), or partitioning, assign a step number or priority to each table. For example:

* Step 1: small tables with low change rate  
* Step 2: medium tables with moderate change  
* Step N: very large tables or tables with heavy change activity  

You can also mark **IGNORE** for tables you do not want included in a specific task, or **SPECIAL_HANDLING** for tables requiring isolation or special treatment.

---

## Step 5: Group tables into tasks
Use the control table and the classification to group tables so that:

* Each task has a balanced workload (size + change rate)  
* Very large tables (e.g., > 2 TB) can be isolated  
* Tables with LOBs or missing PK should be grouped carefully or isolated  
* High-change tables can be separated to avoid affecting others  
* The total number of tasks should not be excessive and should match the capacity of the replication instance  

The goal is to reduce lag, minimize resource contention, and evenly distribute workload across tasks.

---

## Factors to consider
When grouping and sizing tasks, consider:

* **Database object size**: extremely large tables should be isolated or handled separately  
* **Partitioned vs non-partitioned**: partitioned tables may allow parallel migration  
* **Presence of PK / unique index**: DMS requires PK/UK for LOB handling and avoiding duplicates  
* **Use of LOBs**: LOB-heavy tables increase complexity and migration cost — isolating them is recommended  
* **Change volume (CDC)**: high-change tables should be grouped carefully to avoid CDC lag  
* **Parallelism & resource limits**: replication instance capacity (CPU, I/O), network bandwidth, etc., determine the optimal number of tasks  

---

## Reference architecture & workflow
The article includes a diagram showing how source tables are classified, grouped, and processed in parallel migration tasks (not shown here).  
It also describes how the control table is maintained during migration and used to track progress and adjust groupings as needed.

---

## Summary & recommendations
By:

* Systematically analyzing metadata  
* Classifying and grouping tables based on characteristics and workload  
* Isolating high-risk tables (very large, LOB, missing PK)  
* Balancing load across tasks  

You can reduce migration risks, improve task size estimation, and achieve a smooth, high-performance migration.

---

## Authors

|
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Manojit Saha Sardar ![Image](/images/2-Proposal/manojit.png) | **Manojit** is a **Senior Database Engineer** at AWS and is recognized as an **expert** in AWS DMS, Amazon RDS, and Amazon RDS for PostgreSQL. In his role at AWS, he **collaborates with customers** to resolve **various data transfer scenarios** and **supports challenges** involving Amazon RDS for Oracle and Amazon RDS for PostgreSQL. |
| Chirantan Pandya ![Image](/images/2-Proposal/chirantan.png) | **Chirantan** is a **Database Engineer (AWS Countdown Premium)** and an expert in AWS DMS and Amazon RDS for PostgreSQL. At AWS, he **works closely with customers** to provide **guidance and technical support** for **database migration projects**, as well as projects involving **Amazon RDS for PostgreSQL and Oracle**. |
