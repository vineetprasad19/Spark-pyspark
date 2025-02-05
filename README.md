# Spark-pyspark
Apache Spark is an open-source, distributed computing system optimized for big data processing and analytics. It is important for a data engineer or cloud platform engineer to know the Spark capabilities which you can get in this repository.  

# 🔥 1. Spark Core Components  
➤ RDD (Resilient Distributed Dataset)  
Immutable distributed collection of objects.  
Supports transformations (map, filter, flatMap, reduceByKey).  
Actions (collect, count, reduce).  
  
➤ DataFrame API  
Higher-level abstraction over RDDs.  
Uses Catalyst Optimizer for query execution optimization.  
Supports SQL-like queries and transformations.  

➤ Spark SQL  
Enables querying structured data using SQL.  
Works with Hive, Parquet, ORC, Avro, JSON, and JDBC.  
Useful for ETL pipelines and data warehousing.  

# 🚀 2. Spark Execution & Optimization  
➤ Lazy Evaluation  
Spark builds a DAG (Directed Acyclic Graph) instead of executing immediately.  
Helps optimize execution before computation begins.  

➤ Transformations vs. Actions  
Transformations (lazy): map(), filter(), groupBy(), join().  
Actions (triggers execution): collect(), count(), show(), saveAsTable().  

➤ Performance Tuning  
Partitioning: Use repartition() and coalesce() wisely.  
Broadcast Joins: broadcast(df) for small datasets.  
Caching & Persistence: Use .cache() or .persist(StorageLevel.MEMORY_AND_DISK).  
Skew Handling: Salting technique, skewed joins.  

# 🏆 3. Spark on Cloud (Databricks, AWS EMR, GCP, OCI)  
➤ Databricks  
Uses Delta Lake for ACID transactions & versioning.  
Supports Unity Catalog for fine-grained access control.  
Optimized for ML & AI workloads.  

➤ AWS EMR  
Managed Spark service with S3 as storage.  
Integrates with Glue (ETL), Athena, Redshift.  

➤ OCI Data Flow  
Serverless Apache Spark on Oracle Cloud.  
Can integrate with ADW, Object Storage.  

# ⚡ 4. Streaming & Real-Time Processing  
➤ Structured Streaming  
Uses micro-batches for real-time processing.  
Works with Kafka, Kinesis, and Event Hubs.  
Supports checkpointing & stateful processing.  

from pyspark.sql import SparkSession  
from pyspark.sql.functions import *  
  
spark = SparkSession.builder.appName("StreamingApp").getOrCreate()  
  
streamingDF = spark.readStream.format("kafka").option("subscribe", "topic-name").load()  
streamingDF.selectExpr("CAST(value AS STRING)").writeStream.format("console").start()  

# 🎯 5. Spark ML & AI
➤ MLlib (Machine Learning)  
Scalable ML algorithms for classification, regression, clustering.  
Supports Random Forest, Gradient Boosting, KMeans, ALS (Recommender Systems).  

➤ GraphX (Graph Processing)  
PageRank, Connected Components, and Shortest Path algorithms.  
Useful for social network analysis, fraud detection.  

# 🔗 6. Spark Integrations
Databases: PostgreSQL, SQL Server, Oracle (via JDBC).  
Storage: S3, HDFS, ADLS, OCI Object Storage.  
Workflow Orchestration: Apache Airflow, Azure Data Factory.  
Security: Role-based access control (RBAC), Kerberos, OAuth.  

# ⚙️ 7. Best Practices for Enterprise Data Engineering
Optimize partition sizes (128MB–256MB per partition).  
Avoid small files problem (use coalesce() before writing).  
Enable Adaptive Query Execution (AQE) for dynamic optimizations.  
Use Delta Lake for ACID transactions & versioning.  
Leverage Auto Scaling in Databricks/AWS EMR.  
