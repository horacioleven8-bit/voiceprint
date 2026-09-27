# voiceprint

Train Claude on **your** personal writing voice, then have it write anything in your tone, automatically, from then on.

## What this actually does

When you install this, Claude gains a new skill. The first time you write to it, it interviews you, your tone, how you open and close messages, words you use a lot, words you'd never use, emojis, punctuation, how you pitch, how you handle "no". It also asks for 3 to 5 real messages you've actually sent, because real samples teach it more than any description can.

From your answers, it builds a **voice profile**, a plain text file saved on your machine (or in your Obsidian vault / notes folder, if you have one and tell it so). Nothing fancy, just a markdown note you could open and read yourself.

After that, **you never have to ask for it again.** Every time you ask Claude to write a DM, an email, a reply, a post, or outreach to a lead, it writes it in your voice automatically, clean spelling and grammar, simple punctuation (no em-dashes, no decorative colons, just comma/period/question mark like a real person types), no AI-sounding filler. You can also paste any text, yours, a colleague's, an AI draft, and say "humanize this in my voice" to rewrite it the same way.

**It never sends anything for you.** It writes, you send. Nothing here automates outreach or touches your accounts, that part stays fully in your hands.

---

## Install (2 steps, then it just works)

Open Claude Code and paste this in, exactly as it is:

```
/plugin marketplace add horacioleven8-bit/voiceprint
/plugin install voiceprint@voiceprint
```

Then reload:

```
/reload-plugins
```

That's it. No setup, no config. Just start talking to Claude like normal, next time you ask it to write something, it will offer to learn your voice first if it hasn't yet.

## How to use it

**Train it (once, takes a few minutes):**
Say "interview mich" or "lern meine Sprache" or just ask Claude to write something, if there's no profile yet it will offer to interview you on the spot.

**Write in your voice (automatic from then on):**
"Schreib mir eine DM für Lead X." No need to say "in my voice", that's the default now.

**Humanize existing text:**
Paste anything and say "zieh das durch meinen Ton" or "humanize this."

## Where your profile lives

A plain `.md` file, either at `~/.claude/voiceprint/<name>-voice.md` or in your own Obsidian vault / notes folder if you point it there during setup. You can open, read, or edit it yourself any time, it's just text.

---

MIT License. Built by Horacio Leven (HavnOne).
