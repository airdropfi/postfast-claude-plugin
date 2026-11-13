# PostFast plugins for Claude Code

> PostFast lets an AI assistant draft YouTube and TikTok video posts in your PostFast account; you review and press Post in PostFast.

## PostFast at a glance

- **What it is:** PostFast lets an AI assistant draft YouTube and TikTok video posts in your PostFast account; you review and press Post in PostFast.
- **Primary user:** An AI assistant (Claude, Cursor, Gemini CLI or any MCP client) lists your connected channels, prepares media and creates drafts. You open each draft in PostFast, review it and press Post now or Add to calendar.
- **Channels live today:** YouTube (Shorts and videos: title, description, privacy public/unlisted/private, made-for-kids, thumbnail), TikTok (caption, who can view, comments, duet, stitch, commercial-content disclosure; Direct Post or inbox upload), Bluesky (handle and app password), WordPress, DEV and Hashnode. Other networks are not available yet.
- **What the AI can do:** Eight tools: `integrationList`, `groupList`, `integrationSchema`, `triggerTool`, `createDraftPostTool`, `postsListTool`, `postSettingsTool` and `uploadFromUrlTool`. It only creates drafts: it never publishes or schedules, and it cannot delete posts.
- **Human oversight:** Nothing is published until you open the draft in PostFast and press Post now or Add to calendar. TikTok privacy, comment, duet, stitch and commercial-content disclosure are choices you make in the PostFast composer. You can revoke the connection in PostFast.
- **Cost:** You can create a free PostFast account. Plan terms are in the [terms](https://postfast.sh/terms).
- **MCP:** https://postfast.sh/api/mcp (Streamable HTTP, stateless). Sign in with OAuth 2.1 (authorization code, PKCE S256, dynamic client registration; you sign in to PostFast and approve) or send a PostFast API key as `Authorization: Bearer <key>`. Legacy equivalent: https://postfast.sh/api/mcp-oauth-dynamic.
- **Source:** AGPL-3.0, offered on request: [email support@postfast.sh](mailto:support@postfast.sh?subject=Source%20code%20request).

## Connect in 60 seconds

```text
/plugin marketplace add airdropfi/postfast-claude-plugin
/plugin install postfast@postfast-plugins
/reload-plugins
```

Then open `/mcp`, choose `postfast`, select Authenticate, sign in to PostFast and press Approve. You need a PostFast account (free to create) with a channel connected.

## Example prompts

You ask; the assistant prepares a draft; you review and press Post in PostFast.

- `Use PostFast to list my connected channels. Do not create anything.`
- `Use PostFast to draft a YouTube Short from https://example.com/clip.mp4 with the title "Launch day recap". Ask me for privacy and made-for-kids before you create the draft.`
- `Use PostFast to draft this TikTok video on my TikTok channel. Ask me for who can view it, comments, duet, stitch and commercial-content disclosure first.`
- `Use PostFast to list my posts from 2026-11-01 to 2026-11-15 and tell me each state exactly as returned.`

## Human oversight: what you can see, approve and revoke

- **Drafts only.** `createDraftPostTool` creates a DRAFT. It never publishes or schedules. The post goes out only when you open it in PostFast and press Post now or Add to calendar.
- **No deletion.** The AI cannot delete posts.
- **Your choices on TikTok.** Privacy, comments, duet, stitch and commercial-content disclosure are shown to you in the PostFast composer, and TikTok publishing needs your explicit choices there.
- **Approve or refuse a connection.** With OAuth you sign in to PostFast and approve the connection.
- **Revoke access.** You can revoke the OAuth connection or the API key in PostFast.

## Links

- Product: https://postfast.sh
- MCP page with setup (markdown: https://postfast.sh/mcp.md): https://postfast.sh/mcp
- llms.txt: https://postfast.sh/llms.txt
- Privacy: https://postfast.sh/privacy, terms: https://postfast.sh/terms, data deletion: https://postfast.sh/data-deletion
- Other ways in: [Cursor kit](https://github.com/airdropfi/postfast-cursor-kit), [Gemini CLI extension](https://github.com/airdropfi/postfast-gemini-extension)

## Details

A Claude Code plugin marketplace with one plugin, [`postfast`](plugins/postfast/README.md): draft YouTube and TikTok video posts (and posts for Bluesky, WordPress, DEV and Hashnode) in your PostFast account. You review every draft and press Post in PostFast.

## Install

```text
/plugin marketplace add airdropfi/postfast-claude-plugin
/plugin install postfast@postfast-plugins
```

From a shell: `claude plugin marketplace add airdropfi/postfast-claude-plugin` then `claude plugin install postfast@postfast-plugins`. Then `/reload-plugins`, open `/mcp`, choose `postfast` and Authenticate. Details are in [plugins/postfast/README.md](plugins/postfast/README.md).

## Layout

```text
.claude-plugin/marketplace.json     marketplace postfast-plugins
plugins/postfast/                   the plugin: manifest, .mcp.json, commands, skills
scripts/validate.mjs                offline validator (node scripts/validate.mjs)
```

## License

MIT, see `LICENSE`. The PostFast service is governed by its terms: https://postfast.sh/terms. The PostFast application itself is AGPL-3.0; source is available on request.
