# Price Research

Perform comp analysis research for the seller's item. Use web search to find recent sold prices and market data, then deliver a pricing recommendation with supporting evidence.

---

## How to Research (Instructions for Claude)

When asked to price an item, **do the research yourself** using web search. Don't tell the seller to go look things up.

### Context budget rule
**Use WebSearch exclusively — never Fetch full product or retailer pages.** A single retailer page (TCGPlayer, MTGStocks, secretlair.wizards.com) dumps 150–350 KB of HTML into context for maybe 500 bytes of useful pricing data. WebSearch snippets already contain the sold prices, market values, and trend data you need at ~5 KB per search. Fetching pages will exhaust the context window and prevent you from delivering the recommendation.

### Step 1: Search for recent sold prices
Run web searches for the item using queries like:
- `[item name] [set/variant] eBay sold price`
- `[item name] [condition/grade] sold listings`
- `[item name] TCGPlayer market price` (for trading cards)
- `[item name] PPG value` or `[item name] HobbyDB price` (for Funko Pops)

### Step 2: Compile comparable sales
From search results, pull out **actual sold prices** — not asking prices. Look for:
- Recent eBay sold listings (last 30–90 days)
- TCGPlayer Market Price (for cards)
- PPG/HobbyDB estimated value (for Funko)
- Any other marketplace data that surfaces

Aim for 3–10 comparable sales. Note the condition/grade of each comp relative to the seller's item.

### Step 3: Analyze and recommend
- Calculate the **median** of comps (not the average — outliers skew it)
- Adjust for the seller's specific item (condition, variant, completeness)
- Provide a **recommended listing price** (BIN) and a **floor price** (lowest acceptable offer)
- Note the listing format recommendation (auction vs BIN + Best Offer)

### Step 4: Present findings
Format the pricing recommendation like this:

```
## Pricing

**Estimated market value:** $XX – $XX
**Recommended BIN price:** $XX
**Best Offer floor (auto-decline below):** $XX
**Recommended format:** [BIN + Best Offer / Auction]

### Comps found:
- [Item description] — sold $XX on [date/source]
- [Item description] — sold $XX on [date/source]
- [Item description] — sold $XX on [date/source]
...

### Notes:
[Any context on pricing — trending up/down, low supply, seasonal factors, condition adjustments]
```

---

## Where to Search by Category

### Trading Cards (MTG, Pokemon, Sports)
- **Primary:** `[card name] [set] [condition] eBay sold` and `[card name] [set] TCGPlayer price`
- **TCGPlayer Market Price** is the best single-number reference for cards. It's a rolling average of recent sales, broken out by condition (NM, LP, MP, HP, DMG)
- TCGPlayer prices typically run slightly lower than eBay (lower seller fees)
- For graded cards: search `[card name] [grading company] [grade] sold`
- **Sports cards:** also search `[card name] [year] [parallel] 130point` — 130point.com specifically tracks Best Offer accepted prices
- **Useful sites:** TCGPlayer, PriceCharting (vintage/Pokemon), MTGStocks (MTG trends), Card Ladder (graded sports cards), Mavin (eBay sold aggregator)

### Sealed Card Products
- **Primary:** `[product name] [set] sealed eBay sold price`
- Sealed product prices are volatile — prioritize the most recent sales
- Cross-reference eBay with TCGPlayer (MTG sealed) or PriceCharting (Pokemon sealed)
- eBay prices often run higher than hobby shop prices due to buyer convenience

### Funko Pops
- **Primary:** `[character] Funko Pop #[number] PPG value` and `[character] Funko Pop eBay sold`
- **Pop Price Guide (PPG) / HobbyDB** processes 200k+ monthly transactions — its estimated value is a solid baseline
- PPG values tend to be conservative — eBay sold listings may run 10–20% higher for in-demand items
- Always check vaulted status — search `[character] Funko Pop vaulted`
- For graded Pops: search specifically for the grade (`PSA 9 [character] Funko Pop sold`)

### Disney Pins
- **Primary:** `Disney [pin name/design] pin eBay sold` and `Disney [pin name] LE [count] pin price`
- **PinPics** (pinpics.com) is the identification reference — use it to confirm edition details, not for pricing
- Disney pin pricing data is thinner than other categories. If comps are sparse, note this honestly
- LE pins with very small runs (under 250) may have few or no recent comps — state this and give a range based on what's available

---

## Pricing Adjustments

### Grade premiums (apply after finding comps)
- PSA 10 vs PSA 9: PSA 10 is typically 2–4x the PSA 9 price
- PSA 10 vs raw NM: 2–5x for modern cards, 5–20x for vintage/key cards
- BGS 9.5 ≈ PSA 10 in value for most modern cards
- BGS Black Label 10 > PSA 10, sometimes significantly
- If your seller's item is a higher grade than most comps, adjust up accordingly

### Condition adjustments
- Raw NM card with comps mostly in LP: price 15–30% above LP comps
- Funko with mint box vs comps with VG boxes: price 20–40% above
- Sealed product with perfect shrink vs comps with shelf wear: price at top of range

### Best Offer math
- Many eBay collectible sales close via Best Offer — typically 10–20% below BIN
- When recommending BIN + Best Offer: set BIN 10–15% above target price
- Set auto-decline at the floor price (lowest the seller should accept)
- Set auto-accept at or just above target price

---

## Supply and Demand Signals

Look for these while researching — they affect the recommendation:

### High demand (price up)
- Few active listings but many recent solds
- Items selling within hours/days of listing
- Trending item (new set release, movie/show tie-in, content creator spotlight)
- Recently vaulted/discontinued

### Soft demand (price down or auction)
- Many active listings, few recent solds
- Declining sold prices over the last 30–90 days
- Item has been reprinted or superseded
- Market flooded after a popular product release

### Sell-through context
When you find both sold and active listing counts, note the ratio:
- High sold / low active = strong demand, price confidently
- Low sold / high active = competitive market, consider pricing at or below median

---

## Seasonal Patterns

Factor these into the recommendation when relevant:
- **Q4 (Oct–Dec)**: Peak prices. Holiday demand. Best time to list high-value items
- **January**: Post-holiday dip. Prices soften across categories
- **Feb–Apr**: Tax refund recovery. Bigger purchases pick up
- **Summer**: Convention season (SDCC July, GenCon Aug) spikes specific items
- **New set releases**: Singles and sealed product price highest at release, decline over 2–4 weeks
- **Rotation/ban announcements**: MTG Standard rotation drops rotating cards; unbans spike affected cards

---

## When Research Is Thin

If web search doesn't return enough comp data:
- Say so honestly: "I found limited recent sales data for this item"
- Give the best range you can from what's available
- Suggest the seller check eBay sold listings directly (filter by Sold Items) for more granular data
- For very rare items, recommend auction format for price discovery
- Note if community knowledge (Reddit, Facebook groups) might help for niche items
