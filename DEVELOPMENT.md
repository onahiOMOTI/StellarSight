# Development Guide

## Prerequisites

- Rust 1.80+
- Node.js 18+
- Soroban CLI
- Docker and Docker Compose

## Setup

1. Clone the repository
2. Install dependencies for each component
3. Run `docker-compose up` to start the database and Redis

## Building

- Contracts: `cd contracts && cargo build`
- Backend: `cd backend && cargo build`
- Frontend: `cd frontend && npm run build`
- Observers: `cd observers && cargo build`

## Testing

- Run tests for each component in their respective directories