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