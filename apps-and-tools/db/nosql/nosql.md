# 📖 NoSQL

## kinds of NoSQL databases

- **Key-value stores**: these databases map key to a value, implementing a hash table. This data structure is also known as a dictionary. They are usually used to store information that needs quick access, for example, cache. 
  Examples: Redis, DynamoDB.
- **Wide-column stores**: these databases use tables and rows as relational databases. But the difference is that the format and names of columns might change from row to row in the wide-column store. They might be treated as two-dimensional key-value stores and are usually used for storing versatile objects. 
  Examples: BigTable, Apache HBase.
- **Document databases**: originally were created to store documents in XML format. But nowadays, they can work with different formats of data such as JSON, YAML, BSON, and others.
  Examples: MongoDB, Apache CouchDB.
- **Graph databases**: databases that operate with nodes and edges (relationships). They are used to represent data where the most important part is relationships between objects. Graph databases are very useful in identifying patterns in semi-structured and not structured data. 
  Examples: InfiniteGraph, Neo4j.

## BASE

In general, NoSQL databases follow BASE principles
Basically Available, Soft state,  Eventual consistency.
