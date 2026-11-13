---
description: Show your connected PostFast channels (read-only)
---

Show which channels are connected on the user's PostFast account. This is read-only.

1. Call `integrationList` (and `groupList` if the user asks about customer groups).
2. List each channel with its type and name exactly as returned.
3. Do not mention networks PostFast did not return. Live channels today are YouTube, TikTok, Bluesky, WordPress, DEV and Hashnode.
4. If none is connected, tell the user to connect a channel in PostFast.
5. If the tools say sign-in is required, tell the user to open `/mcp` and authenticate `postfast`.
