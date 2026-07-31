<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,100:00F7FF&height=180&section=header&text=Jeshwin%20William%20James&fontSize=38&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Software%20Engineer%20%E2%80%94%20AI%20Infra%20%C2%B7%20Backend%20%C2%B7%20Distributed%20Systems&descAlignY=58&descSize=18" width="100%"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=24&pause=1000&color=00F7FF&center=true&vCenter=true&width=900&lines=Backend+%2B+AI+Infra+Engineer;Distributed+Systems+%C2%B7+Kafka+%C2%B7+Event-Driven+Platforms;Java+%C2%B7+Python+%C2%B7+Spring+Boot+%C2%B7+AWS;Systems%2C+scale%2C+signal." />
</p>

<p align="center">
  <a href="https://jeshwin.com"><img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=00F7FF"/></a>
  <a href="mailto:jeshwin.w.james@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
  <a href="https://linkedin.com/in/jeshwin-william-james-33a83b1a9"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://github.com/jeshwinwilliam"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

---

## 💫 About Me

Software Engineer with **4+ years** of experience across **distributed systems, AI-enabled platforms, backend services, and cloud infrastructure**, working primarily with **Java, Python, Kafka, and AWS**.

- 🧠 Building backend platforms where **AI-assisted tooling meets production-grade reliability** — not just prompt wrappers, but event-driven services with retries, observability, and failure recovery
- 🏗️ Deep focus on **Kafka-based orchestration**, idempotent processing, sagas, and dead-letter isolation at scale
- 📄 Peer-reviewed **Springer publication** (ICSADL 2022) on mobile payment security
- ☁️ **AWS Certified Solutions Architect – Associate**
- 💬 Ask me about event-driven architecture, AI-assisted review pipelines, or reconciliation systems at scale

---

## ⚡ Core Skills

**Backend Engineering** — Java · Spring Boot · REST APIs · gRPC · Spring Security · Hibernate · JPA · service design

**Distributed Systems** — Kafka · JMS · asynchronous workflows · retry strategies · dead-letter queues · resiliency patterns

**AI Platforms** — Python · workflow orchestration · AI-assisted review systems · platform integration · evaluation-minded tooling

**Cloud, Data & Operations** — AWS · GCP · Docker · Kubernetes · PostgreSQL · Oracle · Redis · Prometheus · Grafana · ELK · CI/CD

<p align="left">
<img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white"/>
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=springboot"/>
<img src="https://img.shields.io/badge/Kafka-000000?style=for-the-badge&logo=apachekafka"/>
<img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws"/>
<img src="https://img.shields.io/badge/GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker"/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes"/>
<img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql"/>
<img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis"/>
<img src="https://img.shields.io/badge/Cassandra-1287B1?style=for-the-badge&logo=apachecassandra"/>
<img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white"/>
</p>

---

## 🏗 System Architecture — AI-Assisted Event-Driven Platform

A generalized architecture reflecting the shape of the systems I build: async event backbone feeding both traditional services and an AI-assisted processing layer, with observability wired through everything.

```mermaid
flowchart TB
    Client[Client / Webhook Source]

    subgraph Edge["Edge Layer"]
        LB[Load Balancer]
        APIGW[API Gateway<br/>Rate Limiting · AuthN]
    end

    subgraph Services["Service Layer"]
        Ingest[Ingestion Service]
        Orchestrator[Workflow Orchestrator]
        AIWorker[AI-Assisted Analysis Worker<br/>Python]
        ResultSvc[Result / Review Service]
    end

    subgraph Messaging["Event Backbone"]
        Kafka[(Apache Kafka<br/>Partitioned Topics)]
        DLQ[(Dead Letter Queue)]
    end

    subgraph Data["Storage"]
        PG[(PostgreSQL<br/>Review / Order History)]
        Redis[(Redis<br/>Cache & Idempotency Keys)]
    end

    subgraph Observability["Observability Stack"]
        Prometheus[Prometheus]
        Grafana[Grafana]
        ELK[ELK Stack]
    end

    Client --> LB --> APIGW
    APIGW --> Ingest
    Ingest -- EventReceived --> Kafka
    Kafka -- consume --> Orchestrator
    Orchestrator -- dispatch --> AIWorker
    AIWorker -- AnalysisComplete --> Kafka
    Kafka -- consume --> ResultSvc
    Kafka -. failed events .-> DLQ

    Orchestrator --> Redis
    ResultSvc --> PG

    Ingest & Orchestrator & AIWorker & ResultSvc --> Prometheus
    Ingest & Orchestrator & AIWorker & ResultSvc --> ELK
    Prometheus --> Grafana
```

**Design decisions worth calling out:**

| Concern | Approach | Why |
|---|---|---|
| Service coupling | Kafka as async backbone instead of sync REST chains | Decouples producers/consumers, absorbs bursty webhook/traffic spikes, enables replay |
| AI worker isolation | Dedicated AI-assisted worker pool, decoupled from ingestion | AI latency variance never blocks core ingestion path |
| Failure handling | Dead-letter queues + retry topics + idempotency keys | Poison messages don't block partitions; safe to retry without duplicate side-effects |
| Consistency | Eventual consistency via event choreography, sagas for multi-step transactions | Avoids distributed locks; each service stays autonomous |
| Observability | Metrics (Prometheus), logs (ELK), per-service dashboards | Root-causing latency across service and AI-worker boundaries |

---

## 🏗 System Architecture — Distributed Event Processing Platform

A deeper reference architecture reflecting the backend platforms I build day-to-day: request path, async event backbone, storage-per-service, and full observability.

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
| Data ownership | Database-per-service (PostgreSQL, Cassandra, Redis) | Avoids shared-schema coupling; each store matches its access pattern |
| Failure handling | Dead-letter queues + retry topics | Poison messages don't block partition consumers |
| Consistency | Eventual consistency via event choreography, sagas for multi-step transactions | Avoids distributed locks; each service stays autonomous |
| Observability | Metrics (Prometheus), logs (ELK), traces (OTel) per service | Root-causing latency across service boundaries |

---

## ☁️ Cloud-Native Deployment Architecture

How the platforms above get deployed and scaled in production.

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

**Infra notes:** GitOps-style deploys, HPA driven by custom Kafka-consumer-lag metrics rather than just CPU, and IRSA (IAM Roles for Service Accounts) for least-privilege pod-level AWS access.

---

## 💼 Experience

**Software Engineer — State Street** *(Jan 2026 – Present)*
Built low-latency fund transaction and reconciliation services using Java, Spring Boot, Kafka, JMS, Oracle, PostgreSQL, Docker, Kubernetes, Jenkins, and AWS.
- Improved platform throughput by **40%** through event-driven transaction pipelines
- Reduced database query latency from **3.2s to under 1.1s** in production
- Enabled operations teams to resolve breaks **35% faster** with workflow dashboards

**Software Engineer — Accenture** *(Client: Flipkart, Feb 2022 – Dec 2024)*
Delivered backend systems for large-scale checkout and payment flows using Java, Spring Boot, Kafka, Cassandra, MySQL, Redis, Elasticsearch, Docker, Kubernetes, Jenkins, and GCP.
- Improved payment success rate by **12%** with smart-retry payment orchestration
- Reduced end-to-end API latency by **35%** through performance tuning
- Cut infrastructure overhead by **22%** via scaling and cloud optimization

---

## 🚀 Featured Builds

### [PR Intelligence Platform](https://github.com/jeshwinwilliam/pr-intelligence-platform-jeshwin)
AI-assisted pull request analysis platform with event-driven review orchestration, persistent review history, and observability-first service design.
`Spring Boot` `Kafka` `AI-assisted review` `Docker`
📐 [System design write-up](https://jeshwin.com/system-design/pr-intelligence/index.html)

### [Distributed Order Processing Platform](https://github.com/jeshwinwilliam/distributed-event-processing-system)
Order, payment, inventory, and logistics workflow architecture with Kafka-driven orchestration, idempotent processing, and resilient failure recovery across service boundaries.
`Java` `Spring Boot` `Kafka` `PostgreSQL` `Saga pattern`
📐 [System design write-up](https://jeshwin.com/system-design/order-processing/index.html)

### [Mobile Payment Security System](https://github.com/jeshwinwilliam/mobile-payment-security-system)
IMEI-driven device verification system for mobile payment authentication and fraud-aware decision flows — connected to a peer-reviewed publication.
`Java` `Spring Boot` `REST APIs` `Security`
📐 [System design write-up](https://jeshwin.com/system-design/mobile-payment-security/index.html)

### Real-Time Transaction Reconciliation System
Trade ingestion, validation, ledger updates, duplicate detection, and reconciliation workflows for high-integrity financial operations.
`Kafka` `Partitioned processing` `Auditability`
📐 [System design write-up](https://jeshwin.com/system-design/reconciliation/index.html) *(case study generalized from production work)*

---

## 📄 Publication

**"Improved Security on Mobile Payments Using IMEI Verification"**
Peer-reviewed conference paper, ICSADL 2022 — published in Springer's *Advances in Intelligent Systems and Computing* (Sentiment Analysis and Deep Learning, 2023, pp. 183–193).
[View on Springer](https://link.springer.com/chapter/10.1007/978-981-19-5443-6_16) · [DOI](https://doi.org/10.1007/978-981-19-5443-6_16) · 1120 accesses · 1 citation

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

## 🐍 Contribution Snake

<p align="center">
  <img src="https://raw.githubusercontent.com/jeshwinwilliam/jeshwinwilliam/output/github-contribution-grid-snake-dark.svg" alt="snake animation" width="100%"/>
</p>

---

## 🎓 Education & Credentials

**MS in Computer Science** — Oklahoma City University *(2026)*
**B.Tech in Computer Science and Engineering** — Hindustan University *(2022)*
**AWS Certified Solutions Architect – Associate** — issued March 2026

---

## 📫 Contact

Open to software engineering roles across **backend, distributed systems, and AI platforms** — especially event-driven architecture, cloud infrastructure, and developer-facing systems where reliability, scale, and product thinking matter.

<p align="center">
  <a href="https://jeshwin.com"><img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=00F7FF"/></a>
  <a href="mailto:jeshwin.w.james@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
  <a href="https://linkedin.com/in/jeshwin-william-james-33a83b1a9"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://github.com/jeshwinwilliam"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

<p align="center">
⚡ Systems, scale, signal — building AI-enabled platforms and resilient backend infrastructure for production environments.
</p>

<!--
SETUP: two GitHub Actions power the animated sections above.
Add both workflow files to .github/workflows/ in your `jeshwinwilliam/jeshwinwilliam` repo.

1) Contribution Snake — .github/workflows/snake.yml
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
