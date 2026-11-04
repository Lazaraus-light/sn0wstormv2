---
title: "For members"
nav_order: 2
---

# Sn0wStormV2: a guide for members

Sn0wStormV2 is the server's helper bot. It welcomes new people, keeps spam away and gives you a private way to reach the moderators.

To use a command, type `/` in any channel and pick it from the list.

## Getting into the server

When you join, the bot says hello in the welcome channel. To unlock the rest of the server:

1. Read the rules in the rules channel.
2. Click the reaction under the rules post (usually ✅).

That's it: you'll see the other channels straight away. If the server is in a short lockdown (for example during a spam attack), the bot removes your ✅ and lets you know; just react again a bit later. If you remove your ✅, you lose access again. If you leave the server and come back, you get access back automatically as long as your ✅ is still there.

## Your commands

| Command | What it does |
|---|---|
| `/report @user` | Tells the moderators privately about someone breaking the rules. A box pops up for you to explain what happened. You can attach a screenshot, which is handy for messages sent to you in private. Nobody else sees your report. |
| **Report message** | Right-click a message (on a phone, press and hold it), choose **Apps**, then **Report message**. The moderators get a link to the message and your explanation. |
| `/feedback` | Tell the bot's developer about something that isn't working, or suggest an idea. You don't need a GitHub account. **What you write is published on a public web page**, without your name, so leave out personal details and anything about other members. The moderators of your server can see that you sent it. You can send 3 per hour. |
| `/boop` | Boop the bot's snoot, or boop someone else with `/boop @member`. Just for fun. |
| `/diagnostics` | Shows whether the bot is running smoothly. |
| `/dnd` | For D&D players: join a campaign as your character, or see and leave the ones you're in. See the [D&D guide](DnD_functions.md). |

You can send up to 3 reports every 5 minutes. Use them for real problems. For something urgent that's happening right now, ping the moderators instead.

## Things the bot does by itself

The bot quietly removes some messages to keep the server safe. If it removes yours, you'll see a short note explaining why, and it disappears after a few seconds.

- **Invite links** to other Discord servers
- **Program files** (like `.exe` or `.bat`), which are a common way to spread viruses
- **National ID numbers** (Norwegian fødselsnummer), to protect people's privacy
- **Blocked words** that the moderators have listed
- **Spam**: mentioning lots of people at once, or sending many messages in a few seconds. This also gives you a 5-minute timeout.
- **Links and pictures in the wrong channel**: in some channels, links and media are only allowed as part of an ongoing conversation. The bot will point you to the right channel.

Editing a message doesn't get around this: if you edit in an invite link, an ID number or a blocked word, the bot removes the message.

## Warnings

If a moderator warns you, the bot sends you a private message saying why. Collecting several warnings can lead to an automatic timeout, and on some servers a kick or ban. Unless the moderators have changed it, warnings count for 30 days and **3 warnings within 30 days** give you a 1-hour timeout. Ask the moderators if you're unsure how it works here.

Moderators can also keep private notes about members, for example that they had a friendly word with you. Notes aren't warnings and don't lead to timeouts.

If you think a warning or removed message was a mistake, talk to one of the moderators.

## Your privacy

The bot doesn't save your messages. If a message is deleted or edited, the moderators can see the old version in their private log. Messages containing an ID number are left out of that log. The bot records your voice only if you join a D&D campaign and say yes to recording. Anything you send with `/feedback` is public. Read the full [Privacy Policy](../PRIVACY.md) and [Terms of Service](../TERMS.md).
