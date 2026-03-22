# listing-advisor

## What This Is
eBay listing advisor for collectible hobby items — accessible via Discord (and eventually Telegram) through Claude Code Channels. Think of it as a knowledgeable friend who helps you write better eBay listings: titles, descriptions, pricing guidance, category selection, and photo tips.

## Tech Stack
- Node.js + JavaScript (ESM)
- Claude Code Channels (Discord plugin) for messaging interface
- [add dependencies as they're introduced]

## How to Run
```bash
npm install
npm start
```

## Channels Setup
This project uses Claude Code Channels to bridge Discord messages into a Claude Code session. The Discord bot is configured separately — see the Channels docs for setup steps.

To start a session with Discord enabled:
```bash
claude --channels plugin:discord@claude-plugins-official
```

## Architecture
- `src/index.js` — entry point (placeholder for now)
- Discord messages arrive via Claude Code Channels plugin (not custom bot code)
- Claude Code session handles all message processing and replies

## Listing Expertise (Phase 2)
_Not yet implemented. Planned areas:_

- **Title optimization** — keyword-rich titles that match eBay search behavior
- **Description templates** — structured descriptions for collectible categories
- **Category & item specifics** — correct eBay category tree mapping
- **Pricing guidance** — comp-based pricing from recent sold listings
- **Photo tips** — what to photograph and how for collectibles
- **Condition grading** — standardized condition descriptions by category

## Supported Categories (Phase 2)
_Categories to be added as expertise is built out:_

- Trading cards (sports, TCG)
- Action figures & toys
- Die-cast models
- Vintage electronics
- Comics & manga
- [expand as needed]

## Conventions
- See global CLAUDE.md for commit style and general conventions
- Public repo — no tokens, no Notion IDs, no account details in committed files
- Content and listing expertise will live in structured data files (format TBD)

## Environment Variables
All secrets and config are in `.env`. See `.env.example` for required keys.
