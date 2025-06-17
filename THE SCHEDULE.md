

---

## Woche 1: Advanced SQL, Cloud Foundations (AWS), & Docker Fundamentals

**Focus:** Rapidly master advanced SQL, establish a strong AWS footing, and get hands-on with Docker.

### ✅ **SQL Mastery & Optimization (Est. 2 hours/day)**
- [ ] **Daily Practice:**
    - [ ] LeetCode SQL Puzzles (Advanced Joins, CTEs, Window Functions)
    - [ ] StrataScratch SQL Challenges (Complex aggregations, real-world scenarios)
- [ ] **Study & Implement:**
    - [ ] SQL Optimization: Indexing strategies (create and test indexes)
    - [ ] SQL Optimization: Analyze `EXPLAIN` plans in PostgreSQL for your queries
    - [ ] Design and query moderately complex Star/Snowflake schemas (create a sample schema and write analytical queries)

### ☁️ **AWS Core Services & Infrastructure Setup (Est. 2 hours/day)**
- [ ] **IAM (Identity and Access Management):**
    - [ ] Implement best practices for creating users, groups, roles, and policies
    - [ ] Secure your AWS root account (enable MFA)
- [ ] **S3 (Simple Storage Service):**
    - [ ] Explore advanced features: versioning, lifecycle policies, storage classes (conceptual understanding)
    - [ ] Practice Boto3 for programmatic access: upload, download, list objects/buckets
- [ ] **RDS (Relational Database Service):**
    - [ ] Launch a PostgreSQL instance (Free Tier eligible)
    - [ ] Configure security groups for RDS access
    - [ ] Connect to RDS instance (using `psql` and a GUI tool like DBeaver/pgAdmin) and perform basic operations
- [ ] **EC2 (Elastic Compute Cloud):**
    - [ ] Launch a Linux EC2 instance (e.g., Amazon Linux 2 or Ubuntu)
    - [ ] Connect via SSH
    - [ ] Install necessary tools (e.g., psql client, Python3, pip)
    - [ ] Configure EC2 security groups
- [ ] **VPC (Virtual Private Cloud):**
    - [ ] Study basic VPC concepts: subnets, route tables, internet gateway, NAT gateway (conceptual)

### 🐳 **Docker Fundamentals & First Container (Est. 3 hours/day)**
- [x] Install Docker Desktop (or Docker Engine on Linux)
- [ ] **Core Concepts Study:** Images, Containers, Dockerfile, Docker Hub, Volumes, Networks [[Images, Containers, Dockerfile, Docker Hub, Volumes, Networks]]
- [ ] **Practical:**
    - [ ] Write a simple `Dockerfile` for a Python application (e.g., a script that prints "Hello Docker")
    - [ ] Build a Docker image from your `Dockerfile`
    - [ ] Run your Python application as a Docker container
    - [ ] Practice Docker commands: `docker build`, `docker run`, `docker ps -a`, `docker images`, `docker stop <id/name>`, `docker rm <id/name>`, `docker logs <id/name>`, `docker exec -it <id/name> bash`
    - [ ] Pull and run a standard image from Docker Hub (e.g., `postgres:latest`, `python:3.9-slim`)

### 🧠 **Command Line (Linux) & Bash Scripting (Est. 1 hour/day)**
- [ ] Practice advanced text processing: `grep` (with regex), `awk`, `sed`
- [ ] Write a simple Bash script for automation (e.g., backup a directory, list files older than X days)
- [ ] Setup and use `cron` on your EC2 instance to schedule your Bash script

---

## Woche 2: ETL with Python & Docker, Intro to Data Warehousing on AWS

**Focus:** Build a containerized ETL pipeline, start with cloud data warehousing.

### 🐳 **Containerized Python ETL Pipeline (Est. 3 hours/day)**
- [ ] **Design ETL Process:**
    - [ ] Select a public API (e.g., OpenWeatherMap, REST Countries, a stock API)
    - [ ] Define transformations (using Pandas)
    - [ ] Target: AWS RDS PostgreSQL instance from Week 1
- [ ] **Develop Python ETL Script:**
    - [ ] Implement extraction, transformation, and loading logic
    - [ ] Focus on modularity (functions for each step)
    - [ ] Implement robust error handling (`try-except`)
    - [ ] Add comprehensive logging (Python's `logging` module)
- [ ] **Containerize with Docker:**
    - [ ] Create a `Dockerfile` for the Python ETL script (include `requirements.txt`)
    - [ ] Build the Docker image
    - [ ] Test running the ETL process from within a container (ensure connectivity to RDS)
- [ ] **(Stretch Goal):** Parameterize your Docker container using environment variables for API keys, DB credentials

### 🌌 **Data Warehousing on AWS (Amazon Redshift) (Est. 3 hours/day)**
- [ ] **Launch & Connect:**
    - [ ] Launch an Amazon Redshift cluster (e.g., `dc2.large` - be mindful of Free Tier or costs, shut down when not in use)
    - [ ] Configure security groups for Redshift access
    - [ ] Connect to Redshift using a SQL client
- [ ] **Understand Redshift:**
    - [ ] Columnar nature vs. row-based (PostgreSQL)
    - [ ] Distribution styles (KEY, ALL, EVEN - conceptual)
    - [ ] Sort keys (conceptual)
- [ ] **Design & Implement Schema:**
    - [ ] Design a simple Star Schema for data from your ETL
    - [ ] Create tables in Redshift (DDL)
- [ ] **Load Data:**
    - [ ] Modify Python ETL script (or create new) to load transformed data into Redshift
    - [ ] Learn and practice Redshift `COPY` command for bulk loading from S3 (upload a sample CSV to S3 and `COPY` it into a Redshift table)

### 🐍 **Advanced Python & Project Structure (Est. 1 hour/day)**
- [ ] Implement unit tests for your Python ETL logic using `pytest`
- [ ] Structure your Python project professionally (e.g., `src/`, `tests/`, `data/`, `docker/`, `config/`)

### ☁️ **AWS Networking & Security (Est. 1 hour/day)**
- [ ] Deepen understanding of Security Groups vs. NACLs
- [ ] Study secure credential management:
    - [ ] IAM Roles for EC2 instances (if running scripts from EC2)
    - [ ] AWS Secrets Manager (conceptual understanding, or basic practice if time)

---

## Woche 3: Apache Spark Fundamentals & Processing Data from S3

**Focus:** Get hands-on with Spark for larger-scale data processing.

### 🔥 **Apache Spark with PySpark (Est. 4 hours/day)**
- [ ] **Setup Spark Environment:**
    - [ ] **Option 1 (Recommended for Realism):** AWS EMR (Elastic MapReduce)
        - [ ] Launch a small EMR cluster (e.g., with Spark installed)
        - [ ] Connect using EMR Notebooks or SSH to submit jobs
    - [ ] **Option 2 (Local Convenience):** Docker image for Spark (e.g., `jupyter/pyspark-notebook` or Bitnami Spark)
    - [ ] **Option 3 (Local Full Control):** Install Spark locally
- [ ] **Core Spark Concepts Study:**
    - [ ] Spark Architecture (Driver, Executors, Cluster Manager)
    - [ ] RDDs (Resilient Distributed Datasets - conceptual)
    - [ ] DataFrames & Datasets API (primary focus)
    - [ ] SparkSQL
    - [ ] Lazy Evaluation & Actions vs. Transformations
- [ ] **PySpark DataFrame API Practice:**
    - [ ] Configure Spark to access S3 (using IAM roles if on EMR/EC2, or access keys locally - be careful with keys)
    - [ ] Read data from S3: CSV, JSON, Parquet files
    - [ ] Transformations: `select`, `filter`, `withColumn`, `join`, `groupBy`, `agg`, `orderBy`, `distinct`, UDFs (User Defined Functions - basic)
    - [ ] Actions: `show()`, `count()`, `collect()`, `first()`, `take()`
    - [ ] Write data back to S3 (e.g., in Parquet format)
- [ ] **Practical Task:**
    - [ ] Process a moderately sized dataset (e.g., 100MB-1GB CSV/JSON) from S3 using PySpark on EMR or your chosen Spark setup
    - [ ] Perform significant transformations (e.g., clean data, derive new columns, join with another small dataset, aggregate)
    - [ ] Write the processed results back to S3 in Parquet format

### 💾 **Data Lakes & Optimized File Formats (Est. 2 hours/day)**
- [ ] **Deep Dive Study:** Parquet and ORC (columnar storage benefits, compression, schema evolution, predicate pushdown)
- [ ] **Practice:**
    - [ ] Convert data between formats (CSV/JSON to Parquet/ORC and vice-versa) using PySpark
    - [ ] Convert data between formats using Pandas (for smaller files to understand the structure)
- [ ] **Understand Data Partitioning:**
    - [ ] How to partition data in S3 (e.g., by date `year=/month=/day=`)
    - [ ] How Spark utilizes partitioning for query optimization

### 🐳 **Docker Compose for Multi-Container Applications (Est. 1 hour/day)**
- [ ] Learn Docker Compose syntax (`docker-compose.yml` version 3)
- [ ] Define services, networks, volumes
- [ ] Create a `docker-compose.yml` for a simple setup:
    - [ ] Your Python ETL application (from Week 2)
    - [ ] A PostgreSQL database service
- [ ] Practice `docker-compose up -d`, `docker-compose down`, `docker-compose logs <service_name>`, `docker-compose ps`

### ☁️ **AWS Glue - Introduction & Data Catalog (Est. 1 hour/day)**
- [ ] Explore AWS Glue Data Catalog:
    - [ ] Create a Glue Crawler to infer schema from data in S3 (e.g., your processed Parquet files)
    - [ ] Understand how Glue creates tables in the Data Catalog
- [ ] Run a simple AWS Glue ETL job:
    - [ ] Use a pre-built transform or write a simple PySpark script within Glue Studio
    - [ ] E.g., Convert CSV in S3 to Parquet in S3 using a Glue job

---

## Woche 4: Workflow Orchestration with Apache Airflow & Docker

**Focus:** Automate and schedule data pipelines using Airflow, containerized.

### 💨 **Apache Airflow Deep Dive (Est. 4 hours/day)**
- [ ] **Setup Airflow:**
    - [ ] Run Airflow locally using Docker Compose (use the official `docker-compose.yml` from Apache Airflow docs)
- [ ] **Core Airflow Concepts Study & Practice:**
    - [ ] DAGs (Directed Acyclic Graphs): definition, parameters (`schedule_interval`, `start_date`, `catchup`, `tags`)
    - [ ] Operators:
        - [ ] `BashOperator` (run shell commands)
        - [ ] `PythonOperator` (run Python callables)
        - [ ] `DockerOperator` (run Docker containers)
        - [ ] `PostgresOperator` (run SQL against PostgreSQL)
        - [ ] (If using Redshift) `RedshiftSQLOperator` or generic SQL operators
        - [ ] (If using EMR) `EmrAddStepsOperator`, `EmrCreateJobFlowOperator` (or `ECSOperator` / `KubernetesPodOperator` for more advanced scenarios)
    - [ ] Sensors (e.g., `S3KeySensor`, `HttpSensor` - conceptual or simple practice)
    - [ ] Hooks (how operators interact with external systems)
    - [ ] XComs (for passing small amounts of data between tasks)
    - [ ] Task Dependencies (`>>`, `<<`, `set_upstream`, `set_downstream`)
    - [ ] Variables and Connections (manage them through Airflow UI)
    - [ ] Branching (`BranchPythonOperator`)
    - [ ] SLAs, Retries, Timeouts
- [ ] **Write Several DAGs:**
    - [ ] DAG 1: Run your containerized Python ETL script (from Week 2) using `DockerOperator`.
    - [ ] DAG 2: Orchestrate a PySpark job.
        - [ ] If Spark runs on EMR: A DAG to submit a step to an existing EMR cluster (`EmrAddStepsOperator`).
        - [ ] If Spark runs in Docker: A DAG to run a Spark container using `DockerOperator`.
    - [ ] DAG 3: A DAG with multiple tasks and dependencies (e.g., Task A (extract) -> Task B (transform) -> Task C (load)).
    - [ ] DAG 4 (Stretch): A DAG that uses a Sensor to wait for a file in S3 before proceeding.
- [ ] **Explore Airflow UI:** Monitoring DAG runs, viewing logs, triggering DAGs, clearing tasks, browsing code.

### 🎯 **Portfolio Project 1: Orchestrated Cloud ETL Pipeline (Est. 3 hours/day)**
- [ ] **Objective:** Take your Python ETL (loading to RDS/Redshift from Week 2) and fully orchestrate its execution using an Airflow DAG.
- [ ] If your ETL is containerized, use the `DockerOperator`. Ensure Airflow's Docker can communicate with your RDS/Redshift (networking).
- [ ] Implement robust scheduling, retries, and basic alerting (e.g., `on_failure_callback` to send an email or log to a specific place).
- [ ] Ensure this project is well-documented on GitHub (include Airflow DAG definitions, Dockerfiles, setup for Airflow).

### 🐍 **Python for Data Engineering Best Practices (Est. 1 hour/day)**
- [ ] Study and implement Idempotency in your ETL tasks (tasks can be rerun without side effects).
- [ ] Configuration management for different environments (dev, stage, prod - using environment variables, config files loaded by Airflow).
- [ ] Advanced logging strategies within Airflow tasks.

---

## Woche 5: Introduction to Streaming with Apache Kafka & Data Modeling

**Focus:** Get acquainted with real-time data concepts and solidify data modeling.

### 🌊 **Apache Kafka Fundamentals (Est. 4 hours/day)**
- [ ] **Core Kafka Concepts Study:**
    - [ ] Topics, Partitions, Replication Factor, In-Sync Replicas (ISRs)
    - [ ] Brokers, Zookeeper (or KRaft for newer versions)
    - [ ] Producers (acks, retries, idempotence)
    - [ ] Consumers, Consumer Groups, Offsets (commit strategies)
    - [ ] Message Keys & Partitioning
- [ ] **Setup Kafka:**
    - [ ] **Option 1 (Recommended):** Run Kafka locally using Docker Compose (e.g., Confluent Platform cp-all-in-one or Bitnami Kafka images).
    - [ ] **Option 2 (Cloud):** Use a managed Kafka service free tier (e.g., Confluent Cloud, Aiven, Upstash).
- [ ] **Practice with `kafka-python` (or other client library like `confluent-kafka-python`):**
    - [ ] Write a simple Kafka Producer in Python to send messages (e.g., JSON strings) to a topic.
    - [ ] Write a simple Kafka Consumer in Python to read messages from that topic and print them.
    - [ ] Experiment with different consumer group IDs.
- [ ] **Message Serialization:**
    - [ ] Understand pros/cons of JSON, Avro, Protobuf for Kafka messages.
    - [ ] (Stretch) Implement Avro serialization/deserialization with a schema registry (Confluent Schema Registry if using their platform).
- [ ] **Conceptual Understanding:** Use cases for Kafka in data engineering (event sourcing, real-time ETL, feeding stream processing systems, microservice communication).

### 🏗️ **Advanced Data Modeling & Data Warehousing (Est. 2 hours/day)**
- [ ] **Slowly Changing Dimensions (SCDs):**
    - [ ] Study Type 1, Type 2, Type 3, Type 6.
    - [ ] Implement a basic Type 2 SCD in your data warehouse (Redshift/PostgreSQL) for one dimension table. This involves adding effective/expiry dates or version numbers.
- [ ] **Fact Table Types:** Transactional, Periodic Snapshot, Accumulating Snapshot (understand differences and use cases).
- [ ] **Data Marts vs. Enterprise Data Warehouse.**
- [ ] **(Project Prep):** Start designing a more complex Star/Snowflake schema for Portfolio Project 2 (Mini Data Warehouse), incorporating an SCD.

### ☁️ **AWS Streaming Options (Awareness - Est. 1 hour/day)**
- [ ] Read about Amazon Kinesis:
    - [ ] Kinesis Data Streams (for custom real-time processing)
    - [ ] Kinesis Data Firehose (for loading streaming data to S3, Redshift, etc.)
    - [ ] Kinesis Data Analytics (for SQL/Flink on streams)
- [ ] Read about Amazon MSK (Managed Streaming for Apache Kafka).

### 🐳 **Docker Networking Deep Dive (Est. 1 hour/day)**
- [ ] Understand how containers communicate:
    - [ ] Default bridge network.
    - [ ] User-defined bridge networks (recommended for multi-container apps).
    - [ ] `host` network (use with caution).
    - [ ] `overlay` networks (for Docker Swarm/Kubernetes - conceptual).
- [ ] Practice connecting services defined in `docker-compose.yml` using their service names as hostnames.

---

## Woche 6: Mini Data Warehouse Project & Spark Optimizations

**Focus:** Build a more substantial data warehouse project, learn Spark tuning.

### 🎯 **Portfolio Project 2: Mini Data Warehouse with ETL & Spark (Est. 4 hours/day)**
- [ ] **Objective:** Design and implement a data warehouse (e.g., in Redshift or a well-tuned PostgreSQL) with a Star/Snowflake schema, including at least one SCD Type 2 dimension.
- [ ] **Data Sourcing:**
    - [ ] Use a public dataset or generate synthetic data.
    - [ ] Stage raw data in S3.
- [ ] **Processing:**
    - [ ] Use PySpark (running on EMR or local Docker setup) for complex transformations, joins, and aggregations to populate Dimension and Fact tables.
    - [ ] Implement logic for SCD Type 2 updates.
- [ ] **Loading:** Load processed data into Redshift/PostgreSQL.
- [ ] **Querying:** Write complex OLAP queries against your warehouse to derive insights.
- [ ] **Orchestration:** Orchestrate the entire loading process (S3 -> Spark -> DW) using an Apache Airflow DAG.
- [ ] **Documentation:** Thoroughly document the schema, ETL/ELT process, Spark job logic, and Airflow DAG on GitHub.

### 🔥 **Apache Spark Optimizations (Est. 2 hours/day)**
- [ ] **Understanding Spark UI:**
    - [ ] Navigate the Spark UI (Jobs, Stages, Tasks, Storage, Environment).
    - [ ] Identify bottlenecks: long-running tasks, data skew, shuffles.
- [ ] **Common Optimization Techniques (Study & Apply to Project 2):**
    - [ ] **Partitioning & Bucketing:** Understand how `repartition()`, `coalesce()`, and bucketing (writing data) can improve performance.
    - [ ] **Caching (`.cache()`, `.persist()`):** When and how to use it effectively.
    - [ ] **Broadcast Joins:** For joining large DataFrames with small ones.
    - [ ] **File Formats:** Using Parquet/ORC effectively.
    - [ ] **Predicate Pushdown.**
    - [ ] **Salting for Skewed Data (Conceptual understanding unless you encounter skew in your project).**
    - [ ] **SQL Optimizer (Catalyst):** Basic understanding of how Spark optimizes queries.
- [ ] **Practical:** Try to apply 1-2 relevant optimization techniques to your Spark jobs in Project 2 and observe performance changes (if possible).

### 🌊 **Kafka Connect (Awareness & Simple Exploration - Est. 1 hour/day)**
- [ ] Understand what Kafka Connect is and its distributed, fault-tolerant architecture.
- [ ] Role in easily streaming data from/to common data systems (Source Connectors, Sink Connectors).
- [ ] (If using Confluent Platform Docker) Explore running a simple pre-built connector like `FileStreamSourceConnector` or `FileStreamSinkConnector`.

### ⚙️ **CI/CD for Data Pipelines (Conceptual + Basic GitHub Actions - Est. 1 hour/day)**
- [ ] Understand the principles of CI (Continuous Integration) and CD (Continuous Deployment/Delivery) for data pipelines.
- [ ] **Setup GitHub Actions workflow for one of your Python projects:**
    - [ ] Trigger on push/pull_request to `main` branch.
    - [ ] Run `pylint` or `flake8` for code linting.
    - [ ] Run `pytest` unit tests.
    - [ ] (Stretch Goal) Build a Docker image and push to Docker Hub (or AWS ECR - Elastic Container Registry).

---

## Woche 7: Stream Processing Concepts & Building a Simple Streaming App

**Focus:** Apply Kafka knowledge to a basic stream processing scenario.

### 🌊 **Simple Stream Processing with Kafka & Python or Spark Streaming (Est. 4 hours/day)**
- [ ] **Option 1 (Python Consumer Logic - Simpler Start):**
    - [ ] Enhance your Kafka consumer from Week 5.
    - [ ] Implement stateful processing (e.g., count events per type within a time window, calculate a moving average of sensor readings).
    - [ ] Store results:
        - [ ] Write to another Kafka topic.
        - [ ] Update a database (e.g., Redis for counters, PostgreSQL for aggregated results).
        - [ ] Log to console/file.
    - [ ] Consider error handling and potential for message reprocessing.
- [ ] **Option 2 (Spark Structured Streaming - More Scalable, Steeper Curve):**
    - [ ] Learn basics of Spark Structured Streaming API (very similar to batch DataFrame API).
    - [ ] Read from a Kafka topic as a streaming DataFrame (`readStream`).
    - [ ] Perform transformations (e.g., filtering, adding columns).
    - [ ] Implement windowed aggregations (tumbling windows, sliding windows).
    - [ ] Handle late data (watermarking - conceptual or basic implementation).
    - [ ] Write output (`writeStream`) to:
        - [ ] Console sink (for debugging).
        - [ ] Parquet files on S3.
        - [ ] Another Kafka topic.
        - [ ] (Stretch) JDBC sink to a database.
- [ ] **Focus:** Understand at-least-once / at-most-once / exactly-once processing semantics (conceptual understanding, especially for Spark Streaming).

### 🐳 **Docker Best Practices & Security (Est. 2 hours/day)**
- [ ] **Multi-stage Docker builds:** Create smaller, more secure production images by separating build environment from runtime environment.
- [ ] **Minimize image layers.**
- [ ] **Use specific base images (e.g., `python:3.9-slim-buster` instead of `python:latest`).**
- [ ] **Run containers as non-root users.**
- [ ] **Docker image scanning for vulnerabilities:**
    - [ ] Use a tool like Trivy or Snyk (free tier) to scan one of your Docker images.
- [ ] **Managing secrets in Docker:**
    - [ ] Docker secrets (for Swarm/Kubernetes).
    - [ ] Environment variables (be cautious with sensitive data).
    - [ ] (Conceptual) Integrating with tools like HashiCorp Vault or AWS Secrets Manager.

### 🎯 **Refine Portfolio Projects (Est. 1 hour/day)**
- [ ] Review documentation (`README.md`s) for Project 1 & 2: clarity, completeness, setup instructions, architecture diagrams (simple ones are fine).
- [ ] Ensure code is clean, well-commented, and follows Python best practices.
- [ ] Test that projects are easily runnable by someone else following your instructions.

### ☁️ **AWS Serverless (Lambda - Introduction & Simple Use Case - Est. 1 hour/day)**
- [ ] Understand AWS Lambda core concepts (serverless, event-driven, pay-per-use).
- [ ] Supported runtimes, memory/timeout configurations.
- [ ] **Write a simple Lambda function in Python:**
    - [ ] Triggered by an S3 event (e.g., `s3:ObjectCreated:*`).
    - [ ] Example: Log metadata of the new S3 object, or copy it to another bucket.
- [ ] Understand IAM roles for Lambda functions.

---

## Woche 8: End-to-End Project, Interview Prep & Review

**Focus:** Consolidate learning into an impressive project, prepare for interviews.

### 🎯 **Capstone Project - Your Choice (Est. 4 hours/day)**
- [ ] **Objective:** Build an end-to-end project that showcases a combination of learned skills. Make it your most polished piece.
- [ ] **Option A: Advanced End-to-End Batch Pipeline:**
    - [ ] Data Ingestion (from API/S3) -> Staging in S3 -> Spark Processing (on EMR or Dockerized Spark) with optimizations -> Load to Data Warehouse (Redshift/PostgreSQL with SCDs) -> Orchestration with Airflow -> (Stretch) Basic Data Quality checks in pipeline -> (Stretch) Simple BI dashboard on top (e.g. Metabase, Google Data Studio pointing to DW).
- [ ] **Option B: Simple End-to-End Streaming Pipeline:**
    - [ ] Kafka Producer (simulating real-time events) -> Kafka Topic -> Stream Processor (Spark Structured Streaming or advanced Python consumer) performing transformations/aggregations -> Sink (e.g., aggregated data to PostgreSQL/Redis, alerts to another Kafka topic, raw/transformed stream to S3). Orchestrate producer/consumer deployment if possible (e.g. Docker Compose).
- [ ] **Option C: Deepen an Existing Project with Advanced Features:**
    - [ ] Take Project 1 or 2 and add:
        - [ ] Comprehensive automated testing (unit, integration).
        - [ ] Robust monitoring and alerting (e.g., Airflow alerts, custom metrics).
        - [ ] Data validation framework (e.g., Great Expectations - ambitious, or simpler custom checks).
        - [ ] Performance tuning and benchmarking.
- [ ] **Key:** Focus on a clean, well-documented, and demonstrable project.

### 🎤 **Interview Preparation (Est. 2 hours/day)**
- [ ] **Behavioral Questions:** Prepare stories using the STAR method (Situation, Task, Action, Result) for common questions (teamwork, challenges, failures, strengths, weaknesses).
- [ ] **Technical Explanation of Projects:** Practice explaining each of your portfolio projects in detail:
    - [ ] Problem statement & goals.
    - [ ] Architecture and technologies chosen (and *why*).
    - [ ] Challenges faced and how you overcame them.
    - [ ] Key learnings.
    - [ ] Potential improvements or next steps.
- [ ] **System Design Basics for Data Pipelines:**
    - [ ] Practice whiteboarding/discussing how to design common data pipelines (e.g., "Design an ETL pipeline to ingest customer orders and generate daily sales reports," "Design a system to track website clickstream data in real-time").
    - [ ] Consider scalability, reliability, cost, latency.
- [ ] **SQL & Python Review:** Go over common interview questions for SQL (joins, window functions, aggregations, subqueries) and Python (data structures, algorithms, OOP, specific library questions if relevant to your projects).

### 🛠️ **Tooling & DevOps Review (Est. 1 hour/day)**
- [ ] **Git:** Solidify understanding of branching strategies (e.g., Gitflow - conceptual understanding of its purpose). Practice creating PRs, reviewing code (even your own), and merging.
- [ ] **CI/CD:** Review your GitHub Actions setup. Understand how it automates testing/building.
- [ ] **Documentation:** Ensure all your projects on GitHub have excellent `README.md` files, including architecture diagrams (can be simple text-based or using a tool like diagrams.net/Excalidraw).

### ✨ **Final Polish & Next Steps (Est. 1 hour/day)**
- [ ] Update Resume & LinkedIn profile meticulously: highlight all new skills, tools, and detailed descriptions of your portfolio projects (quantify achievements if possible).
- [ ] Prepare a short "elevator pitch" about yourself and your data engineering interests.
- [ ] Plan your learning path *beyond* these 8 weeks (e.g., which technologies to dive deeper into: advanced Kubernetes, specific BI tools, MLOps, deeper cloud certifications).
- [ ] **Start applying for internships/entry-level roles!** Tailor your cover letter and resume for each application.

---

This is an extremely rigorous plan, Nav. Remember to take short breaks, stay hydrated, and don't burn out. The key is consistent, focused effort. You have the dedication, so make the most of these 8 weeks! Good luck!