# Building Decoupled Applications with AWS SQS and SNS

This project demonstrates how to design and implement a decoupled, event-driven
application architecture using AWS services such as Amazon S3, SNS, and SQS.

The project is based on a hands-on AWS guided lab and focuses on transforming
a tightly coupled application into a scalable, fault-tolerant system.

---

## 🧩 Project Overview

The application simulates an image upload workflow:

- Users upload images through a web interface
- Images are stored in Amazon S3
- S3 triggers an SNS notification on object creation
- SNS delivers messages to:
  - An SQS queue for asynchronous processing
  - An email subscriber for alerts
- The application server polls SQS and processes images independently

This design ensures the system remains operational even if one component fails.

---

## ☁️ AWS Services Used

- Amazon S3 – Image storage and event triggering
- Amazon SNS – Publish/subscribe notifications
- Amazon SQS – Message queue for decoupling components
- Amazon EC2 – Hosts the web and application servers
- Node.js – Application runtime


---

## 🏗 Architecture Phases

### Phase 1 – Tightly Coupled Architecture
- Web server communicates directly with application server
- Synchronous processing
- Application failure causes system downtime

### Phase 2 – Decoupled Architecture
- Asynchronous communication using SNS and SQS
- Improved scalability and fault tolerance
- Message persistence ensures reliable processing

---

## 📸 Screenshots

All implementation evidence is available in the `screenshots/` directory:
- S3 bucket policy configuration
- SNS topic creation
- SNS access policy
- S3 event notifications
- SNS email subscription

---

## 🎯 Key Learnings

- Decoupling improves availability and scalability
- Message queues prevent system-wide failures
- Event-driven architectures are resilient by design
- AWS managed services simplify distributed systems

---

## 📌 Conclusion

This project showcases how AWS SQS and SNS can be used together to build
reliable, loosely coupled cloud applications that scale efficiently and
handle failures gracefully.


# Phase 1 – Tightly Coupled Architecture

In this phase, the application followed a traditional tightly coupled design.

## Workflow
1. User uploads an image
2. Web server directly invokes the application server
3. Image is processed synchronously

## Limitations
- No fault tolerance
- Application server downtime breaks the system
- Poor scalability
- Tight dependency between components

This phase highlights why tightly coupled architectures are unsuitable
for modern cloud-native applications.


# Phase 2 – Decoupled Architecture Using AWS

This phase introduces an event-driven architecture using AWS managed services.

## Improvements Introduced
- Amazon SNS for notifications
- Amazon SQS for message queuing
- Asynchronous processing
- Independent scaling of components

The system remains operational even when the application server is unavailable.

# Decoupled Workflow

1. User uploads an image
2. Image is stored in Amazon S3
3. S3 triggers an SNS notification
4. SNS:
   - Publishes message to SQS queue
   - Sends email notification
5. Application server polls SQS
6. Image is processed asynchronously

Messages persist in SQS until successfully processed.


