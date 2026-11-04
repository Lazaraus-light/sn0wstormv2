---
title: "For moderators and admins"
nav_order: 3
---

# Sn0wStormV2: a guide for moderators and admins

This guide covers the commands only staff can use. Members can't see these commands.

**Moderators** are people with permission to time out, kick, ban or manage messages, plus anyone with the server's mod role if one is set with `/setup modrole`. **Admins** also have Manage Server, which they need for the `/setup` commands.

What you do with the bot is posted in the **mod log** channel, so the whole team can see what happened. Warnings, timeouts, kicks and bans also get a case number.

## Moderating members

| Command | What it does |
|---|---|
| `/warn @member reason` | Gives a warning. The member gets a private message with your reason. Enough warnings automatically give a timeout, kick or ban, set with `/setup escalation`. Out of the box: **3 warnings in 30 days** give a 1-hour timeout. |
| `/strikes @member` | Shows a member's warnings that still count (the last 30 days, unless you've changed it). |
| `/clearstrikes @member` | Removes all of a member's current warnings. |
| `/note @member text` | Writes a private note for the moderators, for example after a friendly word. It isn't a warning, and the member isn't told. |
| `/case number` | Shows one case in full: what happened, to whom, by whom, when and why. Every action gets a case number, shown in the mod log. |
| `/reason number text` | Fixes the reason on a case, for example a typo. You can change your own cases; admins can change any. The bot's automatic cases can be changed by any moderator. The mod log shows the old and the new reason. (For a warning, the strike itself keeps its original text.) |
| `/history @member` | Shows everything on record for someone: warnings, timeouts, kicks, bans, notes and automatic removals, newest first. Use the **Previous** and **Next** buttons for older entries. For someone who has left, paste their user ID instead. |
| `/timeout @member duration reason` | Mutes a member for a while. Write the time like `10m`, `2h`, `1d` or `1h30m`. The maximum is 28 days. |
| `/untimeout @member` | Ends a timeout early. |
| `/kick @member reason` | Removes a member. They can come back with a new invite. |
| `/ban @member reason` | Removes a member for good. Add `delete_days` (0 to 7) to also delete their recent messages. |
| `/unban user_id reason` | Lifts a ban. You need their user ID (see below). |
| `/purge amount` | Deletes the last 1 to 200 messages in the channel you're in. Add `member:` to delete only that person's messages. It won't touch messages from people with the same or a higher role than yours; the bot tells you how many it left. **Deleted messages can't be brought back.** |

**Built-in safety:**

- Warn, timeout, kick and ban don't work on yourself, the server owner, or anyone whose role is as high as yours or higher.
- Moderators and admins can't be given warnings.
- The bot's role must sit above the people it moderates (Server Settings → Roles).

**Finding a user ID:** turn on Developer Mode (User Settings → Advanced), then right-click the person and choose **Copy User ID**. For banned users, look in Server Settings → Bans.

## Reports from members

Reports made with `/report` or **Report message** land in the reports channel, or in the mod log if no reports channel is set. Each report shows who reported whom, why, and any screenshot. Treat them as private.

Each report has buttons, so the team can see who is on it:

- **Claim**: shows the others you're handling it. Click again to let it go. Clicking a report someone else has claimed takes it over.
- **Warn** or **Timeout**: asks for a reason (and, for a timeout, how long), then works just like `/warn` or `/timeout`. The report is marked as resolved.
- **Dismiss**: closes the report without action, for example when it was a misunderstanding.

The report shows its status at the bottom, and closed reports lose their buttons. You can't handle a report about yourself; another moderator has to.

## Raids

A raid is when lots of accounts join at once to spam or harass. The bot watches for this: if many people join within a short time (10 in 30 seconds unless you change it), it posts an alert in the mod log listing the new accounts, and flags any that are only days old.

| Command | What it does |
|---|---|
| `/lockdown` | Closes the doors for a while (1 hour unless you add `duration:`, up to 24 hours). New members can't unlock the server by reacting to the rules (the bot removes their reaction and tells them to try again later), and the bot stops posting welcome messages. It also pauses invites to the server (if the bot was added without the Manage Server permission, it reminds you to do that yourself). |
| `/unlock` | Ends the lockdown early. Otherwise it ends by itself, and the mod log says so. |

During a lockdown, kick or ban the raid accounts as usual. Nobody already in the server is affected, and no channel settings are changed.

## Alerts you'll see in the mod log

- **Deleted and edited messages**, so nothing disappears unnoticed. If the text contains an ID number, the log says "withheld" instead of showing it, even when a moderator posted it.
- **Joins and leaves.** Accounts less than 7 days old are flagged, since they can be alts or people dodging a ban.
- **Name copying:** someone whose name looks like a moderator's, even with tricks like `S4ssi`
- **Join spikes** (possible raids), with the accounts that joined
- **Automatic removals** by the bot, and why. Removals of edited messages say "added in an edit".

## D&D sessions

Moderators run the D&D tools. The server can have several campaigns: `/dm setup` starts one (or edits one), `/dm roster` gives its player list for the notes tool, `/dm delete` ends one, and `/record start` and `/record stop` record a session. A campaign can only be changed by its DM or an admin. See the [D&D guide](DnD_functions.md).

## Server setup (admins only)

These need the Manage Server permission. `/setup show` shows the current settings.

| Command | What it sets |
|---|---|
| `/setup modlog #channel` | Where the mod log goes. Keep this channel staff-only. |
| `/setup reports #channel` | Where member reports go. Staff-only. |
| `/setup rules #channel` | Your rules channel, which the welcome message links to. |
| `/setup welcome #channel` | Where new members are greeted. Add `message:` to write your own greeting: `{user}` becomes their name, `{server}` the server name and `{rules}` a link to the rules. Use `message:default` to go back to the standard text. Leave the channel empty to turn welcomes off. |
| `/setup verification` | Lets people unlock the server by reacting to a post. Give it the link to the post (right-click → **Copy Message Link**) and the role to hand out. |
| `/setup modrole @role` | A role that counts as moderator, for teams that use a role rather than Discord permissions. People with it can use the report buttons, and they don't get warnings or automatic filters. They still can't act on anyone ranked at or above them. Leave the role empty to remove it. See the note below. |
| `/setup gallery #channel` | The channel where pictures and links belong. |
| `/setup media #channel restricted` | Turn on to only allow links and pictures in that channel when they're part of a conversation. |
| `/setup automod` | Turn the automatic spam and safety filters on or off, or change the mention limit. |
| `/setup raid` | How the bot reacts to a sudden wave of joins: `off`, `alert` (a message in the mod log, the default) or `lockdown` (alert and lock the server for an hour). You can also change how many joins in how many seconds count as a wave. |
| `/setup blockword add/remove word` | Words the bot removes automatically. It also catches tricks like `b4dw0rd`. |
| `/setup escalation` | What happens automatically when someone collects warnings. Choose how many warnings lead to a timeout (and how long), a kick, or a ban, and how many days a warning counts. Set a step to 0 to turn it off. Each step needs more warnings than the one before it. |

**Giving the mod role its commands:** Discord hides moderator commands from anyone without the matching permission, and the bot can't change that. If your mod role should use commands like `/warn`, open **Server Settings → Integrations**, pick the bot, and add the role to each command you want it to have. Only give it what you're comfortable with: a role allowed to use `/ban` can ban through the bot even if the role itself has no ban permission.

### Server themes

Swap the server's look for a holiday and put it back afterwards, without redoing everything by hand.

| Command | What it does |
|---|---|
| `/theme mapping name` | Saves how the server looks right now under a name, for example `standard`, `christmas` or `spooktober`: the server name, icon and banner, every role's name, colour and icon, and every channel and category name. If a theme with that name exists, add `overwrite:True` to replace it. |
| `/theme apply name` | Switches the server to a saved theme. Only what's different is changed. The bot first saves the current look as **previous**, so `/theme apply previous` undoes it. |
| `/theme list` | Shows the saved themes. |
| `/theme delete name` | Deletes a saved theme (the bot asks you to confirm). |

A good habit: save your normal look as `standard` before decorating for the first holiday. Roles and channels added after a theme was saved are left alone. The bot can only change roles below its own role (drag it higher in Server Settings → Roles), and the banner and role icons need boost level 2. Anything it couldn't change is listed afterwards and in the mod log. Renaming many channels can take a few minutes, because Discord limits how often a channel can be renamed.

### Locking the server until people accept the rules

1. Post the rules in the rules channel.
2. Run `/setup verification` with the link to that post and a role such as `@Member`.
3. In Server Settings → Roles, drag the bot's role above `@Member`.
4. Hide your other channels from `@everyone` and show them to `@Member`. Keep the rules and welcome channels visible to everyone.

If someone leaves and comes back later, the bot gives them the role again as long as their reaction is still on the post. If you set this up before that feature arrived and your post isn't in the rules channel, run `/setup verification` once more.

A ready-made set of rules is in [SERVER_RULES.md](../SERVER_RULES.md).
