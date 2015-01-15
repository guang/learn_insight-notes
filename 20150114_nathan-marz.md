1/14/2015 Wednesday
=============================
Chat with Nathan Marz

## Data Engineering Roles/Responsibility
Two main responsibilities:
- Product (workflow, infrastructure)
- Exploratory (ad-hoc analysis)

Schemaless is shitty (due to human errors and such)
- use tools like thrift to impose schemas

Compaction and garbage cleaning behave similar to partitions

## Data Engineering Projects
Important considerations for project (and in general):
- scalability
- robustness (machine/human tolerance)
- data schemas: what the data should look like

Two options:
- (product first) build a product (like twitter) to understand the full stack kinda
- (data first) build on data

Data science asks adhoc questions that requires one time computations, whereas data
engineering are constantly processing information.

It is important to know not only how to build it but how to *break the system* you build

Helpful/interesting for data engineering projects
- interesting transformation/indexing to support on-going queries
- fraud prevention
- diversity in query types
- subscription? not just reading data in but sending alerts to many users

## Complicated vs Complex
- complicated means more pieces
- complex implies interwined functionalities

try to avoid complexity :trollface:
