# EdgeFinder

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="repo_cover_dark.png">
  <source media="(prefers-color-scheme: light)" srcset="repo_cover.png">
  <img src="repo_cover.png" alt="EdgeFinder cover" width="100%">
</picture>

> **Real-time arbitrage detection for prediction markets powered by semantic vector search. EdgeFinder pairs semantically equivalent markets, reveals price discrepancies, and streams verifiable arbitrage insights across Polymarket, Kalshi, and more.**

## Table of Contents
- [Overview](#overview)
- [Repositories](#repositories)
- [Platform Architecture](#platform-architecture)
- [Tech Highlights](#tech-highlights)
- [Quick Start](#quick-start)
- [Contributing](#contributing)
- [License](#license)

## Overview
- EdgeFinder matches semantically equivalent markets, reveals price discrepancies, and surfaces executable arbitrage strategies.
- AI-driven embeddings plus custom PostgreSQL vector search find opportunities keyword systems miss.
- x402-powered pay-per-use access keeps the dataset public and up to date without accounts.
- Chainlink CRE-ready workflows, The Graph Amp analytics, and EVVM Sandbox support verifiable, decentralized operations.

## Repositories
| Repo | Purpose | Primary Tech | Docs |
| --- | --- | --- | --- |
| [edgefinder](https://github.com/EdgeFinder-Apps/edgefinder) | Frontend dashboard for discovery, payments, and opportunity exploration and Supabase Edge Functions | React, Vite, TypeScript, Tailwind, wagmi/viem, Supabase Edge Functions, Bun.js | [README](https://github.com/EdgeFinder-Apps/edgefinder#readme) |
| [api](https://github.com/EdgeFinder-Apps/api) | Fastify API server for dataset access and analytics | Fastify, TypeScript, Supabase Edge Functions, Bun.js | [README](https://github.com/EdgeFinder-Apps/api#readme) |

## Platform Architecture
1. **Market ingestion**: Supabase Edge Functions (or Chainlink CRE workflows) fetch and normalize live Polymarket and Kalshi markets.
2. **Embedding and matching**: OpenAI embeddings run inside PostgreSQL; cosine similarity and direction alignment pair equivalent markets.
3. **Arbitrage detection**: Price spreads and strategies are computed per matched pair, stored as hourly snapshots in shared datasets.
4. **Analytics**: Amp from The Graph tracks edge persistence, stability, and quality scores for the UI and downstream APIs.
5. **Access control**: x402 protocol gates fresh data with $1 USDC pay-per-use flows; proofs of payment are verified on-chain.
6. **Sandboxing**: EVVM Sandbox on Sepolia mirrors payment intents for gasless, risk-free previewing of dataset refreshes.

## Tech Highlights
- **x402 Payment Protocol**: Accountless, per-request access using EIP-3009 `transferWithAuthorization`.
- **Chainlink CRE**: Decentralized, consensus-based data fetching for production-ready ingestion.
- **PostgreSQL Vector Search**: In-database embeddings with custom similarity functions, no external vector DB required.
- **The Graph Amp**: Blockchain-native time-series analytics for arbitrage opportunity history and scoring.
- **EVVM Sandbox**: Gasless simulation path for testing payment flows before executing onchain.

## Quick Start
Clone the repos you need and follow their local guides:

```bash
# Frontend dashboard
git clone https://github.com/EdgeFinder-Apps/edgefinder.git
cd edgefinder
cp .env.example .env
pnpm install
pnpm dev

# Backend, pipelines, and functions
git clone https://github.com/EdgeFinder-Apps/api.git
cd api
pnpm install
pnpm dev
```

Refer to each repo's README for environment variables (Supabase, OpenAI, Amp, Chainlink CRE, x402) and deployment steps.

## Contributing
- Open an issue to propose changes or request new integrations before submitting a PR.
- Follow the linting, testing, and CI guidance in each repository.
- Design contributions: align with the existing product language in the frontend repo; infra changes should include rollout notes.

## Support
- Issues: use the respective repo issue tracker for bugs or feature requests.
- Discussions: start organization-wide conversations in GitHub Discussions (if enabled) or the app repo.
- For roadmap or integration questions, open an issue labeled `question`.

## License
- Each repository includes its own LICENSE file. Review individual terms before re-use or redistribution.
