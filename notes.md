
### 1. Introduction to MongoDB:

#### What is MongoDB?
MongoDB is a popular "NoSQL" database that uses a "document-oriented data model".
It stores data in flexible, JSON-like documents, meaning fields can vary from document to document and data structure can be changed over time.

#### Key Features:
- **Schema-less**: Unlike traditional SQL databases, MongoDB doesn't require a predefined schema.
- **Highly Scalable**: MongoDB can handle large volumes of data and scale horizontally across multiple servers.
- **Flexible Data Model**: Documents in MongoDB can hold arrays and other documents as values, making it very flexible.
- **Indexes**: Supports secondary indexes to improve query performance.
- **Replication & High Availability**: Offers replica sets for data redundancy and automatic failover.

#### Example Code:
```javascript
// Connect to MongoDB
const { MongoClient } = require('mongodb');
const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri, { useNewUrlParser: true, useUnifiedTopology: true });

async function run() {
    try {
        await client.connect();
        console.log("Connected to MongoDB");

        const database = client.db("myDB");
        const collection = database.collection("myCollection");

        // Insert a document
        await collection.insertOne({ name: "John Doe", age: 30 });

        // Query documents
        const result = await collection.findOne({ name: "John Doe" });
        console.log(result);
    } finally {
        await client.close();
    }
}

run().catch(console.error);
```

### SQL vs Mongodb(Nosql)
#### SQL:
- **Structured Query Language**: SQL databases use a structured query language to define and manipulate data.
- **Tables and Rows**: Data is stored in tables with rows and columns.
- **Fixed Schema**: Requires a predefined schema with a fixed structure.
- **EG**: MySQL, PostgreSQL, SQLitE , Oracle , SQL Server

#### NoSQL:
- **Document-Oriented**: MongoDB stores data in flexible, JSON-like documents.
- **Collections and Documents**: Data is stored in collections of documents.
- **Schema-less**: Does not require a predefined schema, allowing for flexible data models.
- **EG**: MongoDB, Couchbase, Cassandra, Redis

MongoDB offers several key features that make it a popular choice for developers and businesses:

1. **Document-Oriented**: MongoDB stores data in flexible, JSON-like documents called BSON (Binary JSON). This document-oriented model allows for the storage of heterogeneous data structures within a single collection, making it easier to represent complex relationships and hierarchical data.

2. **Schema Flexibility**: Unlike traditional relational databases, MongoDB does not require a predefined schema for data. Documents within a collection can have different fields and structures, providing greater flexibility in handling evolving data requirements and allowing for faster iteration in development.

3. **High Scalability**: MongoDB is designed to scale horizontally across multiple servers, making it well-suited for applications with growing data volumes and high throughput requirements. It supports automatic sharding, which distributes data across shards (partitions) in a cluster, enabling linear scalability.

4. **High Availability**: MongoDB provides built-in replication, allowing data to be replicated across multiple nodes within a cluster. In the event of node failure, MongoDB automatically promotes a secondary node to primary status, ensuring continuous availability and data durability.

5. **Rich Query Language**: MongoDB's query language offers powerful and expressive features for querying and manipulating data. It supports a wide range of query operators, including comparison, logical, array, and geospatial operators, making it versatile for various use cases.

6. **Indexing**: MongoDB supports various types of indexes, including single-field, compound, geospatial, and text indexes, to optimize query performance. Indexes can significantly improve the speed of read operations by allowing MongoDB to quickly locate documents matching query criteria.

7. **Aggregation Framework**: MongoDB provides a powerful aggregation framework for performing data aggregation operations, such as grouping, filtering, and transforming data. The aggregation pipeline allows for complex data processing tasks to be executed efficiently within the database.

8. **Ad Hoc Queries**: Developers can perform ad hoc queries on MongoDB using its query language without the need to define complex joins or adhere to rigid schemas. This flexibility simplifies development and allows for faster prototyping and iteration.

9. **Geospatial Capabilities**: MongoDB offers native support for geospatial indexing and querying, allowing developers to build location-aware applications that efficiently store and retrieve geospatial data, such as coordinates and polygons.

10. **Community and Ecosystem**: MongoDB benefits from a large and active community of developers, contributors, and users. It offers extensive documentation, tutorials, and resources, as well as official drivers and integrations for popular programming languages and frameworks, fostering rapid development and adoption.


10gen 
- MongoDB was developed by the company 10gen, which was later renamed to MongoDB Inc.
- The name "MongoDB" is derived from the word "humongous," reflecting the database's ability to handle large volumes of data.
### 2. NoSQL Vs SQL:

#### NoSQL:
- **Schema-less**: NoSQL databases like MongoDB do not require a fixed schema.
- **Horizontal Scalability**: Designed to scale out horizontally across multiple servers.
- **Flexible Data Models**: Can handle unstructured and semi-structured data efficiently.
- **Performance**: Typically offers better performance for certain use cases, like real-time analytics and high-volume web applications.

#### SQL:
- **Structured Data**: Relational databases like MySQL have a rigid schema with tables, rows, and columns.
- **ACID Transactions**: Offers strong consistency and ACID (Atomicity, Consistency, Isolation, Durability) transactions.
- **Joins**: Supports complex queries with JOIN operations, making it suitable for complex data relationships.
- **Maturity**: SQL databases have been around longer and are well-established in the industry.

#### Example Code (MySQL):
```sql
-- Create a table
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    age INT
);

-- Insert a record
INSERT INTO users (name, age) VALUES ('John Doe', 30);

-- Query records
SELECT * FROM users WHERE name = 'John Doe';
```

### 3. JSON Vs BSON:

#### JSON (JavaScript Object Notation):
- **Human-readable**: Easy for humans to read and write.
- **Text-based format**: Represents data in key-value pairs.
- **Lightweight**: Suitable for transmitting data between a server and a web application.
- **Supported by many programming languages**: Can be easily parsed and generated by most programming languages.

#### BSON (Binary JSON):
- **Binary format**: BSON is a binary-encoded serialization of JSON-like documents.
- **Efficient storage**: Being binary, BSON is more compact than JSON, making it more efficient for storage and data transfer.
- **Richer data types**: Supports additional data types like Date and Binary that are not natively supported in JSON.
- **Internal representation**: MongoDB stores data in BSON format internally.

#### Example Code (JSON):
```json
{
    "name": "John Doe",
    "age": 30,
    "address": {
        "city": "New York",
        "zipcode": "10001"
    }
}
```

#### Example Code (BSON):
```
\x16\x00\x00\x00                  // Total document size
\x02                               // Type String
name\x00                           // Field name
\x0C\x00\x00\x00John Doe\x00      // Field value
\x10\x00\x00\x00                   // Type Integer
age\x00                            // Field name
\x1E\x00\x00\x00                   // Field value (30)
\x03                               // Type Object
address\x00                        // Field name
\x26\x00\x00\x00                   // Embedded document size
\x02                               // Type String
city\x00                           // Field name
\x08\x00\x00\x00New York\x00       // Field value
\x10                               // Type String
zipcode\x00                        // Field name
\x05\x00\x00\x0010001\x00          // Field value
\x00                               // End of document
```

### 4. database, collection, document, field
DATABASE====>TABLE====>ROW====>COLUMN (SQL)
DATABASE====>COLLECTION====>DOCUMENT====>FIELD (nosql)



download-link: https://www.mongodb.com/try/download/community (community server)✅
download-link: https://www.mongodb.com/try/download/shell (shell)✅
download-link: https://www.mongodb.com/try/download/tools (compass)
