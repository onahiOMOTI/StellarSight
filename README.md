# StellarSight — Decentralised RPC Node Health and Observability Network

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Rust](https://img.shields.io/badge/Rust-1.80+-orange.svg)](https://www.rust-lang.org)
[![Next.js](https://img.shields.io/badge/Next.js-15-black.svg)](https://nextjs.org)
[![Stellar](https://img.shields.io/badge/Stellar-Soroban-blueviolet.svg)](https://soroban.stellar.org)
[![Stars](https://img.shields.io/github/stars/stellarsight/stellarsight.svg)](https://github.com/stellarsight/stellarsight)

**A community-run, on-chain monitoring network for Stellar and Soroban RPC endpoints.**

StellarSight allows node operators to register their Stellar Horizon, Stellar RPC, and Soroban RPC endpoints **on-chain** via a Soroban smart contract. A distributed network of observer nodes continuously performs liveness checks, latency measurements, and response accuracy tests. Results are aggregated into a transparent, reputation-weighted **reliability score** for each endpoint.

Developers and dApps can now query a **trustless node directory** before routing transactions, significantly improving reliability and reducing downtime risks.

Node operators with consistently high reliability scores earn **XLM micropayments** from a community treasury funded by protocol integrators and heavy users.

---

## ✨ Problem It Solves

The Stellar ecosystem currently lacks a **neutral, decentralized** way to evaluate RPC endpoint quality. Most developers blindly choose public endpoints or run their own nodes without real performance data. StellarSight provides:

- Trustless uptime and performance metrics
- A public reputation system for RPC providers
- An alerting API for degraded endpoints
- On-chain incentives for maintaining high-quality nodes

---

## 🚀 Key Features

- **On-Chain Node Registry** — Node operators register endpoints via Soroban smart contract
- **Distributed Observability Network** — Multiple independent observer nodes perform health checks
- **Multi-Metric Monitoring**
  - Liveness / availability
  - Latency (p50, p90, p99)
  - Response accuracy & correctness
  - Sync status validation
- **Reputation & Reliability Scoring** — Algorithmic score updated in real-time
- **Public Directory & API** — Query best nodes by region, reliability, or workload type
- **Alerting System** — Webhook and WebSocket notifications when endpoints degrade
- **Incentive Mechanism** — XLM micropayments from community treasury to top performers
- **SDK Integration Ready** — Any dApp or wallet can query the directory before submitting transactions

---

## 🛠 Tech Stack

| Layer                | Technology                                      | Purpose |
|----------------------|--------------------------------------------------|---------|
| **Smart Contracts**  | Rust + Soroban SDK                              | On-chain node registry & treasury |
| **Backend**          | Rust (Axum + Tokio + sqlx + Redis)              | Observer coordination & scoring engine |
| **Frontend**         | Next.js 15 (App Router) + TypeScript + Tailwind + shadcn/ui | Public dashboard & node explorer |
| **Database**         | PostgreSQL + TimescaleDB                        | Time-series metrics storage |
| **Blockchain**       | Stellar + Soroban (RPC + Horizon)               | Registry & micropayments |
| **Observer Nodes**   | Lightweight Rust binaries (distributed)         | Performing health checks |
| **Deployment**       | Docker + Docker Compose (Kubernetes ready)      | Easy self-hosting of observers |

---

## 📂 Project Structure

```bash
stellarsight/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── DEVELOPMENT.md
├── docker-compose.yml
├── contracts/                 # Soroban smart contracts
│   └── src/
│       ├── registry.rs        # Node registration & scoring
│       ├── treasury.rs        # XLM reward distribution
│       └── tests/
├── backend/                   # Rust Axum server + scoring engine
│   ├── src/
│   │   ├── observer/          # Health check logic
│   │   ├── registry/
│   │   ├── scoring/
│   │   ├── api/               # Public directory + alerting API
│   │   └── metrics/
├── frontend/                  # Next.js dashboard
│   ├── src/app/dashboard/
│   ├── components/NodeMap.tsx
│   └── components/ReliabilityChart.tsx
├── observers/                 # Lightweight observer client
├── infra/                     # Docker & K8s configs
├── docs/
└── scripts/
```

🚀 Quick Start (Local Development)
git clone https://github.com/stellarsight/stellarsight.git
cd stellarsight

Start infrastructure
docker-compose up -d db redis
Deploy Soroban contracts (Testnet)
cd contracts
soroban contract deploy --network testnet
Run backend
cd backend
cp .env.example .env
cargo run
Run frontend
cd frontend
npm install
npm run dev
Dashboard available at http://localhost:3000

📡 Usage Examples
Query Best RPC Node (for your dApp)
JavaScriptconst bestNode = await fetch("https://stellarsight.org/api/v1/nodes/best?region=eu&min_score=95")
  .then(res => res.json());
Register Your Node (via Soroban)
Rust// Example using Soroban SDK - see contracts/registry.rs
Subscribe to Alerts
httpPOST /api/v1/alerts/subscribe
{
  "endpoint": "https://rpc.example.com",
  "webhook_url": "https://yourapp.com/alerts"
}

Roadmap (2026)

 On-chain node registry contract (MVP)
 Distributed observer network v1
 Real-time scoring engine + public API
 Public dashboard with node map and historical metrics
 SDKs (JavaScript, Python, Rust)
 Treasury & micropayment distribution
 Multi-region observer incentives


Contributing
We actively welcome contributions from the Stellar community!
Types of work we will post on Drips Wave include:

New Features: Observer health check improvements, new metrics, advanced scoring algorithms
Bug Fixes: Reliability issues in observers or scoring logic
Frontend Enhancements: Better visualizations, node map, filtering UI
Documentation: API docs, integration guides, contributor setup
Testing: End-to-end tests for observers and contract interactions
DevOps: Docker optimizations and Kubernetes deployment
Research: New ways to measure RPC correctness and sync status

Each issue will be clearly scoped with difficulty level and required skills.
See CONTRIBUTING.md for details.

License
Apache License 2.0 — see the LICENSE file.

Built for a more reliable Stellar ecosystem.
Status: Early Active Development (April 2026)
Seeking community observers and Drips Wave contributors

StellarSight — Making RPC quality transparent and incentivized.
