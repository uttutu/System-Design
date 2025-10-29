# System Design Principles

A curated repository of **system design principles**, **architecture patterns**, and **real-world examples** — built for software engineers, architects, and anyone preparing for **system design interviews** or planning scalable systems.

---

## 📘 Purpose

The goal of this repository is to provide a **structured, practical reference** to key topics in system design:

* Core principles of scalability, reliability, and performance.
* Common architectural patterns used in production systems.
* Hands-on examples of system design problems.
* Templates for documenting design decisions (ADRs).

Whether you’re building distributed systems, reviewing designs, or mentoring engineers — this repo gives you a foundation to discuss and document architecture effectively.

---

## 🗂 Repository Structure

```
/ (root)
├── README.md                    # Overview (this file)
├── CONTRIBUTING.md              # How to contribute
├── CODE_OF_CONDUCT.md           # Code of conduct
├── docs/
│   ├── principles/              # Core design principles
│   │   ├── scalability.md
│   │   ├── reliability.md
│   │   ├── availability.md
│   │   ├── consistency.md
│   │   ├── caching.md
│   │   └── monitoring_observability.md
│   ├── patterns/                # Design patterns
│   │   ├── load_balancing.md
│   │   ├── database_sharding.md
│   │   ├── leader_election.md
│   │   └── cqrs.md
│   ├── examples/                # Example systems
│   │   ├── url_shortener.md
│   │   ├── realtime_chat.md
│   │   └── metrics_ingestion.md
│   └── templates/               # ADR and diagram templates
│       ├── adr_template.md
│       └── architecture_diagram_guidelines.md
├── adrs/                        # Architecture Decision Records
│   └── 0001-example-adr.md
├── interview_questions/         # Interview prep material
│   ├── backend.md
│   ├── frontend.md
│   └── system_design_mini_problems.md
└── assets/                      # Visuals and diagrams
    └── diagrams/
```

---

## 🧠 Key Topics

Each document under `docs/principles` explores a foundational design topic:

* **Scalability:** horizontal vs vertical scaling, load balancing, autoscaling
* **Reliability & Availability:** redundancy, failover, replication
* **Consistency Models:** strong vs eventual, CAP theorem
* **Caching:** cache-aside, write-through, invalidation strategies
* **Observability:** metrics, logs, traces, SLIs/SLOs
* **Security:** authentication, authorization, data protection

The `docs/patterns` directory contains production patterns — from **load balancing** and **database sharding** to **event-driven systems** and **CQRS**.

---

## 🧩 Examples

The `docs/examples` directory provides design walkthroughs for common system problems:

* URL Shortener
* Real-time Chat App
* Metrics Ingestion Pipeline

Each example includes:

* Problem statement and goals
* Component architecture diagrams
* Data model and flow
* Scaling and caching considerations
* Failure handling and monitoring

---

## 🧾 Architecture Decision Records (ADRs)

We use **ADRs** to document design decisions.

📄 Example template: [`docs/templates/adr_template.md`](docs/templates/adr_template.md)

Each ADR includes:

* **Context:** what problem are we solving?
* **Decision:** what we chose and why.
* **Consequences:** trade-offs and follow-ups.
* **Alternatives:** options we evaluated.

All ADRs live under the `/adrs` directory.

---

## 🧑‍💻 Contributing

We welcome contributions! 🙌

To add or update content:

1. Fork this repository.
2. Create a new branch: `feature/add-scalability-notes`
3. Add or update markdown files under `docs/`.
4. If relevant, add an ADR under `adrs/`.
5. Submit a pull request.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for details.

---

## 🌟 Acknowledgments

Inspired by concepts and systems designed by:

* Google SRE Book
* Designing Data-Intensive Applications (Kleppmann)
* High Scalability Blog
* System Design Primer (Donne Martin)

---

## 🚀 Getting Started

To clone and explore locally:

```bash
git clone https://github.com/uttutu/System-Design.git
cd system-design-principles
```

Explore documentation in `docs/` and start contributing!

---

> *"Design is not just about scalability; it's about trade-offs that align with goals."*
