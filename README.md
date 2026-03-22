# listing-advisor

Listing advisor for collectible hobby items. Send it a message about what you're selling — a trading card, Funko Pop, Disney pin, sealed product — and it returns a complete listing recommendation: pricing, description, category, shipping, and photo guidance.

Runs as a Discord bot powered by Claude Code Channels.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- A Discord bot token (create one at the [Discord Developer Portal](https://discord.com/developers/applications))
- Node.js (for project dependencies)

## Setup

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment

```bash
cp .env.example .env
# Fill in your values
```

### 3. Connect Discord

Run the `/discord:configure` command in Claude Code to save your bot token and set access policy:

```bash
claude
# Then inside the session: /discord:configure
# Paste your Discord bot token when prompted
```

### 4. Authorize users

The bot uses an allowlist to control who can interact with it. To pair a user:

1. Run `/discord:access` inside a Claude Code session
2. Follow the prompts to approve a pairing or edit the allowlist

**To pair additional users later:** Run `/discord:access` again from any active session — you don't need to reconfigure the bot, just manage the allowlist.

## Running the advisor

Start a Claude Code session with the Discord plugin:

```bash
claude --channels plugin:discord@claude-plugins-official
```

The bot comes online in Discord as soon as the session starts. Send it a message like:
- "I have a near-mint Sheoldred, the Apocalypse from Dominaria United"
- "I found a vaulted Funko Pop #01 Batman at a garage sale"
- "I have a sealed Pokémon Prismatic Evolutions ETB"
- "I have a Limited Edition 500 Stitch pin from 2019"

## Shutting down

Shutting down requires **two steps**. The Claude Code session and the Discord channel plugin run as separate processes.

### Step 1: End the Claude Code session

Exit the Claude Code session normally (`/exit`, Ctrl+C, or close the terminal).

### Step 2: Kill the channel plugin process

The Discord plugin runs on **Bun** (not Node), and it survives after the Claude session ends. The bot will still appear online in Discord — it maintains its WebSocket connection — but messages go nowhere.

Find and kill the orphaned Bun process:

```bash
ps aux | grep bun
# Find the PID(s) for the channel plugin
kill -9 <PID>
```

The bot goes offline in Discord once the Bun process is killed.

> **Note:** `ps aux | grep node` won't find it — the plugin doesn't run on Node. Always grep for `bun`.

## Supported categories

- **Trading cards** — MTG, Pokémon, sports (raw and graded singles)
- **Sealed card products** — booster boxes, ETBs, blister packs, bundles
- **Vinyl figures** — Funko Pops (common, chase, exclusive, vaulted)
- **Disney pins** — official park pins, limited editions, rack/open edition
- **General collectibles** — fallback for items outside the above

## License

MIT
