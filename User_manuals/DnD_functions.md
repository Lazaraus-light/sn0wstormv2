---
title: "For D&D players and DMs"
nav_order: 4
---

# Sn0wStormV2: a guide for D&D players

The bot can record your D&D sessions so the group gets a written transcript and session notes afterwards. **Nobody is recorded unless they say yes**, and you can change your mind at any time.

A server can run several campaigns at once, each with its own DM and players. Saying yes to one campaign doesn't mean you're recorded in the others.

## For players

### Join a campaign

Type `/dnd`, pick the campaign from the list, and type your character's name:

```
/dnd campaign: Ember Road   character: Aurel Vael
```

If the server only has one campaign, you can leave the campaign out: `/dnd character: Aurel Vael`.

This adds you to that campaign as that character, and it's how you say yes to being recorded during its sessions. Run it again with a new name if your character changes. You can play in several campaigns, with a different character in each.

### Check your status, or stop being recorded

- `/dnd` on its own lists the campaigns on the server and which character you play in each.
- `/dnd campaign: Ember Road` shows your character there, with an **Opt out of recording** button. It works straight away, even in the middle of a session.

### Don't want to be recorded?

Then simply don't join with `/dnd`. You can still play as normal: you just won't be in the recording or the notes.

## For the DM

These commands are for moderators.

| Command | What it does |
|---|---|
| `/dm setup` | Starts a new campaign. A box pops up asking for the **DM name** (how you appear in the notes) and the **campaign name**. You become its DM and are recorded as the DM. To have someone else run it, add `dm:` and pick them. |
| `/dm setup campaign: Ember Road` | Changes an existing campaign's names, or hands it to a new DM with `dm:`. Only its DM or an admin can do this. |
| `/dm roster campaign: Ember Road` | Gives you a small file with the campaign's players and characters, to use with the notes tool when you recorded with Craig or at the table. Sessions recorded with `/record` already include it. |
| `/dm delete campaign: Ember Road` | Ends a campaign. The bot asks you to confirm. The players' sign-ups are removed; saved recordings are kept. Only its DM or an admin can do this. |
| `/record start campaign: Ember Road` | Join the voice channel first, then run this. The bot joins the call and records that campaign's DM and players. If the server has only one campaign, you can leave the campaign out. |
| `/record stop` | Stops the recording and saves it. |

Only one session per server can be recorded at a time.

## During a session

- While recording, the bot's name starts with **🔴 REC**, so it's easy to see.
- When recording starts, the bot posts a list of who is and isn't being recorded.
- Anyone who joins the call later gets a message saying whether they're recorded.
- Only the DM and the players who joined **this** campaign with `/dnd` are recorded. Everyone else in the call is ignored completely.
- The bot doesn't speak or play sounds.
- Recording stops by itself if everyone has left the call for 2 minutes, or after 8 hours.

## After the session

The recording is turned into:

- a **transcript** of what everyone said
- a **session recap** for the whole party, like a "previously on…"
- **DM notes**, private to the DM: plot threads, NPCs, loot, ideas for next time
- **your own character notes**: a journal of what your character did and learned

The notes tool already knows who is who from the recording, so nobody has to type in player names. For now, the DM shares the recap and notes with the group. Everything is processed on the bot owner's own computer. Recordings are never sent to outside services. Norwegian and English are both fine, including mixed in the same sentence.

**Note:** your character notes are written by an AI, which tries to leave out things your character didn't see. It doesn't always get that right, so they might contain small spoilers.

## Your privacy

- You're only recorded after joining a campaign with `/dnd`, only in that campaign's sessions, and only between `/record start` and `/record stop`.
- Opting out stops future recording. To have earlier recordings deleted, ask the DM or the bot's owner.
- Read more in the [Privacy Policy](../PRIVACY.md).
