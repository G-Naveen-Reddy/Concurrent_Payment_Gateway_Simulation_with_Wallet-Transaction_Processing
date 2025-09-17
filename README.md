# Concurrent Payment Gateway Simulation with Wallet & Transaction Processing

Languages / Tech: Java (OOP, concurrency), suggested infra: PostgreSQL/MySQL (wallet & transaction persistence), Optional: Redis (cache), Kafka/RabbitMQ (async notifications), Spring Boot (REST API)

Project Summary : 

A production-oriented payment gateway simulation that supports multiple payment methods (Wallet, Card, UPI), concurrent transaction processing, transaction status tracking, and wallet management. Integrates seamlessly with Notification System for OTPs, payment alerts, and confirmations. Designed for fintech/payment applications like Juspay.

Key Impacts : 

1. Supports 1,000+ transactions per minute with concurrency-safe wallet operations.
2. Tracks transaction status: PENDING, SUCCESS, FAILED for reliability and analytics.
3. Demonstrates thread-safe operations to avoid double-spend or wallet inconsistencies.
4. Easily extensible for multiple payment channels, retry mechanisms, and reporting.


Architecture Diagram (Mermaid) :

flowchart LR
  User[Client / App] --> Gateway[Payment Gateway]
  Gateway --> Auth[Transaction Auth Service]
  Gateway --> Wallet[Wallet Service]
  Auth --> DB[(Transaction DB)]
  Wallet --> DB
  Gateway --> MQ[(Notification Queue)]
  MQ --> NotificationWorker[Notification System]

<img width="3840" height="1378" alt="Payment Gateway_System design" src="https://github.com/user-attachments/assets/f849f358-3c45-4114-b22a-0b48749f999b" />


Design Highlights : 

1. Payment flow: User → Gateway → Auth → Wallet → Notification
2. Multi-channel payments: Wallet, Card, UPI simulated via separate methods.
3. Thread-safe wallet updates: Prevents double-spend in concurrent transactions.
4. Transaction status tracking: PENDING, SUCCESS, FAILED with timestamps.
5. Integration-ready: Can easily integrate the Notification System for alerts/OTP.
6. OOP design: Classes for User, Wallet, Transaction, Gateway, AuthService.
7. Metrics & observability: Tracks transactions per minute, success rate, and failed transactions.


How to Use / Run (Local Demo)
1. Clone the repo.
2. Compile and run PaymentGatewayDemo.java in src.
3. The demo simulates multiple users performing concurrent transactions with different payment methods.
4. For production-ready use, add:
    -> Persistent storage (PostgreSQL/MySQL) for wallet balances and transactions.
    -> Distributed queue (Kafka/RabbitMQ) for async notifications.
    -> REST API wrapper (Spring Boot) for real-world endpoints.
    -> Retry mechanism for failed transactions.


Future Enhancements : 

1. Persistent storage – save transactions and wallet balances in PostgreSQL/MySQL.
2. Distributed transaction queue – integrate Kafka/RabbitMQ for high throughput.
3. Retry mechanism – automatically retry failed transactions.
4. Notification integration – use Notification System for OTPs or transaction alerts.
5. REST API endpoints – expose /pay and /wallet endpoints via Spring Boot.
6. Scheduling – support delayed payments or recurring transactions.
7. Enhanced metrics & monitoring – throughput, latency, success/failure rates.
8. Fraud detection / limits – prevent double-spend or abnormal transactions.
