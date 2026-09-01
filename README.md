<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2F81F7,50:8B5CF6,100:10B981&height=200&section=header&text=Ra%C3%BAl%20Ben%C3%ADtez&fontSize=52&fontColor=ffffff&fontAlignY=38&desc=Building%20with%20AI%20%C2%B7%20Engineering%20with%20Data&descSize=18&descAlignY=58&animation=fadeIn" alt="Raúl Benítez. Building with AI, engineering with data.">
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3400&pause=800&color=8B5CF6&center=true&vCenter=true&width=780&lines=I+build+software+with+AI+as+a+power+tool;I+build+systems+that+move+and+model+data;Spec+first%2C+tests+always%2C+then+the+code" alt="I build software with AI as a power tool. I build systems that move and model data. Spec first, tests always, then the code.">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/San_Salvador-El_Salvador-2F81F7?style=for-the-badge&logo=googlemaps&logoColor=white" alt="San Salvador, El Salvador">
  <img src="https://img.shields.io/badge/English-C1-8B5CF6?style=for-the-badge&logo=duolingo&logoColor=white" alt="English C1">
  <img src="https://img.shields.io/badge/Open_to_work-10B981?style=for-the-badge&logo=handshake&logoColor=white" alt="Open to work">
</p>

---

## Two things I am serious about

<table>
<tr>
<td width="50%" valign="top">

### 🤖 Building with AI

I develop **with** AI, not around it. My workflow is spec first: I write the design document, then the implementation plan, then the tests, and only then does code get written. The AI accelerates the typing. It does not make the architectural calls.

You can check that claim. Every product repo here carries the real specs and plans I worked from, in `docs/design/`, dated before the commits that implemented them.

That discipline is why three production-grade products exist with **636 automated tests** behind them.

</td>
<td width="50%" valign="top">

### 📊 Engineering with data

Before the products, data was the job. **ETL and ELT pipelines in Python**, integrity and validation checks, MongoDB and SQL sources reconciled against each other, and datasets loaded and analysed in **BigQuery** and **Cloud Storage**.

The part I actually love is the modelling: choosing the representation that makes a hard question cheap to answer. A street network becomes a graph and an NP-hard route collapses into something solvable. A noisy sales series becomes a question about whether the extra model earns its keep, which sometimes it does not.

</td>
</tr>
</table>

**Both, together, are the point.** AI makes me fast. Data engineering makes me right. Neither is worth much on its own.

---

## 📐 How the AI workflow actually looks

```mermaid
flowchart LR
    A["📋 Spec<br/><i>what and why</i>"] --> B["🗺️ Plan<br/><i>ordered tasks</i>"]
    B --> C["🧪 Tests<br/><i>written first</i>"]
    C --> D["⌨️ Implementation<br/><i>AI-accelerated</i>"]
    D --> E["🔍 Review<br/><i>against the spec</i>"]
    E -->|"gap found"| A
    E -->|"matches"| F["🚀 Ship"]

    style A fill:#8B5CF6,color:#fff
    style C fill:#10B981,color:#fff
    style D fill:#2F81F7,color:#fff
    style F fill:#F59E0B,color:#fff
```

The specs are committed, so this is auditable rather than a claim: [RestoPos](https://github.com/raulben6/restopos/tree/main/docs/design) · [Growly](https://github.com/raulben6/growly/tree/main/docs/design) · [Smart Trader](https://github.com/raulben6/smart-money-app/tree/main/docs/design)

---

## 🧮 Data and algorithms

### 📉 [wings-forecast](https://github.com/raulben6/wings-forecast)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Time Series](https://img.shields.io/badge/Time_Series-8B5CF6?style=flat-square)
![Walk-forward](https://img.shields.io/badge/Walk_forward_validation-10B981?style=flat-square)

**Forecasting daily sales for a restaurant, from 227 days of its real operating data.**

Three findings, and two of them are negative. **A day-of-week average beat both the Ridge and the gradient boosting model**, and all three sit inside the same bootstrap interval, so they are statistically tied. Then I added El Salvador's holiday calendar and daily weather history, and **both made the models worse**.

The third finding is the one worth acting on. Rain barely moves total sales, but it **doubles the delivery share of revenue**, from 12% to 25% (p = 0.001). Rain does not remove demand, it relocates it, which is exactly why weather cannot forecast the total: the channels compensate. And because the delivery marketplace takes an effective 27% cut, a rainy day converts the same revenue into **3.25 points less margin** (p = 0.0009).

Weather is split into an **operational** mode (yesterday's observed weather, what production could actually use) and an **explanatory** one, because tomorrow's weather is a forecast, not a fact. Validation is walk-forward, never a random split, and nine of the twenty-five tests exist purely to prove no feature can see its own future.

The repo also carries a **read-only exporter for product-level demand**, validated against a live production Postgres: one `SELECT`, aggregated in the database, no access to personal data, amounts indexed before they are written. It reports descriptives at any volume but **refuses to emit forecast metrics below a data threshold**, because the POS has no sales history yet and a model fitted on a handful of rows per product is not a result.

<br>

### 🗺️ [ruta-cartero](https://github.com/raulben6/ruta-cartero)

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![NetworkX](https://img.shields.io/badge/NetworkX-2C5BB4?style=flat-square)
![OSMnx](https://img.shields.io/badge/OSMnx-7EBC6F?style=flat-square&logo=openstreetmap&logoColor=white)
![Graph Theory](https://img.shields.io/badge/Graph_Theory-8B5CF6?style=flat-square)
![Operations Research](https://img.shields.io/badge/Operations_Research-F59E0B?style=flat-square)

**The Rural Postman Problem, solved on a real city street network.**

Every house on 15 streets has to be visited, and the route must start and end at fixed points. That path exists only if the graph is Eulerian, and real street networks never are. So: download the genuine OpenStreetMap cycling graph, pair the odd-degree vertices at **minimum matching cost**, duplicate the connecting paths, then add a **virtual start-to-end edge** so an Eulerian circuit can be built and reopened into the path you actually need.

Cost is measured in minutes rather than metres, because a courtyard or a portal with thirteen mailboxes is expensive in ways distance cannot see. The output is an interactive map you follow on a phone.

> The dataset shipped here is synthetic and reproducible. The original described how to reach specific private homes, so it stays private.

---

## 🚀 Products that shipped

### 🍽️ [RestoPos](https://github.com/raulben6/restopos)

![Live](https://img.shields.io/badge/%F0%9F%9F%A2_running_in_production-10B981?style=flat-square)
![Node](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Socket.IO-010101?style=flat-square&logo=socketdotio&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

A real-time POS **deployed at a working restaurant**. Orders appear on the kitchen screen instantly, tickets print over raw TCP to a thermal printer, and order history is immutable by design, so editing tomorrow's menu never rewrites yesterday's receipts.

### 📈 [Smart Trader Performance System](https://github.com/raulben6/smart-money-app)

![Tests](https://img.shields.io/badge/302_tests-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle-C5F74F?style=flat-square&logo=drizzle&logoColor=black)
![Clerk](https://img.shields.io/badge/Clerk-6C47FF?style=flat-square&logo=clerk&logoColor=white)

A trading journal with a mentor on the other side. **Every metric is derived from the trades, never stored**, so a cached total cannot drift from reality. Authorization is enforced twice, and proven by a matrix of tests running against a real Postgres embedded in the test process.

### 💰 [Growly](https://github.com/raulben6/growly)

![Tests](https://img.shields.io/badge/283_tests_+_E2E-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma_6-2D3748?style=flat-square&logo=prisma&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)

Personal finance built as a real product. Money is stored in **integer cents, never floats**, and recurring transactions are made **idempotent by a database constraint** rather than by trusting a job to run exactly once.

<details>
<summary>🔒 <b>Also: an automated trading bot</b> (private, collaborative)</summary>

<br>

Node.js bot for Interactive Brokers with a generic host and swappable strategies: bracket order lifecycle, percentage-of-equity sizing, safe end-of-day close, crash recovery, Telegram alerts and a backtesting UI. Dockerized, around 480 commits and 97 test files. The repository stays private because the copyright belongs to its original author.

</details>

---

## 🧰 Stack

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,ts,nextjs,react,nodejs,postgres,gcp,docker,vercel,git&perline=10" alt="Python, TypeScript, Next.js, React, Node.js, PostgreSQL, Google Cloud, Docker, Vercel, Git">
</p>

**🤖 AI & Automation**

![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=claude&logoColor=white)
![MCP](https://img.shields.io/badge/MCP_Servers-000000?style=flat-square&logo=modelcontextprotocol&logoColor=white)
![Spec-Driven](https://img.shields.io/badge/Spec_Driven_Development-8B5CF6?style=flat-square)
![Python Automation](https://img.shields.io/badge/Python_Automation-3776AB?style=flat-square&logo=python&logoColor=white)

**📊 Data & Analytics**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=googlebigquery&logoColor=white)
![ETL](https://img.shields.io/badge/ETL_%2F_ELT-FF6B35?style=flat-square&logo=apacheairflow&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![NetworkX](https://img.shields.io/badge/NetworkX-2C5BB4?style=flat-square)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Data Validation](https://img.shields.io/badge/Data_Validation-10B981?style=flat-square)

**⚙️ Backend & Data Layer**

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle-C5F74F?style=flat-square&logo=drizzle&logoColor=black)
![Socket.IO](https://img.shields.io/badge/Socket.IO-010101?style=flat-square&logo=socketdotio&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=flat-square&logo=zod&logoColor=white)

**🎨 Frontend**

![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)

**🧪 Testing**

![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![PGlite](https://img.shields.io/badge/PGlite-336791?style=flat-square&logo=postgresql&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

**🚀 Cloud & Ship**

![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

---

## 📊 By the numbers

<table>
<tr>
<td align="center" width="25%"><h2>5</h2><b>public projects</b></td>
<td align="center" width="25%"><h2>661</h2><b>automated tests</b></td>
<td align="center" width="25%"><h2>295</h2><b>commits</b></td>
<td align="center" width="25%"><h2>38k</h2><b>lines shipped</b></td>
</tr>
</table>

<p align="center"><sub>Counted from the repositories on this profile. Not estimated.</sub></p>

---

## 📫 Let's talk

<p align="center">
  <a href="mailto:raulantoniobenitezva06@gmail.com">
    <img src="https://img.shields.io/badge/Email_me-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="https://github.com/raulben6?tab=repositories">
    <img src="https://img.shields.io/badge/See_the_code-181717?style=for-the-badge&logo=github&logoColor=white" alt="Repositories">
  </a>
</p>

<p align="center">
  <sub><b>Open to roles in AI-assisted development, data engineering, and full stack. Remote or based in El Salvador.</b></sub>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:10B981,50:8B5CF6,100:2F81F7&height=110&section=footer" alt="">
</p>
