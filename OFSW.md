# Creating A Database with MongoDB

## Introduction

MongoDB is a popular NoSQL database that uses a document-based model to store data. It is designed for scalability, performance, and flexibility, making it ideal for handling large volumes of unstructured data. In this step-by-step guide, you will learn how to install MongoDB for the first time, create a database, and perform basic operations.

## Table of Contents

- [System Requirements](#system-requirements)
- [Installing MongoDB](#installing-mongodb)
  - [On Windows](#on-windows)
  - [On Mac](#on-mac)
- [Starting MongoDB](#starting-mongodb)
- [Creating a MongoDB Database](#creating-a-mongodb-database)
- [Creating a Collection in MongoDB](#creating-a-collection-in-mongodb)
- [Performing CRUD Operations](#performing-crud-operations)
- [Backing Up and Restoring Databases](#backing-up-and-restoring-databases)
- [Working with MongoDB in Applications](#working-with-mongodb-in-applications)
- [Appendix](#appendix)

---

## System Requirements

Before installing MongoDB onto your system, ensure the system meets the following requirements.

### Operating Systems:

- Windows 10 or higher  
- macOS 10.11 or higher  
- Linux (Ubuntu 18.04, CentOS 7 or later)

### Hardware:

- Minimum of 2GB of RAM  
- At least 2GB of free disk space  
- Processor: MongoDB 5.0 requires use of the AVX instruction set, available on select Intel and AMD processors.

### Software:

- Node.js (if you are using MongoDB with Node.js)  
- MongoDB version 5.0 or later

---

## Installing MongoDB

### On Windows

1. **Download MongoDB**:
   - Visit the official [MongoDB Download](https://www.mongodb.com/try/download/community) page.
   - Select "MSI" as the installer type for Windows.

2. **Run the Installer**:
   - Follow the installation wizard. Choose **Complete** to install all components.
   - Check the **Install MongoDB as a Service** box.
   - MongoDB will start automatically as a service after installation.

3. **Verify Installation**:
   - Open Command Prompt and run:
     
     ```bash
     mongo --version
     ```
   
   - This returns the installed MongoDB version.

### On Mac

1. **Install Homebrew** (if not installed):
   
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install MongoDB**:
   
   ```bash
   brew tap mongodb/brew
   brew install mongodb-community@5.0
   ```

3. **Verify Installation**:
   
   ```bash
   mongo --version
   ```

---

## Starting MongoDB

### On Windows

MongoDB runs automatically as a service. To manually start it:

```bash
net start mongodb
```

### On Mac/Linux

Start MongoDB with:

```bash
sudo systemctl start mongod
```

Verify it’s running:

```bash
ps aux | grep mongod
```

Connect to MongoDB Shell:

```bash
mongo
```

Disconnect:

```bash
exit
```

---

## Creating a MongoDB Database

Access MongoDB Shell:

```bash
mongo
```

Create a Database:

```bash
use myNewDatabase
```

Verify Creation:

```bash
show databases
```

---

## Creating a Collection in MongoDB

Insert a Document (creates the collection automatically):

```javascript
db.myCollection.insertOne({ name: "John Doe", age: 30, profession: "Developer" })
```

View the Collection:

```javascript
db.myCollection.find()
```

---

## Performing CRUD Operations

### Create

```javascript
db.myCollection.insertOne({ name: "Jane Doe", age: 28, profession: "Designer" })
```

### Read

```javascript
db.myCollection.find({ name: "John Doe" })
```

### Update

```javascript
db.myCollection.updateOne({ name: "John Doe" }, { $set: { age: 31 } })
```

### Delete

```javascript
db.myCollection.deleteOne({ name: "Jane Doe" })
```

---

## Backing Up and Restoring Databases

### Backing Up

Use `mongodump` to export data:

```bash
mongodump --db=myNewDatabase --out=/backup/directory/
```

### Restoring

Use `mongorestore` to import data:

```bash
mongorestore --db=myNewDatabase /backup/directory/myNewDatabase/
```

---

## Working with MongoDB in Applications

### Node.js Example

#### Install the MongoDB Driver

```bash
npm install mongodb
```

#### Connect and Insert Data

```javascript
const { MongoClient } = require('mongodb');
const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function run() {
  try {
    await client.connect();
    const db = client.db("myNewDatabase");
    const collection = db.collection("myCollection");
    await collection.insertOne({ name: "Alice", age: 25 });
  } finally {
    await client.close();
  }
}

run().catch(console.dir);
```

---

## Appendix

For detailed documentation, visit the official [MongoDB Documentation](https://www.mongodb.com/docs/manual/).
