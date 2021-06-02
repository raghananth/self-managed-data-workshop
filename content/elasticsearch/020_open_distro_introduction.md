---
title: "Open Distro for Elasticsearch"
date: 2021-04-08T10:00:00-08:00
weight: 20
draft: false
---

### Elasticsearch 

[Elasticsearch](https://github.com/elastic/elasticsearch) is a distributed, document-oriented search and analytics engine. It supports structured and unstructured queries, and does not require a schema to be defined ahead of time. Elasticsearch can be used as a search engine, and is often used for web-scale log analytics, real-time application monitoring, and clickstream analytics.

### Open Distro for Elasticsearch

[Open Distro for Elasticsearch](https://opendistro.github.io/for-elasticsearch/) is a value-added distribution of Elasticsearch that is 100% open source (Apache 2.0 license) and supported by AWS. Open Distro for Elasticsearch leverages the open source code for Elasticsearch and Kibana. 

The first release includes Elasticsearch, Kibana, a set of advanced security, event monitoring & alerting, performance analysis, and SQL query features. In addition to the source code repo, Open Distro for Elasticsearch and Kibana are available as RPM and Docker containers, with separate downloads for the SQL JDBC and the PerfTop CLI. You can run this code on your laptop, in your data center, or in the cloud.

Deep dive into the features:

#### Elasticsearch

[Elasticsearch](https://opendistro.github.io/for-elasticsearch-docs/docs/elasticsearch/) is a distributed search and analytics engine based on Apache Lucene. After adding your data to Elasticsearch, you can perform full-text searches on it with all of the features you might expect: search by field, search multiple indices, boost fields, rank results by score, sort results by field, and aggregate results.

#### Kibana

[Kibana](https://opendistro.github.io/for-elasticsearch-docs/docs/kibana/) is the default visualization tool for data in Elasticsearch. It also serves as a user interface for the Open Distro for Elasticsearch security, alerting, and Index State Management plugins.

#### Security

The distribution has a [security plugin](https://opendistro.github.io/for-elasticsearch-docs/docs/security/) that supports node-to-node encryption, five types of authentication (basic, Active Directory, LDAP, Kerberos, and SAML), role-based access controls at multiple levels (clusters, indices, documents, and fields), audit logging, and cross-cluster search so that any node in a cluster can run search requests across other nodes in the cluster. 

#### Alerting

[Alerting](https://opendistro.github.io/for-elasticsearch-docs/docs/alerting/) notifies you when data from one or more Elasticsearch indices meets certain conditions. You could, for example, notify a Slack channel if an application logs more than five HTTP 503 errors in an hour. Monitoring is based on jobs that run on a defined schedule, checking indices against trigger conditions, and raising alerts when a condition has been triggered. 

#### Deep Performance Analysis

[Performance Analyzer](https://opendistro.github.io/for-elasticsearch-docs/docs/pa/) is a REST API that allows you to query a long list of performance metrics for your cluster. You can access the metrics programmatically or you can visualize them using PerfTop.

#### SQL Support

[Open Distro for Elasticsearch SQL](https://opendistro.github.io/for-elasticsearch-docs/docs/sql/) feature allows you to query your cluster using SQL statements rather than the Elasticsearch query domain-specific language (DSL). It is an improved version of the elasticsearch-sql plugin, and supports a rich set of statements.
