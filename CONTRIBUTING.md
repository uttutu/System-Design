# Contributing to System Design Principles

We’re excited that you’re interested in contributing to the **System Design Principles** repository! 🎉
This project thrives on open collaboration — whether you’re adding new design topics, refining explanations, or contributing architecture decision records (ADRs).

---

## 🧭 Contribution Guidelines

### 1. Fork & Clone

Start by forking this repository and cloning it locally:

```bash
git clone https://github.com/uttutu/System-Design.git
cd System-Design
git checkout -b feature/<short-description>
```

---

### 2. Follow the Structure

Organize your contribution under the correct directory:

| Type           | Location           | Example                |
| -------------- | ------------------ | ---------------------- |
| **Principles** | `docs/principles/` | `scalability.md`       |
| **Patterns**   | `docs/patterns/`   | `load_balancing.md`    |
| **Examples**   | `docs/examples/`   | `url_shortener.md`     |
| **ADRs**       | `adrs/`            | `0002-new-decision.md` |
| **Templates**  | `docs/templates/`  | `adr_template.md`      |

Each document should be self-contained, clear, and practical.

---

### 3. Writing Standards

When contributing content:

* Use **Markdown** for all files.
* Keep tone **neutral, educational, and concise**.
* Include **real-world examples** when applicable.
* Add diagrams or visuals under `/assets/diagrams/`.
* Cite sources if referencing external materials.

#### Formatting checklist

* Top-level title (`#`) for each page.
* Logical subheadings (`##`, `###`).
* Lists for trade-offs and design choices.
* Code blocks for pseudocode or configs.
* Use tables for pros/cons or comparisons.

---

### 4. Submitting an ADR (Architecture Decision Record)

If your change involves a major architectural or conceptual decision:

1. Copy `docs/templates/adr_template.md` into `adrs/`.
2. Name it sequentially: `adrs/000X-title.md`.
3. Fill out:

   * **Context** – what problem are we solving?
   * **Decision** – what did we choose and why?
   * **Consequences** – trade-offs or follow-ups.
   * **Alternatives** – what was rejected.

---

### 5. Commit and Push

Use clear, descriptive commit messages:

```bash
git add .
git commit -m "docs: add caching principle with examples"
git push origin feature/add-caching-principle
```

---

### 6. Create a Pull Request

1. Open a pull request to the main branch.
2. Fill out the PR template:

   * Purpose of the change.
   * Summary of updates.
   * Any related ADR or diagram.
3. Request review from maintainers.

#### PR Checklist ✅

* [ ] Follows directory and naming conventions.
* [ ] Content is clear and technically accurate.
* [ ] Added diagrams (if needed).
* [ ] ADR created for major changes.

---

### 7. Review Process

* Maintainers will review PRs for structure, clarity, and correctness.
* Feedback may include adding diagrams, simplifying explanations, or reorganizing sections.
* Approved PRs will be merged into `main`.

---

## 🧱 Issue Reporting

To report an issue:

1. Use the [Issue Template](.github/ISSUE_TEMPLATE.md).
2. Clearly describe the problem or suggestion.
3. Include file paths, references, or screenshots.

Common issue types:

* 📘 Documentation improvement
* 🧩 New system design example
* 🧠 Missing design pattern
* 🧰 Tooling or build fix

---

## 🌟 Contribution Examples

Here are great first contributions:

* Add `docs/principles/scalability.md` or expand `availability.md`.
* Write an ADR about a trade-off (e.g., REST vs gRPC APIs).
* Add a new example system (`docs/examples/job_scheduler.md`).
* Contribute a design diagram for existing examples.

---

## 🤝 Code of Conduct

By contributing, you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).
We strive to maintain a respectful, inclusive, and knowledge-sharing environment.

---

> *Thank you for helping make system design knowledge open and accessible to all!* 💙
