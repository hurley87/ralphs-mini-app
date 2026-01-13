# Ralph's Forge

**The ultimate full-stack starter kit for Farcaster Mini Apps.**

This repository combines a production-ready Next.js frontend with a robust Foundry smart contract environment. It is designed to get you from "zero" to "deployed dApp" as fast as possible.

## Quick Start

```bash
git clone https://github.com/hurley87/ralphs-forge.git
cd ralphs-forge
```

```bash
claude "help me get set up"
```

## Architecture

This is a "Monorepo-Lite" setup. Everything lives in one place, but concerns are separated:

- `app/` (Frontend): The Next.js application, powered by the Farcaster Mini App Starter.
- `contracts/` (Backend): The Smart Contract environment, powered by LazerForge.

### Available Commands

Run these from the root directory:

| Command | Description |
|---------|-------------|
| `pnpm run dev` | Starts the Next.js local development server. |
| `pnpm run forge:build` | Compiles your smart contracts. |
| `pnpm run forge:test` | Runs Foundry tests for your contracts. |
| `pnpm run forge:deploy` | Deploys contracts and syncs ABIs to the frontend. |
| `pnpm run ralph` | Runs the autonomous development loop (see below). |

**Note**: Check `package.json` to configure the deployment script specific to your chain.

## Ralph: Autonomous Development Loop

Ralph is an autonomous coding agent powered by Claude. It works through a generated implementation plan, writing code, running tests, and committing changes without human intervention.

### How It Works

1. **Generate a Plan**: Use the `/blueprint` slash command in Claude Code to create an implementation plan.
   ```bash
   /blueprint Add a voting contract with a frontend UI
   ```
   This creates a task checklist in `ralph/IMPLEMENTATION_PLAN.md`.

2. **Run Ralph**: Execute the autonomous loop.
   ```bash
   pnpm run ralph        # Default: 10 iterations
   pnpm run ralph 20     # Custom: 20 iterations
   ```

Ralph will:
- Pick the next unchecked task from the plan
- Write the code and run verification (`forge test` or `pnpm run lint`)
- Mark the task complete and commit
- Exit and restart for the next task

### Key Principle: Contracts First

Ralph enforces a strict ordering: **all smart contract tasks must complete before frontend tasks begin**. This ensures ABIs exist before the frontend tries to import them.

## Tribute & Credits

Ralph's Forge stands on the shoulders of giants. It is a remix of these open-source projects:

- **Frontend**: [Farcaster Mini App Starter](https://github.com/builders-garden/miniapp-starter) by Builders Garden.
- **Smart Contracts**: [LazerForge](https://github.com/lazertechnologies/lazerforge) by Lazer Technologies.
- **Ralph**: [How to Ralph Wiggum](https://github.com/ghuntley/how-to-ralph-wiggum) by Geoffrey Huntley.

Please support the original creators by starring their repositories!

## License

This project retains the open-source licenses of its parent components. See the LICENSE file in the root and `contracts/` directory for details.
