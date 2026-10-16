# Red Arrows Team Bot

## Install
1. `npm install`
2. Copy `.env.example` to `.env`, paste your bot token (or set `DISCORD_TOKEN` on your host). Node 18.17+.
3. Developer Portal → Bot → enable **Server Members Intent** and **Message Content Intent**.
4. Invite with `bot` + `applications.commands` and **Administrator** (simplest) — or at least: Manage Channels/Roles/Messages/Nicknames, Ban/Kick/Moderate Members, View Audit Log, Move Members.
5. `npm start`, then in your server run:
   **`/setup staff_role:@Staff game_url:https://www.roblox.com/games/<id>/<name>`**
6. **Drag the bot's role to the very top** of Server Settings → Roles (needed for anti-nuke to punish people).

`/setup` automatically creates: Verified + Unverified roles, #welcome, #verify (with the panel), #applications (staff only), a ready-made `team` application form, modmail category + logs, a private Logs category (mod, automod, messages, members, voice, server, antinuke, verify…), and a temp-voice hub. Finally run `/verification lock` once to hide the server from Unverified members.

## What it does (automatically)
- **Anti-nuke** — watches the audit log. Mass channel/role delete or create, mass bans/kicks, webhook spam, dangerous permission grants and unauthorised bot adds are blocked. The culprit is banned (or kicked / stripped), things they created are deleted, deleted channels & roles are rebuilt, the raid shield turns on and the owner is DMed. Only the **server owner** can change settings or whitelist (`/antinuke`).
- **Roblox verification** — members enter their Roblox username and paste a one-time code into their profile description; the bot checks it via Roblox's public API, gives the Verified role and sets their nickname to their Roblox name. Returning members are re-verified instantly. Unverified members are kicked after 24h (configurable).
- **Game integration** — `/game info` live stats, `/game play` link, Play buttons on welcome messages, auto-announced game updates, live "Playing: N" voice channel, and the bot's status shows the player count. (`/gamesetup`)
- **Welcomer** — embed + optional DM + leave messages, with placeholders (`/welcome`).
- **Applications in DMs** — `/apply team`; answers are collected in DMs, staff accept/deny with buttons, applicant's verified Roblox profile is shown on the review card. Edit forms with `/form`.
- **Modmail** — members DM the bot; staff reply in a private thread; transcripts, ratings, snippets, claim, auto-close.
- **Automod** — spam, invites, scam/free-Robux phishing, repeated messages, links from brand-new members, mass mentions, caps, blocked words. Hits become warnings that escalate automatically (`/escalation`).
- **Raid shield, logs, warnings, bans, global bans across your servers, levels, giveaways, polls, reminders, suggestions, starboard, birthdays, temp voice** — see `/help`.

Data lives in `data/db.json` (back it up). Commands re-register only when their definitions change.
