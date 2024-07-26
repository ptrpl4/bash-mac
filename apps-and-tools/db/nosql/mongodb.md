# MongoDB

MongoDB is a schema-less DB that uses flexible "key-value" pairs, called documents for data storage.

- All data in MongoDB is stored as JSON documents (though technically, in **b**inary J**SON** format – **BSON**) grouped by collections.
- Documents in the same collection may have different fields. One document can have fields of different data types, the data does not need to be reduced to the same type.
- The data model in MongoDB allows easily represent complex hierarchical structures as well as store arrays.
- MongoDB is intentionally developed as a highly scalable and fault-tolerant database for large amounts of data. To achieve it, MongoDB should be run in a cluster environment where several connected databases work together.

limitations:
- MongoDB does not support unification, so depending on how often you want to get access to your data, you should probably update your documents on the regular basis.
- This DB structure tends to be memory-consuming due to the "key-value" pairs, which could lead to excessive data.
- Documents are limited to 16 MB.
- As ACID (atomicity, consistency, isolation, durability) principles are not strictly followed in the NoSQL management system, complicated transactions could become even more complex.

#### Links

- [https://docs.mongodb.com/manual/tutorial/query-documents/](https://docs.mongodb.com/manual/tutorial/query-documents/) - query
- [https://www.mongodb.com/products/compass](https://www.mongodb.com/products/compass) - GUI tool
