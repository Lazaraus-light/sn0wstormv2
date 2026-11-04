---
title: "Privacy Policy"
nav_order: 6
---

# Sn0wStormV2 Privacy Policy

_Effective 4 November 2026_

Sn0wStormV2 is a moderation bot for Discord. This policy explains what information the bot
handles when it runs in a Discord server, why, where it ends up and how long it is kept.

The bot is run by its operator, **gramzon** on Discord. Send gramzon a direct message with any
question or request about the bot or your data. "We" below means the operator.

## The short version

- The bot stores **moderation records**: Discord user IDs, strike and case reasons, and
  timestamps. It also stores **server settings**.
- The bot **reads messages as they are sent** so it can enforce the server's rules, but it
  **does not save message history** in its own database.
- Some information, such as deleted messages, reports and moderation actions, is posted to
  **private staff channels in the Discord server**, where the server's moderators can see it.
- **D&D session recordings are opt-in.** The bot only records your voice if you opted in with
  `/dnd` (or set up the campaign as its DM), and only between `/record start` and
  `/record stop`. See [D&D session recordings](#dd-session-recordings).
- Nothing is sold, used for advertising or analytics, or shared outside Discord and the
  operator.

## What the bot stores in its database

| Data | Example | Why |
|---|---|---|
| Server settings | server ID, IDs of the mod-log, welcome, rules, reports and gallery channels, the verification post, its channel, emoji and role, the mod role, automod switches, blocked words, strike escalation and raid-protection settings, and when a lockdown ends | so the bot behaves the way the server's staff configured it |
| Strikes | server ID, your user ID, the moderator's user ID, the reason, when it was given | so repeated rule breaks lead to the escalation described in the server's rules |
| Moderation cases | server ID, the action (warn, timeout, kick, ban, unban, automod, note), your user ID, the moderator's user ID, the reason or note text, the duration, when it happened | a numbered record of moderation actions, so staff can be consistent and accountable. Notes are written by staff, aren't warnings, and you aren't notified of them |
| Report status | server ID, the reported user's ID, the report's status (open, claimed, resolved or dismissed), the moderator handling it, the outcome (e.g. "warned, case #12"), where the report message is | so staff can see who is dealing with a report and how it ended. The report's text and who sent it are **not** stored by the bot; they stay only in the reports channel |
| Server themes | for each saved theme: its name, who saved it and when, the server's name, icon and banner, role names, colours and icons, and channel and category names | so admins can switch the server's look between themes and back |
| D&D campaigns | for each campaign on a server: its name, the DM's user ID and DM name; for each player who opted in to that campaign: user ID, character name, when they opted in | to know whose voice may be recorded in which campaign, and how to label them |
| Recording log | server ID, voice channel ID, which campaign, who started the recording, where it's saved, start and end time | a record of when sessions were recorded |

Automod case reasons can include what triggered the rule, such as the invite link or file name.
They never include a national ID number.

**How long:** these records are kept until the operator deletes them, or until you ask for
them to be deleted (see [Your rights](#your-rights)). There is currently no automatic
deletion. Strikes stop counting towards escalation after 30 days (the server's staff can change this),
but they stay in the record.

**Backups:** the bot makes a copy of its database once a day and keeps the last 7 days (the
operator can change this). A record that is deleted therefore disappears from the backups
within that many days, too.

## What the bot processes without storing

These are used in memory while the bot runs and are never written to its database:

- **Message content, attachment file names, mentions and replies**, checked against the
  server's rules as each message is sent or edited. This is how the bot detects invite links,
  executable files, national ID numbers, blocked words, mention spam and media posted outside
  the gallery.
- **When you sent recent messages**: seconds for flood detection, and up to five minutes in
  media-restricted channels to tell whether a conversation is going on.
- **Usernames and nicknames**, compared with staff names to spot impersonation.
- **Account creation date**, to flag accounts younger than seven days when they join.
- **When members joined in the last few minutes**, to notice a raid (many accounts joining at
  once). If it looks like one, the mod log gets a list of those accounts with their usernames,
  user IDs and account ages.
- **Whether you've reacted to the verification post**, checked when you join, so a returning
  member gets their role back.

All of this is discarded when the bot restarts, and most of it much sooner.

## Error reports

If the bot hits an error, it sends a technical report to the operator (by Discord DM, or to a
private channel the operator chose). These reports are for fixing the bot. They usually
contain only code locations, but an error message can occasionally include an ID or a piece of
text the bot was handling at the time. They aren't stored by the bot.

## What the bot posts in Discord

Discord stores these posts like any other messages. The server's staff can see them and
delete them; the operator does not keep separate copies.

- **Mod log (staff-only channel):** the content of deleted and edited messages, with author
  and channel; joins, with username, user ID and account age; leaves; moderation actions and
  automod hits, with reasons; impersonation alerts; raid alerts listing the accounts that
  joined in a burst. When a deleted or edited message
  contains a national ID number, its content is withheld from the log, whoever posted it.
- **Reports (staff-only channel):** if you use `/report` or **Report message**, the report
  contains your username and user ID, the reported user's username and user ID, your reason,
  and a link to and short excerpt of the reported message. A screenshot you attach is copied
  into the report so it survives if the original is deleted. Attachments on a reported
  message are listed by file name only, never copied. The report shows its status and which
  moderator handled it.
- **Short public notices:** when automod removes a message, a brief notice mentioning you
  appears in the channel and deletes itself after a few seconds. New members are greeted in
  the welcome channel if the server has one.
- **Direct messages:** if a moderator warns, times out, kicks or bans you, the bot DMs you the
  action and the reason, if your DMs are open. If you react to the rules while the server is
  in lockdown, the bot DMs you to try again later.

## Operational logs

The bot writes technical logs (startup, errors, missing permissions) on the server it runs on.
These include server IDs and channel names, but not message content. They are rotated
automatically and capped at about 30 MB in total, so older entries are overwritten.

## D&D session recordings

The bot can record a D&D session's voice channel so the campaign gets a transcript and session
notes. This only applies to you if you opt in.

**Who is recorded.** Only the recorded campaign's DM (set with `/dm setup`) and the players who
opted in to **that campaign** with `/dnd`. A server can run several campaigns; opting in to one
doesn't mean you're recorded in the others. Everyone else in the channel is not recorded. Their audio is
discarded the moment it arrives, before it is even decrypted, and never written anywhere.

**When.** Only between a moderator's `/record start` and `/record stop`, or until the
recording stops by itself: when the channel has been empty for two minutes, after eight hours,
or if the bot is disconnected. While recording, the bot's name starts with `🔴 REC`, it posts
who is and isn't recorded, and it tells people who join whether they're recorded.

**What is saved,** on the operator's server:

- one audio file per person who spoke (Opus audio, as Discord sent it)
- a session file with the campaign name, and each participant's user ID, username, name,
  character, and how long they spoke. The local transcription software reads the names from
  this file, so they don't have to be typed in elsewhere

**What happens next.** The operator may turn the recording into a transcript and session notes
(recap, DM notes, per-character notes) using software that runs **locally on the operator's own
computer**. Recordings and transcripts are never sent to cloud transcription or AI services.
The session recap may be shared with the campaign's players, and DM notes only with the DM.

**How long.** Recordings are kept until the DM or the operator deletes them. There is no
automatic deletion yet. You can ask for your recordings to be deleted at any time.

**Withdrawing consent.** Run `/dnd campaign:<name>` and press **Opt out**. It takes effect immediately,
including in a session that's being recorded. Opting out doesn't delete earlier recordings by
itself; ask the operator if you want those deleted too.

## Who can see your data

- **The server's moderators and administrators**, through the bot's commands and the staff
  channels they configure.
- **The operator**, who runs the bot and manages the database, logs and recordings.
- **UpCloud**, the hosting provider. The bot runs on a server rented from UpCloud in Norway, so
  the database, logs and recordings are stored there on the operator's behalf.
- **The campaign's DM**, who receives the session recordings and notes for their campaign.
- **Discord**, which carries every message the bot sends and receives. Discord's own
  [Privacy Policy](https://discord.com/privacy) applies to that.

We don't share data with anyone else unless the law requires it. The bot does not use
third-party analytics, advertising or AI services.

## Why we're allowed to (legal basis)

Under the GDPR, the bot processes this data on the basis of **legitimate interests**
(Article 6(1)(f)): keeping the community safe and moderating it fairly. Removing messages that
contain national ID numbers exists to protect the person the number belongs to.

D&D session recordings are based on your **consent** (Article 6(1)(a)), given with `/dnd` or
`/dm setup`, separately for each campaign. You can withdraw it at any time with `/dnd` →
**Opt out**.

## Your rights

You can ask the operator to:

- give you a copy of the moderation records (including staff notes), or recordings, about you
- correct records that are wrong
- delete records about you
- restrict how they're used, or object to them being used

Message **gramzon** on Discord. We'll respond within one month.
A request to delete a record may be declined while it is still needed to handle an ongoing
moderation issue; if so, we'll tell you why.

Messages the bot has posted in a server's channels belong to that server. Ask its staff to
remove them, or contact the operator and we'll pass the request on.

If you think your data has been mishandled, you can complain to your data protection
authority. In Norway that is [Datatilsynet](https://www.datatilsynet.no).

## Security

The database and recordings are stored on a server the operator rents from UpCloud in Norway, in
a locked-down container.
They are not exposed to the internet. The bot's credentials are kept as encrypted deployment secrets and never
stored in the source code.

## Children

Discord requires users to be at least 13, or older where local law says so. The bot does not
knowingly collect any information about age.

## Changes

If this policy changes, the effective date above will change too. Significant changes will be
announced in the servers that use the bot.
