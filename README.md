# Awesome-Data-Replication-Platform

# Top Data Replication Platforms Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**
*Focused on Change Data Capture, Real-Time Replication, Database Migration & Data Integration*
**Last updated: September 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Data Replication**. These tools help organizations capture changes from production databases in real time, replicate data across heterogeneous systems, and keep data warehouses, search indexes, and microservices in sync.

**Examples** include Qlik Replicate, Striim, HVR (Fivetran), Oracle GoldenGate, Debezium, SharePlex, Precisely Connect, Attunity Replicate, SymmetricDS, AWS DMS, Azure Data Factory, IBM InfoSphere CDC, PeerDB, and Hevo Data (the category leaders).

**Open-source emphasis**: Data replication has a **mature and production-proven open-source ecosystem**. **Debezium** is the de facto standard for log-based CDC, supporting MySQL, PostgreSQL, SQL Server, Oracle, and MongoDB, and is widely used in production at companies like Coupang and Woowa Brothers (Baemin) . **Flink CDC** provides streaming data integration with exactly-once semantics. **Sequin** offers Postgres-native CDC without requiring Kafka, positioning itself as a lighter alternative to Debezium . **SymmetricDS** delivers multi-master asynchronous replication with conflict management . This section documents these production-grade solutions.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Qlik Replicate](https://www.qlik.com/)**  
  Enterprise database replication (formerly Attunity Replicate, acquired by Qlik in 2019). Provides real-time CDC across heterogeneous environments with strong support for 30+ databases . Detailed transaction logging, audit trails, and hybrid deployment. **Best for**: Large organizations with complex multi-platform replication and strict governance requirements .

- **[Fivetran](https://www.fivetran.com/)**  
  Fully managed ELT platform with 300+ connectors. Automated schema drift handling, log-based replication, and minimal configuration . **Note**: Since January 2026, includes a $5 minimum per connection, bills deletes, and charges repeated updates in history mode . **Best for**: Analytics teams wanting managed warehouse ingestion with low operational overhead .

- **[Striim](https://www.striim.com/)**  
  Real-time data integration and streaming platform. Supports sub-60-second CDC latency and enterprise-grade governance . **Best for**: Enterprises requiring real-time operational analytics and hybrid cloud deployments.

- **[Oracle GoldenGate](https://www.oracle.com/)**  
  Enterprise replication with mature CDC capabilities. Best for Oracle-heavy environments with existing Oracle ecosystem investments .

- **[SharePlex](https://www.quest.com/)**  
  Oracle-focused replication and data integration platform. Provides real-time replication, data validation, and conflict resolution.

- **[AWS DMS](https://aws.amazon.com/dms/)**  
  AWS-native database migration and replication service. Supports heterogeneous migrations and continuous replication with CDC. Best for AWS-centric organizations .

- **[Azure Data Factory](https://azure.microsoft.com/en-us/products/data-factory)**  
  Azure-native data integration service with mapping data flows and CDC support. Best for Azure-centric data engineering teams.

- **[Precisely Connect](https://www.precisely.com/)**  
  Data integration and replication platform for mainframe and distributed systems. Provides CDC, data quality, and ETL capabilities.

- **[IBM InfoSphere CDC](https://www.ibm.com/)**  
  Enterprise CDC platform for heterogeneous replication. Provides field-level encryption and detailed audit trails .

- **[Hevo Data](https://hevodata.com/)**  
  Managed ELT platform with 150+ connectors. Near real-time replication with automated pipeline management .

## Open-Source GitHub Projects

### Kafka-Centric CDC Platforms

- **[Debezium](https://github.com/debezium/debezium)**  
  **The de facto standard for log-based change data capture.** Open-source distributed platform that captures changes from MySQL (binlog), PostgreSQL (logical decoding), SQL Server (CDC), Oracle, and MongoDB, publishing events into Kafka topics . **Built-in Outbox Event Router** for event-driven architectures . **Large community and ecosystem** with Kafka Connect integration. **At-least-once delivery** — duplicates can occur . **Production adoption**: Coupang uses Kafka + Debezium for order/inventory changes; Woowa Brothers (Baemin) and Kakao have published operational case studies . **Key tradeoff**: Requires Kafka infrastructure and engineering expertise — operational complexity is significant . **Apache-2.0**.

- **[Flink CDC](https://github.com/apache/flink-cdc)**  
  **Streaming data integration with exactly-once semantics.** Java-based, integrates with Apache Flink for real-time CDC pipelines. Supports MySQL, PostgreSQL, Oracle, MongoDB, and more . **Best for**: Teams already using Flink for stream processing.

### Postgres-Native CDC

- **[Sequin](https://github.com/sequinstream/sequin)**  
  **Postgres change data capture to streams and queues — no Kafka required.** **MIT licensed**, standalone Docker container . **Key features**: Logical replication slot to detect changes; **backfills** for existing rows; **SQL-based routing** to filter and route messages; supports **Kafka, SQS, Redis Streams, GCP Pub/Sub, Azure Event Hubs, NATS, RabbitMQ, Webhooks, and HTTP Pull** . **Transforms** (coming soon) in Lua, JavaScript, or Go. **Tested on YugabyteDB** — both live streaming and backfill worked with minimal changes . **Best for**: Postgres-centric teams wanting CDC without Kafka operational overhead.

- **[pglogical](https://github.com/2ndQuadrant/pglogical)**  
  **Logical replication extension for PostgreSQL 9.4–17.** Provides much faster replication than Slony, Bucardo, or Londiste, as well as cross-version upgrades . **Best for**: PostgreSQL-native logical replication without Kafka.

- **[pgcapture](https://github.com/replicase/pgcapture)**  
  **A scalable Netflix DBLog implementation for PostgreSQL.** Provides scalable real-time change data capture .

### Multi-Database & Enterprise CDC

- **[SymmetricDS](https://github.com/JumpMind/symmetric-ds)**  
  **Database replication and file synchronization — platform independent, web enabled, database agnostic.** Designed for **bi-directional data replication** across a large number of nodes, working near real-time across WAN and LAN networks . **Uses triggers** (not binlog) to capture updates, with conflict management built in . **Best for**: Multi-master asynchronous replication, POS systems, and distributed deployments requiring conflict resolution.

- **[Tungsten Replicator](https://github.com/continuent/tungsten-replicator)**  
  **Multi-master asynchronous replication for MySQL, PostgreSQL, and Oracle.** Open-source Replicator component with commercial enterprise options . Can run standalone or embedded in Java applications .

- **[OpenLogReplicator](https://github.com/bersler/OpenLogReplicator)**  
  **Open-source Oracle database CDC.** C++ based, provides Oracle redo log parsing for change data capture .

- **[Ape Data Transfer Suite (Ape-DTS)](https://github.com/apecloud/ape-dts)**  
  **Ultra-fast data replication written in Rust.** Supports MySQL, PostgreSQL, Redis, MongoDB, Kafka, and ClickHouse. Ideal for **disaster recovery (DR) and migration scenarios** .

- **[TiFlow (TiCDC + DM)](https://github.com/pingcap/tiflow)**  
  **Change data capture for TiDB and data migration platform.** Maintains DM (data migration) and TiCDC (change data capture for TiDB) .

### Additional Strong Open-Source Options

- **Kafka-Centric CDC**: **Debezium** (de facto standard, extensive connectors), **Flink CDC** (exactly-once, Flink integration) .
- **Postgres-Native**: **Sequin** (no Kafka, multi-sink), **pglogical** (fast logical replication), **pgcapture** (scalable Netflix DBLog) .
- **Multi-Database**: **SymmetricDS** (trigger-based, conflict management), **Tungsten Replicator** (MySQL/PostgreSQL/Oracle), **Ape-DTS** (Rust, multi-source) .
- **Oracle CDC**: **OpenLogReplicator** (redo log parsing) .
- **MySQL CDC**: **CanalSharp** (.NET client for Alibaba Canal), **MySqlCdc** (.NET binlog client) .

**Frameworks for building custom systems**: Combine **Debezium** for Kafka-based CDC with broad database support, **Sequin** for Postgres-native CDC without Kafka, **SymmetricDS** for multi-master replication with conflict resolution, **Flink CDC** for exactly-once streaming integration, and **Ape-DTS** for high-speed migration and disaster recovery. Add **Kafka** for event streaming, **PostgreSQL** for state storage, and **Docker** for deployment.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Data replication platforms handle sensitive production data; ensure proper access controls, encryption, and compliance with data protection regulations.
- **Open-source reality**: The open-source ecosystem for data replication is **mature and production-proven**. **Debezium** is the de facto standard for Kafka-based CDC, adopted at scale by Coupang, Woowa Brothers, and Kakao . **Sequin** provides a Kafka-free Postgres CDC alternative with multi-sink support . **SymmetricDS** delivers multi-master asynchronous replication with conflict management . **Flink CDC** offers exactly-once streaming integration . However, **commercial platforms** (Qlik Replicate, Fivetran, Striim, Oracle GoldenGate) provide **managed infrastructure, enterprise-grade monitoring, and dedicated support** that open-source alternatives require significant operational investment to match. The open-source path is **genuinely viable** for organizations with strong data engineering capacity, particularly for Kafka-centric architectures or Postgres-native CDC.
