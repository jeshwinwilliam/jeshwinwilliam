
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,100:00F7FF&height=180&section=header&text=Jeshwin%20William%20James&fontSize=40&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Backend%20Engineer%20%7C%20Distributed%20Systems%20%7C%20Kafka%20%7C%20Spring%20Boot%20%7C%20AWS&descAlignY=58&descSize=18" width="100%"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=28&pause=1000&color=00F7FF&center=true&vCenter=true&width=900&lines=Backend+Engineer;Distributed+Systems+Engineer;Kafka+%7C+Spring+Boot+%7C+AWS;Building+Scalable+Cloud-Native+Systems" />
</p>

<p align="center">
  <a href="mailto:jeshwin.w.james@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
  <a href="https://linkedin.com/in/jeshwin-william-james-33a83b1a9"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://github.com/jeshwinwilliam"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

---

## 💫 About Me

Software Engineer with 3+ years of experience building **scalable distributed systems**, **event-driven microservices**, and **cloud-native backend applications**.

- 🔭 Currently building low-latency, event-driven services on cloud-native infrastructure
- 🌱 Deepening expertise in distributed consensus, CQRS, and streaming architectures
- 💬 Ask me about Kafka internals, Spring Boot performance tuning, or Kubernetes scaling
- ⚡ Fun fact: I think in sequence diagrams

---

## ⚡ Tech Stack

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
<img src="https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white"/>
<img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white"/>
</p>

---

## 🏗 System Architecture — Distributed Event Processing Platform

A reference architecture reflecting the kind of systems I design and build: request path, async event backbone, storage-per-service, and full observability.

```mermaid
flowchart TB
    Client[Client Applications]

    subgraph Edge["Edge Layer"]
        LB[Load Balancer]
        APIGW[API Gateway<br/>Rate Limiting · AuthN]
    end

    subgraph Services["Service Layer"]
        Auth[Auth Service]
        Order[Order Service]
        Payment[Payment Service]
        Inventory[Inventory Service]
        Notification[Notification Service]
    end

    subgraph Messaging["Event Backbone"]
        Kafka[(Apache Kafka<br/>Partitioned Topics)]
        DLQ[(Dead Letter Queue)]
    end

    subgraph Data["Storage — Database per Service"]
        PG[(PostgreSQL<br/>Orders / Payments)]
        Redis[(Redis<br/>Session & Cache)]
        Cassandra[(Cassandra<br/>Inventory — high write)]
    end

    subgraph Observability["Observability Stack"]
        Prometheus[Prometheus]
        Grafana[Grafana]
        ELK[ELK Stack]
        Tracing[Distributed Tracing<br/>OpenTelemetry]
    end

    Client --> LB --> APIGW
    APIGW --> Auth
    APIGW --> Order
    APIGW --> Payment
    APIGW --> Inventory

    Order -- OrderCreated --> Kafka
    Payment -- PaymentProcessed --> Kafka
    Inventory -- StockReserved --> Kafka
    Kafka -- consume --> Notification
    Kafka -- consume --> Inventory
    Kafka -- consume --> Payment
    Kafka -. failed events .-> DLQ

    Auth --> Redis
    Order --> PG
    Payment --> PG
    Inventory --> Cassandra

    Auth & Order & Payment & Inventory --> Prometheus
    Auth & Order & Payment & Inventory --> ELK
    Auth & Order & Payment & Inventory --> Tracing
    Prometheus --> Grafana
```

**Design decisions worth calling out:**

| Concern | Approach | Why |
|---|---|---|
| Service coupling | Kafka as async backbone instead of sync REST chains | Decouples producers/consumers, absorbs traffic spikes, enables replay |
| Data ownership | Database-per-service (PG, Cassandra, Redis) | Avoids shared-schema coupling; each store matches its access pattern |
| Failure handling | Dead-letter queues + retry topics | Poison messages don't block partition consumers |
| Consistency | Eventual consistency via event choreography, sagas for multi-step transactions | Avoids distributed locks; each service stays autonomous |
| Observability | Metrics (Prometheus), logs (ELK), traces (OTel) per service | Root-causing latency across service boundaries |

---

## ☁️ Cloud-Native Deployment Architecture

```mermaid
flowchart LR
    User --> CloudFront[CloudFront CDN]
    CloudFront --> ALB[Application Load Balancer]
    ALB --> K8S[Kubernetes Cluster — EKS]

    subgraph K8S_Internal["Inside the Cluster"]
        HPA[Horizontal Pod Autoscaler]
        ServiceA[Spring Boot Service A]
        ServiceB[Spring Boot Service B]
        ServiceC[Kafka Consumer Pods]
        HPA -.scales.-> ServiceA
        HPA -.scales.-> ServiceB
        HPA -.scales.-> ServiceC
    end

    K8S --> Kafka[(MSK / Apache Kafka)]
    K8S --> RDS[(AWS RDS — Multi-AZ)]
    K8S --> Elasticache[(Elasticache Redis)]

    K8S --> Prometheus --> Grafana
    K8S --> Secrets[AWS Secrets Manager]
    K8S --> IAM[IAM Roles for Service Accounts]
```

**Infra notes:** GitOps-style deploys, HPA driven by custom Kafka-consumer-lag metrics rather than just CPU, and IRSA for least-privilege pod-level AWS access.

---

## 💼 Experience

**Software Engineer — State Street**
- Built low-latency Spring Boot microservices for financial transaction processing
- Designed Kafka-based event-driven reconciliation pipelines
- Optimized database queries, improving throughput
- Deployed containerized services using Docker & Kubernetes

**Software Engineer — Accenture** *(Client: Flipkart)*
- Developed high-traffic checkout microservices used by millions
- Implemented Kafka-based asynchronous processing pipelines
- Improved payment success rate and reduced API latency
- Built scalable cloud-native microservices architecture

---

## 🚀 Featured Projects

### Distributed Event Processing System
Scalable microservices backend using Kafka and Spring Boot for real-time event processing.
`Java` `Spring Boot` `Kafka` `PostgreSQL` `Docker`

### Mobile Payment Security System
Device authentication framework using IMEI verification for secure mobile payments.
`Java` `Spring Boot` `REST APIs` `MySQL`

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=jeshwinwilliam&show_icons=true&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=jeshwinwilliam&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=jeshwinwilliam&layout=compact&theme=tokyonight" />
</p>

## 📈 Activity Graph

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=jeshwinwilliam&theme=tokyo-night&hide_border=true" width="100%"/>
</p>

## 🕒 Recent GitHub Activity

<!--START_SECTION:activity-->
<!-- This section auto-updates via the jamesgeorge007/github-activity-readme action — see setup note below -->
<!--END_SECTION:activity-->

## 🐍 Contribution Snake

<p align="center">
  <img src="https://raw.githubusercontent.com/jeshwinwilliam/jeshwinwilliam/output/github-contribution-grid-snake-dark.svg" alt="snake animation" width="100%"/>
</p>

<!-- Generated nightly by the Platane/snk GitHub Action — snake "eats" your contribution graph. See setup note below. -->

---

## 🎓 Education

**MS in Computer Science** — Oklahoma City University
**B.Tech in Computer Science** — Hindustan Institute of Technology & Science

## 🏆 Certifications

- AWS Certified Solutions Architect – Associate

---

<p align="center">
⚡ Focused on building scalable infrastructure, distributed systems, and production-grade backend services.
</p>

<!--
SETUP: two GitHub Actions power the animated sections above.
Add both workflow files to .github/workflows/ in your `jeshwinwilliam/jeshwinwilliam` repo.

1) Recent Activity list — .github/workflows/update-readme.yml
---------------------------------------------------------------
name: Update README Activity
on:
  schedule:
    - cron: '0 */6 * * *'
  workflow_dispatch:
jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: jamesgeorge007/github-activity-readme@master
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}

2) Contribution Snake — .github/workflows/snake.yml
---------------------------------------------------------------
name: Generate Snake
on:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:
  push:
    branches: [ main ]
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: jeshwinwilliam
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
-->

