<h1 align="center">Raúl Benítez</h1>

<p align="center">
  <strong>Computer Science Engineer</strong> · Cloud Engineer @ TELUS<br>
  <sub>San Salvador, El Salvador 🇸🇻</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=blue" alt="Cloud">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=red" alt="Full-Stack">
  <img src="https://img.shields.io/badge/SQL-336791?style=flat-square&logo=postgresql&logoColor=white" alt="SQL">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=orange" alt="AI Automation">
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=green" alt="NoSQL">
  <img src="https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=googlebigquery&logoColor=white" alt="Integrations">
</p>

---

I work across the whole path data takes: **the pipelines that move it, the cloud infrastructure that runs it, and the products people actually use on top of it.**

Most engineers pick one end of that path. I've spent the last few years deliberately covering all three, building ETL/ELT pipelines and validating data integrity at **Clearview**, running production workloads on GCP at **TELUS**, and shipping full-stack systems that real businesses depend on daily.

That combination is why I can take a problem from *"we have messy data somewhere"* all the way to *"here's a working system your team uses every morning."*

**Currently:** Cloud Engineer at TELUS, working with Compute Engine, Cloud Storage, IAM, monitoring and CI/CD on Google Cloud Platform.

---

## Featured Projects

### 🍽️ [RestoPos](https://github.com/raulben6/restopos)
**Real-time restaurant POS, running in production**

A complete point-of-sale system deployed at a working restaurant. A waiter takes an order on a tablet, the kitchen screen updates instantly, the ticket prints on a thermal printer, and the owner watches revenue on a dashboard.

The interesting parts aren't the CRUD. They're the constraints a real restaurant imposes: **dual-channel pricing** (dine-in vs. delivery marketplace commission), **immutable order snapshots** so editing tomorrow's menu never rewrites yesterday's receipts, and **ESC/POS thermal printing** over raw TCP.

`Node.js` `Express` `PostgreSQL` `Socket.IO` `React 19` `JWT` `Railway` `Vercel`

---

### 📈 [Smart Trader Performance System](https://github.com/raulben6/smart-money-app)
**Trading journal with mentorship**

A mentor invites students, reviews their trades and written journals, assigns objectives, and moves them through a level system as performance improves.

Two decisions define it. First, **metrics are always derived from trades, never stored**, so a cached total can never silently drift from reality. Second, **authorization is enforced twice**, once at the Server Action and again inside every query, so a new call site can't accidentally bypass it. That second layer is verified by a full authorization matrix running against embedded Postgres.

**302 tests.** `Next.js 16` `TypeScript` `Drizzle ORM` `Neon` `Clerk` `Vercel Blob` `Vitest + PGlite`

---

### 💰 [Growly](https://github.com/raulben6/growly)
**Personal finance, built as a real product**

Accounts, transfers, envelope budgets, savings goals, recurring rules, a payment calendar and alerts: the things a bank statement never tells you.

Money is stored in **integer cents, never floats**, because `0.1 + 0.2 !== 0.3` compounds across every rollup in a budgeting app. Recurring transactions are made **idempotent by a database constraint** rather than by trusting a job to run exactly once.

**67 test suites + Playwright E2E.** `Next.js 16` `TypeScript` `Prisma` `PostgreSQL` `NextAuth v5` `Tailwind v4` `Zod`

---

<details>
<summary><b>Also: an automated trading bot</b> (private, collaborative)</summary>

<br>

A Node.js trading bot for Interactive Brokers with a generic host + swappable strategy architecture: bracket order lifecycle, percentage-of-equity sizing, safe end-of-day close, crash recovery, Telegram alerts, and a backtesting UI. Dockerized, ~480 commits, 97 test files.

The repository stays private because it's a collaborative project and the copyright belongs to its original author.

</details>

---

## Tech

**Cloud & Data**
<br>
`Google Cloud Platform` · `BigQuery` · `Compute Engine` · `Cloud Storage` · `IAM` · `ETL / ELT` · `Data Validation` · `Power BI` · `Monitoring & Observability` · `CI/CD`

**Languages & Backend**
<br>
`Python` · `SQL` · `TypeScript` · `JavaScript` · `Node.js` · `Express` · `REST APIs` · `Socket.IO`

**Data Stores**
<br>
`PostgreSQL` · `MongoDB` · `Neon` · `Prisma` · `Drizzle ORM`

**Frontend**
<br>
`React 19` · `Next.js 16` · `Tailwind CSS` · `Vite`

**Testing & Tooling**
<br>
`Vitest` · `Playwright` · `PGlite` · `Postman` · `Docker` · `Git` · `Active Directory`

---

## Experience

| | | |
|---|---|---|
| **2026 - Present** | **Cloud Engineer** | TELUS |
| **2025 - 2026** | **Data Engineer** | Clearview |
| **2024 - 2025** | **Business Analyst** | Lebbel |
| **2023 - 2024** | **Technical Support / IT Assistant** | Sequential Technologies |
| **2020 - 2023** | **Data Analyst** | Wings Station |

**B.Sc. Computer Science Engineering**, Universidad Francisco Gavidia (2020-2025)

Selected certifications: Cloud Security Technician · Fundamentals of Information Security · Relational Database Administrator · Python (Intermediate) · Career Skills in Data Analytics · Project Management Foundations

**Languages:** Spanish (native) · English (C1)

---

## GitHub

<p align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=raulben6&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=default&title_color=2F81F7&icon_color=2F81F7" alt="GitHub stats">
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=raulben6&layout=compact&hide_border=true&langs_count=8&theme=default&title_color=2F81F7" alt="Top languages">
</p>

---

## Contact

<p align="center">
  <a href="mailto:raulantoniobenitezva06@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
</p>

<p align="center">
  <sub>Open to opportunities in Cloud Engineering, Data Engineering and Full-Stack development, remote or based in El Salvador.</sub>
</p>
