---
description: Show your PostFast posts and their states for a date range (read-only)
---

Show the user's PostFast posts. This is read-only: do not create or change anything. Range or topic from the user: $ARGUMENTS

1. Work out two UTC dates from the request (ask, or use the last 7 days and say so).
2. Call `postsListTool` for that range.
3. Show channel, state and settings for each post exactly as returned. Never say a post was published unless its state says so.
4. This is read-only: do not change anything and you cannot delete posts.
5. If the tools say sign-in is required, tell the user to open `/mcp` and authenticate `postfast`.
