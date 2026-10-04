## Overview

MongoDB stores BSON documents in collections. Its flexible document model suits aggregates that are commonly read and written together, but schema design still needs explicit constraints and access-pattern thinking.

## Modeling

Embed related data when it has bounded size, is owned by the parent, and is commonly accessed together. Reference documents for independently growing, shared, or separately queried entities. MongoDB document size is limited, so unbounded embedded arrays are a warning sign.

## Indexes and Queries

MongoDB supports single-field, compound, multikey (array), text, and other index types. Compound indexes also follow a prefix principle; order fields for measured query/sort patterns. Use `explain()` to compare keys/documents examined with returned results.

## Aggregation, Consistency, and Scale

The aggregation pipeline transforms documents through stages such as `$match`, `$group`, `$project`, and `$sort`; put selective `$match` early. Replica sets provide redundancy and replication. Read/write concerns select acknowledgement and read-consistency behavior. Transactions exist for multi-document atomicity but should not replace good aggregate design. Sharding partitions collections across nodes and requires a carefully chosen shard key.

## Interview Takeaway

MongoDB schema design begins with access patterns. Choose embed vs reference intentionally, index the actual queries, and understand replica/shard trade-offs.

```table-of-contents
```
