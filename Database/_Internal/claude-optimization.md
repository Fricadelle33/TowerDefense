# Token Optimization

Token optimization with Claude Code requires a surgical approach. You need to control the exact payload of what goes in and what comes out.

Here is the mechanics to cut the fat:

## Isolate the Context

Claude Code will ingest your entire repository if you let it. Don't.
— Use .claudesignore relentlessly. Exclude assets, static files, and irrelevant modules.
— If you are working on the scoring engine, block its access to the UI components. Point the model exclusively to the files required for the immediate task.

## Stop Full-File Rewrites

Generating a 500-line script for a 10-line logic change is a massive waste of output tokens.
— Command Claude to output only the modified functions or classes.
— Enforce a strict diff format: "Provide only the updated code blocks. Do not rewrite the entire file."

## The Architecture Anchor

Raw code is an inefficient way to provide high-level context.
— Maintain a dense, centralized architecture.md or game_state.md file.
— Document the core game loop, data structures, and board state mechanics in tight bullet points.
— Feed this single summary file to Claude to align its understanding, rather than letting it parse a dozen different scripts to figure out how your game works.

## Kill the Thread

Conversation history is a token parasite. Every subsequent prompt resends the entire chat history.
— Compartmentalize your coding sessions. Build one specific feature per thread.
— Once the feature works and is committed, wipe the session. Start fresh for the next component.

## Compress the Input

Drop the conversational filler. The model doesn't need "please" or "can you help me."
— State the objective, the constraints, and the exact target file.
— Use XML tags (e.g., <current-logic>, <desired-output>) to segment your prompts. It organizes the context natively and speeds up the model's parsing efficiency.

Which specific mechanic of your board game is burning through the most tokens right now?

## Prompt example

Objective: Implement dual-element cards into the core mechanics.

<rule-definition>
- A card can have two elements in YAML (Syntax: `element: [water, air]`).
- Mechanical constraint: If a dual-element card is the FIRST card played in a turn, the playing hero must declare which of the two elements becomes "Element E" for the combo counter.
</rule-definition>

<execution>
1. Update `Database/economy-and-engine.md` and `Database/rules.md` to explain the mechanical constraint.
2. Update `Database/effect-vocabulary.md` to include the new YAML array syntax.
3. Update `.claude/claude-context.md` to reflect this change for future AI context.
</execution>

<constraints>
- DO NOT rewrite the entire files. 
- Output ONLY the specific Markdown sections or headers that you are modifying.
- Keep the rule explanations under two sentences. No flavor text.
</constraints>

### Generation tasks (Epic 2)

When the database is sufficiently populated, Claude Code will:

1. **Parse** all YAML blocks across all .md files
2. **Validate** cross-references (card:slug, hero:slug, contract:slug, etc.)
3. **Generate** `cards-master.md` — flat table of all cards with auto-assigned IDs
4. **Generate** print-ready SVG/PDF card sheets (63×88mm standard)
5. **Run** balance simulations against enemy Zeal pools
6. **Report** loop-risk card combinations and recommended fixes

### Suggested invocation order for a content review:

1. `strict_validator` — catch typos before anyone reads
2. `market_supervisor` — validate design direction
3. `rotating_player` (Felix persona) — test teachability
4. `adversarial_gm` — stress-test the encounter
5. `creative_player` — find the exploits
6. `rotating_player` (Beatrice persona) — check staying power
