# MongoDB Installation and Setup Guide

## Introduction

MongoDB is a widely used NoSQL database that stores data in a flexible, document-based format. It is designed to provide scalability, high performance, and high availability. This guide will walk you through the steps required to install MongoDB, create a database, and perform basic operations. 

## Table of Contents
- [System Requirements](#system-requirements)
- [Installing MongoDB](#installing-mongodb)
  - [On Windows](#on-windows)
  - [On Mac](#on-mac)
- [Starting MongoDB](#starting-mongodb)
- [Creating a MongoDB Database](#creating-a-mongodb-database)
- [Creating a Collection in MongoDB](#creating-a-collection-in-mongodb)
- [Performing CRUD Operations](#performing-crud-operations)
- [Additional Features](#additional-features)
- [Appendix](#appendix)

## System Requirements

Before installing MongoDB, ensure that your system meets the following requirements:

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

## Installing MongoDB

### On Windows

1. **Download MongoDB:**
   - Visit the official MongoDB website: [MongoDB Download Center](https://www.mongodb.com/try/download/community)
   - Select "MSI" as the installer type for Windows.

2. **Run the Installer:**
   - Follow the installation wizard. Choose "Complete" to install all necessary components.
   - Ensure to check the "Install MongoDB as a Service" box.
   - Once the installation is complete, MongoDB will run automatically as a service.

3. **Verify Installation:**
   - Open Command Prompt (CMD) and type the following:
   ```bash
   mongo --version
