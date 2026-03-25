# Neural Lattice — The Digital Architect for Codebases

## Overview

Neural Lattice is an AI-powered codebase intelligence platform with a futuristic dark-mode UI. It analyzes pull requests contextually, maintains a living architectural blueprint, runs multi-agent debates, generates auto-fix patches, and provides real-time system health insights.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/neural-lattice)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **State**: Zustand
- **Animations**: Framer Motion
- **Build**: esbuild (CJS bundle)

## Structure

```text
artifacts-monorepo/
├── artifacts/
│   ├── neural-lattice/     # React + Vite frontend (preview at /)
│   └── api-server/         # Express API server (at /api)
├── lib/
│   ├── api-spec/           # OpenAPI spec + Orval codegen config
│   ├── api-client-react/   # Generated React Query hooks
│   ├── api-zod/            # Generated Zod schemas from OpenAPI
│   └── db/                 # Drizzle ORM schema + DB connection
├── scripts/                # Utility scripts
└── ...
```

## Features

- **Auth Flow**: Login page with animated neural background, role selection (Developer / Architect / Reviewer), Demo Mode bypass
- **Dashboard (Sentinel View)**: Interactive SVG system health map, metrics panel (Code Stability, Architectural Integrity, PR Risk Score, Active Agents)
- **Agent Lab**: 5 specialized agents (Chronicler, Inquisitor, Advocate, Security Scout, Refactor Agent), real-time agent debate chat panel with typing animations
- **PR Analysis**: Step-by-step flow — input → simulated AI processing → output with violations, synthetic patch (before/after diffs)
- **Blueprint Explorer**: Full-screen interactive graph with clickable nodes
- **Notifications**: Bell icon with dropdown, seeded with demo notifications
- **Demo Mode**: Toggle simulates full PR → debate → patch generation flow

## Database Schema

- `pr_analyses` — PR analysis results with violations, improvements, synthetic patches
- `debate_messages` — Agent debate messages with agent identity and message type
- `notifications` — System notifications

## API Routes

- `GET /api/healthz` — Health check
- `GET /api/metrics` — System metrics dashboard
- `GET /api/graph` — System health graph nodes/edges
- `GET /api/agents` — List all 5 agents
- `GET /api/agents/debate?prId=` — Get debate messages
- `POST /api/agents/debate` — Trigger new agent debate (seeds demo messages)
- `GET /api/prs` — List PR analyses
- `POST /api/prs` — Analyze a new PR
- `GET /api/prs/:id` — Get specific PR analysis
- `GET /api/notifications` — List notifications

## Color Theme

- Background: Dark navy `220 15% 10%`
- Primary: Electric blue `220 100% 60%`
- Secondary: Neon purple `270 80% 60%`
- Accent: Soft green `140 70% 45%`
- Destructive: Soft red `0 70% 50%`

## Running

- Frontend dev: `pnpm --filter @workspace/neural-lattice run dev`
- API dev: `pnpm --filter @workspace/api-server run dev`
- DB push: `pnpm --filter @workspace/db run push`
- Codegen: `pnpm --filter @workspace/api-spec run codegen`
