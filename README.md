
<h1 align="center">Hi 👋, I'm Jeshwin William James</h1>

<h3 align="center">
Backend Engineer | Distributed Systems | Kafka | Spring Boot | AWS | Kubernetes
</h3>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=30&pause=1000&color=00F7FF&center=true&vCenter=true&width=900&lines=Backend+Engineer;Distributed+Systems+Engineer;Kafka+%7C+Spring+Boot+%7C+AWS;Building+Scalable+Cloud-Native+Systems" />
</p>

---

# 💫 About Me

Software Engineer with 3+ years of experience building scalable distributed systems, event-driven microservices, and cloud-native backend applications.

Specialized in:

- Java
- Spring Boot
- Kafka
- Distributed Systems
- AWS & Kubernetes
- High-Throughput Backend Systems

Currently focused on low-latency services, event-driven architectures, and scalable microservices deployed on cloud-native infrastructure.

---

# 🚀 What I Do

- Build distributed event-driven systems
- Design scalable microservices architectures
- Develop high-throughput backend services
- Optimize performance & reduce latency
- Deploy cloud-native applications
- Work with Kafka-based async processing

---

# 🧠 Areas of Interest

- Distributed Systems
- System Design
- Event-Driven Architecture
- Microservices Architecture
- High-Throughput Backend Services
- Cloud-Native Applications
- Performance Optimization

---

# ⚡ Technologies

<p align="left">

<img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white"/>

<img src="https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=springboot"/>

<img src="https://img.shields.io/badge/Kafka-000000?style=for-the-badge&logo=apachekafka"/>

<img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws"/>

<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker"/>

<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes"/>

<img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql"/>

<img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis"/>

<img src="https://img.shields.io/badge/Cassandra-1287B1?style=for-the-badge&logo=apachecassandra"/>

<img src="https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins"/>

</p>

---

# 🏗 Distributed Event Processing Architecture

```mermaid
flowchart TB

    Client[Client Applications]

    subgraph Edge
        LB[Load Balancer]
        APIGW[API Gateway]
    end

    subgraph Services
        Auth[Auth Service]
        Order[Order Service]
        Payment[Payment Service]
        Inventory[Inventory Service]
        Notification[Notification Service]
    end

    subgraph Messaging
        Kafka[(Apache Kafka)]
    end

    subgraph Data
        PG[(PostgreSQL)]
        Redis[(Redis Cache)]
        Cassandra[(Cassandra)]
    end

    subgraph Observability
        Prometheus[Prometheus]
        Grafana[Grafana]
        ELK[ELK Stack]
    end

    Client --> LB
    LB --> APIGW

    APIGW --> Auth
    APIGW --> Order
    APIGW --> Payment
    APIGW --> Inventory

    Order --> Kafka
    Payment --> Kafka
    Inventory --> Kafka

    Kafka --> Notification
    Kafka --> Inventory
    Kafka --> Payment

    Auth --> Redis
    Order --> PG
    Payment --> PG
    Inventory --> Cassandra

    Auth --> Prometheus
    Order --> Prometheus
    Payment --> Prometheus
    Inventory --> Prometheus

    Prometheus --> Grafana

    Auth --> ELK
    Order --> ELK
    Payment --> ELK
    Inventory --> ELK
```

---

# ☁️ Cloud-Native Deployment Architecture

```mermaid
flowchart LR

    User --> CloudFront
    CloudFront --> ALB

    ALB --> K8S[Kubernetes Cluster]

    subgraph Kubernetes
        ServiceA[Spring Boot Service A]
        ServiceB[Spring Boot Service B]
        ServiceC[Kafka Consumer]
    end

    K8S --> Kafka[(Apache Kafka)]
    K8S --> RDS[(AWS RDS)]
    K8S --> Redis[(Elasticache)]

    K8S --> Prometheus[Prometheus]
    Prometheus --> Grafana[Grafana]
```

---

# 💼 Experience

## Software Engineer — State Street

- Built low-latency Spring Boot microservices for financial transaction processing
- Designed Kafka-based event-driven reconciliation pipelines
- Optimized database queries improving throughput
- Deployed containerized services using Docker & Kubernetes

---

## Software Engineer — Accenture (Client: Flipkart)

- Developed high-traffic checkout microservices used by millions
- Implemented Kafka-based asynchronous processing pipelines
- Improved payment success rate and reduced API latency
- Built scalable cloud-native microservices architecture

---

# 🚀 Featured Projects

## Distributed Event Processing System

Scalable microservices backend system using Kafka and Spring Boot for real-time event processing.

### Tech Stack

Java • Spring Boot • Kafka • PostgreSQL • Docker

---

## Mobile Payment Security System

Device authentication framework using IMEI verification for secure mobile payments.

### Tech Stack

Java • Spring Boot • REST APIs • MySQL

---

# 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=jeshwinwilliam&show_icons=true&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=jeshwinwilliam&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=jeshwinwilliam&layout=compact&theme=tokyonight" />
</p>

---

# 🎓 Education

## MS in Computer Science
Oklahoma City University

## B.Tech in Computer Science
Hindustan Institute of Technology & Science

---

# 🏆 Certifications

- AWS Certified Solutions Architect – Associate

---

# 📫 Connect With Me

<p align="left">

<a href="mailto:jeshwin.w.james@gmail.com">
  <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
</a>

<a href="https://linkedin.com/in/jeshwin-william-james-33a83b1a9">
  <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>

<a href="https://github.com/jeshwinwilliam">
  <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"/>
</a>

</p>

---

<p align="center">
⚡ Focused on building scalable infrastructure, distributed systems, and production-grade backend services.
</p>
