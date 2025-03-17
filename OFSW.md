# Creating A Database with MongoDB

## Introduction

MongoDB is a popular NoSQL database that uses a document-based model to store data. It is designed for scalability, performance, and flexibility, making it ideal for handling large volumes of unstructured data. This guide provides a step-by-step approach to installing MongoDB, creating a database, performing operations, and troubleshooting common issues.

---

## Table of Contents

- [System Requirements](#system-requirements)
- [Safety Warnings](#safety-warnings)
- [Installing MongoDB](#installing-mongodb)
  - [On Windows](#on-windows)
  - [On Mac](#on-mac)
- [Configuring MongoDB](#configuring-mongodb)
- [Creating a Database](#creating-a-database)
- [Basic Operations (CRUD)](#basic-operations-crud)
- [Common Errors & Fixes](#Common-Errors--Fixes)
- [Backing Up and Restoring](#backing-up-and-restoring)
- [Appendix](#appendix)

---

## System Requirements

Before installing MongoDB, ensure your system meets the following requirements:

### **Operating Systems:**
- Windows 10 or later
- macOS 10.11 or later
- Linux (Ubuntu 18.04, CentOS 7, or later)

### **Hardware:**
- Minimum of 2GB RAM
- At least 2GB of free disk space
- Processor: MongoDB 5.0 requires use of the AVX instruction set, available on [select Intel and AMD processors.](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions#CPUs_with_AVX)

### **Software:**
- Node.js (for Node.js applications)
- MongoDB version 5.0 or later

---

## Safety Warnings

Before proceeding with MongoDB installation and setup, consider these precautions:

⚠️ **Backup Your Data:** Before making changes to an existing database, create backups using `mongodump`.

⚠️ **Secure Your Database:** MongoDB does not enable authentication by default. Ensure you configure access control.

⚠️ **Avoid Running as Root:** Running MongoDB as a root user can pose security risks. Use a dedicated user account.

---

## Installing MongoDB

### **On Windows**

1. **Download MongoDB:**  
   - Visit the [MongoDB Download Page](https://www.mongodb.com/try/download/community).  
   - Select **MSI Installer**.

2. **Run the Installer:**  
   - Follow the intruction wizard. During Installation, choose **Complete** to install all necessary components.
   - Ensure **Install MongoDB as a Service** is checked.
   - Once Installation is complete, MongoDB will run automatically as a service.

3. **Verify Installation:**
   - Open Command Prompt (CMD) and type:
   ```sh
   mongo --version
   ```
  - This should return the installed version of MongoDB.
    
### **On Mac**

1. **Install Homebrew (if not installed):**
   - Open the terminal and run:
   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install MongoDB:**
   - Use homebrew to install MongoDB by running:
   ```sh
   brew tap mongodb/brew
   brew install mongodb-community@5.0
   ```

3. **Verify Installation:**
   - Check that MongoDB was installed by typing:
   ```sh
   mongo --version
   ```

---

## Configuring MongoDB

### **Starting the MongoDB Service**

#### **On Windows:**
The MongoDB Service will begin automatically with the system. If needed, you can manually start the service by typing this command into your CMD:
```sh
net start mongodb
```

#### **Mac/Linux:**
To start MongoDB, run:
```sh
sudo systemctl start mongod
```
You can confirm that the MongoDB service is running by typing:
```sh
sudo systemctl start mongod
```
**Connecting:** To connect to MongoDB, open a new CMD or Terminal window and type:
```sh
mongo
```

**Disconnecting:** To exit MongoDB shell, type:
```sh
exit
```

---

## Creating a Database

Once connected to MongoDB:

1. **Create a new database:**
   ```sh
   use myNewDatabase
   ```

2. **Verify creation:**
   ```sh
   show databases
   ```

---

## Basic Operations (CRUD)

### **Create a Document**
```sh
db.users.insertOne({ name: "John Doe", age: 30 })
```

### **Read Data**
```sh
db.users.find({ name: "John Doe" })
```

### **Update a Document**
```sh
db.users.updateOne({ name: "John Doe" }, { $set: { age: 31 } })
```

### **Delete a Document**
```sh
db.users.deleteOne({ name: "John Doe" })
```

---

## Common Errors & Fixes

### **Error 1: MongoDB Service Not Starting**  
**Fix:** Check logs with:  
```sh
sudo journalctl -u mongod --no-pager
```

### **Error 2: "Connection Refused" Error**  
**Fix:** Ensure MongoDB is running:
```sh
sudo systemctl status mongod
```

### **Error 3: Authentication Failure**  
**Fix:** Enable authentication in `mongod.conf`.

---

## Backing Up and Restoring

### **Backing Up a Database**
```sh
mongodump --db=myNewDatabase --out=/backup/directory/
```

### **Restoring a Database**
```sh
mongorestore --db=myNewDatabase /backup/directory/myNewDatabase/
```

---

## Appendix

For more information, visit the official [MongoDB Documentation](https://www.mongodb.com/docs/manual/).
