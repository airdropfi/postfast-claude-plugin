# PostFast for Claude Code

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

Then open `/mcp`, choose `postfast`, select Authenticate, sign in to PostFast and press Approve.

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

Prepare video posts for your own channels with [PostFast](https://postfast.sh) without leaving Claude Code. The plugin connects Claude to the PostFast MCP server and adds two skills and two commands. The assistant only creates drafts; you review and publish in PostFast.

## What it contains

| Component | Name | What it does |
|---|---|---|
| MCP server | `postfast` (`https://postfast.sh/api/mcp`) | The eight PostFast tools. Sign-in is OAuth 2.1 with PKCE; there is no key to paste. |
| Skill | `draft-a-video-post` | Find the channel, read its schema, upload media, create a draft, tell you to press Post in PostFast. |
| Skill | `check-post-status` | List posts for a date range and report states as returned. Read-only. |
| Command | `/postfast:channels` | Your connected channels. Read-only. |
| Command | `/postfast:posts` | Your posts and their states for a date range. Read-only. |

## Install

You need a PostFast account (free to create) with a channel connected, and Claude Code.

```text
/plugin marketplace add airdropfi/postfast-claude-plugin
/plugin install postfast@postfast-plugins
/reload-plugins
```

From a shell: `claude plugin marketplace add airdropfi/postfast-claude-plugin` and `claude plugin install postfast@postfast-plugins`. Then open `/mcp`, choose `postfast` and select Authenticate. Try `/postfast:channels`.

To try it from a local checkout without a marketplace: `claude --plugin-dir ./plugins/postfast`.

## Using an API key instead of OAuth

Create an API key in PostFast Settings, in the Public API section, then add the server yourself with a header: `claude mcp add --transport http postfast https://postfast.sh/api/mcp --header "Authorization: Bearer YOUR_API_KEY"`. Keep the key out of chat and out of git.

## Tools

| Tool | Notes |
|---|---|
| `integrationList` | Lists connected channels; optional group id. |
| `groupList` | Lists customer groups. |
| `integrationSchema` | Settings and rules for a channel type (YouTube title, privacy, madeForKids; TikTok privacy, comment, duet, stitch, disclosure). |
| `triggerTool` | Read-only lookup of provider helper data such as tags or publications (WordPress, Hashnode). |
| `createDraftPostTool` | Creates a DRAFT post. Never publishes or schedules. |
| `postsListTool` | Lists posts between two UTC dates with state, channel and settings. |
| `postSettingsTool` | Changes settings of an unpublished post or draft. |
| `uploadFromUrlTool` | Copies a public image or video URL into the media library. |

## What it will and will not do

- It creates drafts only and tells you to open PostFast and press Post now or Add to calendar. It never claims a post was published.
- YouTube and TikTok settings come from you, not from the assistant.
- It cannot delete posts.
- It reports post states exactly as PostFast returns them.
- It never asks you to paste a key into chat.

## Data and privacy

The MCP server receives what the tools need: the captions, media URLs and settings you ask Claude to use, and the channel and post data on your PostFast account. This plugin stores nothing and runs no code on your machine; it is a server address, Markdown instructions and an icon. See the [privacy policy](https://postfast.sh/privacy), [terms](https://postfast.sh/terms) and [data deletion](https://postfast.sh/data-deletion).

## Support

https://postfast.sh/mcp or support@postfast.sh.

## License

MIT for the files in this repository (see `LICENSE`). The PostFast service is governed by its terms.
