# 🔒 LockSync - Distributed Locking System

## Overview

LockSync is a lightweight distributed locking service built using FastAPI that enables multiple distributed applications and services to safely coordinate access to shared resources.

In distributed environments, concurrent access to shared resources can lead to race conditions, data corruption, and inconsistent system states. LockSync solves this problem by providing a centralized lock management mechanism that allows clients to acquire, renew, release, and monitor locks in real time.

The project demonstrates concepts commonly used in distributed systems such as mutual exclusion, lock expiration, fault tolerance, lease-based locking, and resource coordination.

---

## Key Features

### Lock Acquisition

Clients can request exclusive access to a resource using a unique lock identifier.

### Lock Renewal

Active locks can be renewed before expiration to maintain ownership.

### Lock Release

Lock owners can voluntarily release locks when operations are completed.

### Time-To-Live (TTL)

Every lock is assigned an expiration time to prevent deadlocks caused by crashed or disconnected clients.

### Automatic Lock Cleanup

A background cleanup process automatically removes expired locks.

### RESTful API

Simple and scalable FastAPI endpoints for lock management operations.

### Interactive Swagger Documentation

Built-in API testing and documentation through Swagger UI.

### Fault-Tolerant Design

Prevents stale locks from blocking system operations.

### Extensible Architecture

Designed for future integration with databases, Redis, and distributed consensus algorithms.

---

## System Architecture

The LockSync system consists of four major components:

1. Client Applications
2. FastAPI Server
3. Lock Manager
4. Persistent Storage Layer (Future Enhancement)

### Request Flow

1. Client sends lock acquisition request.
2. Server forwards request to Lock Manager.
3. Lock Manager validates resource availability.
4. Lock is granted or rejected.
5. Lock metadata is stored in memory.
6. Cleanup service continuously removes expired locks.

---

## Technology Stack

* Python 3.12
* FastAPI
* Uvicorn
* Pydantic
* UUID
* Threading
* Swagger UI
* MongoDB (Planned)
* Redis (Planned)

---

## Project Structure

```text
LockSync/
│
├── src/
│   ├── lock_manager.py
│   ├── server.py
│   ├── database.py
│   └── models.py
│
├── docs/
│   └── architecture.png
│
├── screenshots/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Installation Guide

### Step 1: Clone Repository

```bash
git clone https://github.com/codebreaker939/LOcksync_sd
cd LockSync
```

### Step 2: Create Virtual Environment

```bash
python3 -m venv venv
```

### Step 3: Activate Virtual Environment

Mac/Linux:

```bash
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Application

Navigate to the source directory:

```bash
cd src
```

Start the FastAPI server:

```bash
uvicorn server:app --reload
```

Server will start on:

```text
http://127.0.0.1:8000
```

Swagger Documentation:

```text
http://127.0.0.1:8000/docs
```

ReDoc Documentation:

```text
http://127.0.0.1:8000/redoc
```

---

## API Endpoints

### Acquire Lock

```http
POST /acquire-lock
```

Request:

```json
{
  "resource_id": "database-record-1",
  "client_id": "client-123",
  "ttl": 30
}
```

---

### Renew Lock

```http
POST /renew-lock
```

Request:

```json
{
  "lock_id": "lock-uuid",
  "ttl": 30
}
```

---

### Release Lock

```http
POST /release-lock
```

Request:

```json
{
  "lock_id": "lock-uuid"
}
```

---

### View Active Locks

```http
GET /locks
```

---

## Example Use Cases

* Distributed Job Scheduling
* Microservices Coordination
* Database Migration Control
* Resource Allocation Systems
* Distributed Task Execution
* CI/CD Pipeline Synchronization
* Cloud Infrastructure Management

---

## Performance Characteristics

* O(1) Lock Lookup
* O(1) Lock Release
* Low Memory Overhead
* Fast Lock Acquisition
* Concurrent Client Support

---

## Future Enhancements

### Database Persistence

Store lock information in MongoDB or PostgreSQL.

### Redis Integration

Implement Redis-backed distributed locking.

### Raft Consensus Algorithm

Support leader election and distributed consensus.

### Multi-Node Deployment

Run LockSync across multiple servers.

### Kubernetes Deployment

Containerized deployment with auto-scaling.

### Monitoring & Metrics

Prometheus and Grafana integration.

### Authentication & Authorization

Secure API access using JWT tokens.

---

## Screenshots

Add screenshots of:

* Swagger UI
* Successful Lock Acquisition
* Lock Renewal
* Lock Release
* Active Lock Listing
* System Architecture Diagram

---

## Author

**Aniket Rai**

B.Tech Student | Full Stack Developer | Founder, BYT Solutions

LinkedIn: Add your LinkedIn profile here

GitHub: Add your GitHub repository link here

---

## License

This project is developed for educational and learning purposes and can be extended for production-grade distributed systems.
