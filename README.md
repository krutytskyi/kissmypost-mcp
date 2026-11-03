# KissMyPost: Reddit Audience Research (MCP server)

Reddit analytics and audience research for AI assistants: find subreddits for a topic, see who is in them, the best time to post, posting rules and Reddit brand mentions. KissMyPost works as a subreddit finder and Reddit marketing tool: subreddit growth and audience stats, similar subreddits, trending topics, Reddit post and mention search, and threads worth a reply. Not affiliated with Reddit, Inc.

Reddit audience data for your AI assistant. Ask about any subreddit or brand and get answers from KissMyPost data instead of guesses: how big a subreddit is and whether it is growing, when to post there, which subreddits are similar or share its audience, who the regulars are, and how often Reddit mentions a brand or a phrase.

- **Endpoint:** `https://kissmypost.com/api/mcp` (remote, Streamable HTTP)
- **Auth:** an API key sent as `Authorization: Bearer kmp_…` (free account at [kissmypost.com/mcp](https://kissmypost.com/mcp)), or OAuth sign-in in clients that support it
- **Registry:** [`com.kissmypost/mcp`](https://registry.modelcontextprotocol.io/v0.1/servers/com.kissmypost%2Fmcp/versions/latest) in the official MCP Registry
- **Claude:** listed in the [Claude Directory](https://claude.ai/directory/kissmypost)

This repository holds the public description of the hosted server (`server.json`) and setup instructions. The server itself is hosted by KissMyPost; there is nothing to install or run locally.

## Tools

All tools are read-only.

| Tool | What it returns | Example prompt | Plan |
|---|---|---|---|
| `search_subreddits` | Subreddits whose name matches a keyword, with members and monthly posts | Find subreddits about woodworking. | free |
| `find_subreddits_by_topic` | The most active subreddits about a topic | Which subreddits talk about home espresso? | free |
| `subreddit_overview` | Members, 12-month growth, posts and authors per month, top topics, main language | How big is r/SaaS and is it growing? | free |
| `best_time_to_post` | Best day and hour (UTC), whether timing matters, where the active audience is | When should I post in r/startups? | free |
| `similar_subreddits` | Up to 10 subreddits with similar topics and 10 with an overlapping audience | Which subreddits are like r/Entrepreneur? | free |
| `brand_mentions` | How often Reddit links to a brand: monthly mentions, top subreddits and topics | Where on Reddit do people talk about notion.so? | free |
| `top_subreddits` | The largest, fastest-growing and most active subreddits, overall or by topic | What are the fastest-growing fitness subreddits? | free |
| `reddit_statistics` | Headline Reddit numbers: monthly active posters, posts, comments, countries | How many people post on Reddit each month? | free |
| `explore_topics` | Where a topic sits on the map of Reddit topics and which subreddits lead its area | What does Reddit talk about around sourdough? | free |
| `subreddit_audience` | Who the regulars are: share of women, median age, where else they hang out | Who are the people in r/espresso? | free |
| `compare_subreddits` | Two subreddits side by side: overlap, gender and age, interests | How are r/running people different from r/bicycling people? | free |
| `search_research` | KissMyPost studies of Reddit data with short answers, dates and dataset DOIs | Is there data on karma requirements for new accounts? | free |
| `search_reddit_mentions` | How often posts and comments mention a phrase, month by month, and where | How often has Reddit mentioned Cursor IDE in the last two years? | free account |
| `search_reddit_posts` | The most relevant posts for a phrase: title, subreddit, month and link | Find Reddit posts asking for a Notion alternative. | paid |
| `subreddit_posting_rules` | What a subreddit allows (links, images, crossposts) and how often posts get removed | Can I post a link to my blog in r/marketing? | paid |
| `where_to_post` | Subreddits where similar posts live and how they scored, best day and hour | Where and when should I post about my CRM for freelancers? | paid |
| `reply_radar` | Fresh threads in your subreddits that are worth a reply, with a suggested angle | Which new threads in r/SaaS should I reply to today? | paid |

Free accounts have daily limits; current limits and plans are on [kissmypost.com/mcp](https://kissmypost.com/mcp) and [kissmypost.com/pricing](https://kissmypost.com/pricing).

## Setup

Get a free API key at [kissmypost.com/mcp](https://kissmypost.com/mcp) and replace `kmp_YOUR_API_KEY` below. Step-by-step instructions for 20 clients (ChatGPT, Claude, Gemini, Codex, Zed, JetBrains, n8n and more) are on the same page.

**VS Code (GitHub Copilot)** — `MCP: Open User Configuration`, or `.vscode/mcp.json` in a project:

```json
{
  "servers": {
    "kissmypost": {
      "type": "http",
      "url": "https://kissmypost.com/api/mcp?src=github",
      "headers": { "Authorization": "Bearer kmp_YOUR_API_KEY" }
    }
  }
}
```

**Cursor** — `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "kissmypost": {
      "url": "https://kissmypost.com/api/mcp?src=github",
      "headers": { "Authorization": "Bearer kmp_YOUR_API_KEY" }
    }
  }
}
```

**Claude Code:**

```bash
claude mcp add --transport http kissmypost "https://kissmypost.com/api/mcp?src=github" --header "Authorization: Bearer kmp_YOUR_API_KEY"
```

Treat the key like a password. If it leaks, revoke it on [kissmypost.com/mcp](https://kissmypost.com/mcp) or in your account settings.

## Data

Statistics come from public Reddit activity, aggregated by KissMyPost. NSFW communities are skipped.

## Links

- Website: https://kissmypost.com
- Privacy: https://kissmypost.com/privacy
- Terms: https://kissmypost.com/terms
- Support: hi@kissmypost.com

## License

The contents of this repository (documentation and `server.json`) are MIT licensed. The hosted service is covered by the [KissMyPost terms](https://kissmypost.com/terms).
