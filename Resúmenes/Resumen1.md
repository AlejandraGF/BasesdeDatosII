# Bases de datos II - Resumen 1
###### Estudiante: Alejandra González - 2020035049

---
###### Definiciones, acrónimos y abreviaturas:
AWS - Amazon Web Services \
BI - business intelligence \
MPP - massively parallel processing \
OLTP - online transaction processing \
<a name="datalakes">Data lake</a>: Centralized, highly flexible storage repository that stores large amounts of structured and unstructured data in its raw, original, and unformatted form. \
<a name="s3">Amazon S3</a>:
popular storage solution for non-transactional data.
### Introduction
A data warehouse is a central repository of information coming from one or more data sources used in most large enterprises. In the past however, building and running a data warehouse was complicated and expensive. When data volumes grew or an enterprise wanted to make analytics and reports available to more users, they had to choose between accepting slow query performance or investing time and effort on an expensive upgrade process. \
Cloud data warehouses like Amazon Redshift changed how enterprises think about data warehousing by dramatically lowering the cost and effort associated with deploying data warehouse systems, without compromising on features, scale, and performance. Amazon Redshift makes it simple and cost-effective to analyze large volumes of data using existing BI tools. With Amazon Redshift, you can get the performance of columnar data warehousing engines that perform MPP at a tenth of the cost.

### Modern Analytics and Data Warehousing Architecture 
The differences between data warehouses and OLTP databases.
- Data warehouses are optimized for batched write operations and reading high
volumes of data.
- OLTP databases are optimized for continuous write operations and high
volumes of small read operations.

To get the benefits of using a data warehouse managed as a separate data store with your source OLTP or other source system, building an effective data pipeline is recommended. Such a pipeline extracts the data from the source system, converts it into a schema suitable for data warehousing, and then loads it into the data warehouse.
#### Analytics Architecture 
Analytics pipelines are designed to handle large volumes of incoming streams of data from sources such as databases, applications, and devices. A typical analytics pipeline has the following stages: 

1. **Collect data**: Consider that you probably have different types of data, such as transactional data, log data, streaming data, and Internet of Things (IoT) data. AWS provides solutions for data storage for each of these types of data. 
2. **Store the data**: 
    * Lake house: — Combines the best elements of data warehouses and [data lakes](#datalakes). With this architecture, you can store data in open file formats in your data lake and query it in place while joining with data warehouse data. 
    * Data warehouse — Using data warehouses, you can run fast analytics on large volumes of data and unearth patterns hidden in your data by leveraging BI tools. 
    * Data mart — Simple form of data warehouse focused on a specific functional area or subject matter, you can have specific data marts for each division in your enterprise.
3. **Process the data**: This provides data that potentially has useful information. This process might, for example, tell you about your user behavior and the relative popularity of your products.
    1. Batch Processing:
        * Extract Transform Load (ETL) — ETL is the process of pulling data from multiple sources to load into data warehousing systems. 
        * Extract Load Transform (ELT) — Variant of ETL, where the extracted data is loaded into the target system first. Transformations are performed after the data is loaded into the data warehouse. 
        * <a name="abcd">Online Analytical Processing (OLAP)</a> — OLAP systems store aggregated historical data in multidimensional schemas. Used widely for query, reporting, and analytics.
    2. Real-Time Processing: Information derived from this processing gives companies visibility of their business and customer activity, such as service usage (for metering or billing), website clicks, geolocation of devices, people, and physical goods. This enables them to respond promptly to emerging situations.
4.**Analyze and visualize the data**: You need the right tools to analyze and visualize the processed data. In many cases, you can perform data analysis using the same tools you use for processing data.

### Data Warehouse Technology Options 
The options available for building a data warehouse are: row-oriented databases, column-oriented databases, and massively parallel processing architectures. 

**Row-oriented**: 
- Typically store whole rows in a physical block. 
- High performance for read operations is achieved through secondary indexes.
- In a row-based data warehouse, every query has to read through all of the columns for all of the rows in the blocks that satisfy the query predicate, including columns you didn’t choose. 

**Column oriented:**
- Organize each column in its own set of physical blocks.
- More I/O efficient for read-only queries.
- Improved compression. When all the data is the same data type, the database can use extremely efficient compression algorithms. As a result, you need less storage compared to a row-oriented database.

**MPP**: An MPP architecture enables you to use all the resources available in the cluster for processing data. MPP data warehouses allow you to improve performance by simply adding more nodes to the cluster.

### Amazon Redshift Deep Dive
As a columnar MPP technology, Amazon Redshift delivers fast query and I/O performance for virtually any data size by using columnar storage, and by parallelizing and distributing queries across multiple nodes.

**Integration with Data Lake**: Amazon Redshift provides a feature called Redshift Spectrum that makes it easier to both query data and write data back to your data lake in open file formats.\
**Durability and Availability**: Amazon Redshift automatically detects and replaces any failed node in your data warehouse cluster. It makes your replacement node available immediately, and loads your most frequently accessed data first so you can resume querying your data as quickly as possible.\
**Elasticity and Scalability**: You can scale compute and storage independently, and pay
only for what you use.

### Operations 
As a managed service, Amazon Redshift completely automates many operational tasks, including: \
**Cluster Performance** — Amazon Redshift performs Auto ANALYZE to maintain accurate table statistics. It also performs Auto VACUUM to ensure that the database storage is efficient and deleted data blocks are reclaimed. \
**Cost Optimization** — Amazon Redshift enables you to pause and resume the clusters that need to be available only at a specific time, enabling you to suspend on-demand billing while the cluster is not being used. 

### Ideal Usage Patterns
Amazon Redshift is ideal for [OLAP](#abcd) using your existing BI tools. Enterprises use
Amazon Redshift to do the following:
- Running enterprise BI and reporting
- Analyze global sales data for multiple products
- Store historical stock trade data
- Analyze ad impressions and clicks
- Aggregate gaming data
- Analyze social trends
- Measure operation efficiency, and financial performance in health care 

### Anti-Patterns
Amazon Redshift is not ideally suited for the following usage patterns:
- **OLTP** – Amazon Redshift is designed for data warehousing workloads delivering
extremely fast and inexpensive analytic capabilities. If you require a fast
transactional system, you might want to choose a relational database system.
- **Unstructured data** – Data in Amazon Redshift must be structured by a defined
schema. Amazon Redshift doesn’t support an arbitrary schema structure for each
row. 
- **BLOB data** – If you plan to store binary large object (BLOB) files such as digital
video, images, or music, you might want to store the data in [S3](#s3). In this scenario, Amazon Redshift keeps track of
metadata (such as item name, size, date created, owner, location, etc)
about your binary objects, but the large objects themselves are stored in S3. 
