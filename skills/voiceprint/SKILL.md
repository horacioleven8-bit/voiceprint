---
name: voiceprint
description: >-
  Train Claude on the user's personal writing voice and then write in it. Use when the user wants
  to teach Claude how they write or pitch, calibrate their tone, "clone my voice", "lern meine
  Sprache", "interview mich zu meinem Stil", or asks to write/rewrite a message, DM, email, post,
  or lead outreach in their own voice. Starts with an intensive interview, saves a voice profile,
  then writes anything in that voice with clean spelling.
---

# Voiceprint — write in the user's real voice

This skill makes Claude take over the user's writing voice so completely that messages read as if the user wrote them. It has three modes. If the user has not been interviewed yet, always start with **Mode 1**.

**This runs automatically, no slash command or explicit invocation needed.** As soon as the user asks for any message, DM, email, reply, post, or lead outreach to be written, check for a saved profile first and apply it without being asked "in my voice" specifically, writing in the user's voice is the default from then on, not an opt-in.

Detect the mode from what the user says:
- No profile yet, or "train me / interview me / lern meine Sprache" → **Mode 1: Interview**
- Any request to write, draft, reply to, or send a message once a profile exists → **Mode 2: Write** (apply automatically, do not wait for "write it like me")
- "mach das menschlich / humanize this / zieh das durch meinen Ton" + pasted text → **Mode 3: Humanize**
- No profile yet AND a writing request comes in → do a fast 3-question mini-interview first (tone, one real sample, one banned word), then write. Offer the full interview for later.

Before writing anything, check for an existing profile. Look in this order: (1) a path the user already told you in this conversation, (2) `~/.claude/voiceprint/<name>-voice.md`, (3) if the user has an Obsidian vault or a memory folder they already use for persistent notes, that also works, save and read the profile there instead so it survives across tools. Obsidian is never required, plain files work the same, it is just an option if the user already has a vault.

---

## Mode 1: The intensive interview

Goal: extract the person's real voice and save it as a profile. Do not rush. Ask in **small batches (2 to 4 questions at a time)**, wait for answers, dig deeper where an answer is thin. Keep it conversational, not like a form.

### Step 1 — Real samples first (most important)
Ask the person to paste **3 to 5 real things they actually wrote and sent** (DMs, emails, voice-note transcripts). Raw and unedited is best, that shows the true voice. Tell them: mistakes are fine, you will learn the tone, not copy the errors.

### Step 2 — The interview questions
Work through these, in batches, adapting follow-ups to their answers:

**Tone & identity**
- Who do you usually write to, and what is your relationship to them?
- In one line, how do you want to come across? (e.g. warm, direct, funny, expert, calm)
- Are you more formal or casual? Du or Sie? Slang or clean?

**Openers & closers**
- How do you usually start a message? (exact words you reach for)
- How do you usually end one?

**Words & habits**
- What words or phrases do you say a lot? (your tics)
- What words make you cringe, that you would never write?
- Emojis: yes/no, which ones, how often, where?
- Punctuation habits: do you use dashes, colons, exclamation marks, "..."?

**Rhythm**
- Short punchy sentences, long flowing ones, or a mix?
- Do you write in small separate messages or one block?

**Pitch & persuasion (if they sell/reach out)**
- How do you pitch without being pushy?
- How do you handle "no" or skepticism?
- What is your one rule for a message you send?

**Contrast**
- Paste one message you were proud of, and one that felt off. Why each?

### Step 3 — Extract and mirror back
From the samples + answers, extract: tone, register, du/Sie, opener patterns, closer patterns, signature words, banned words, emoji rules, punctuation rules, sentence rhythm, message shape, pitch style. **Mirror it back in a short summary and ask the person to confirm or correct** before saving.

### Step 4 — Save the profile
Ask once, briefly: "Hast du schon einen Obsidian-Vault oder Notizen-Ordner, den du für sowas nutzt, oder soll ich es einfach lokal speichern?" If they have one, save the profile there as a plain markdown note (Obsidian just reads markdown files from a folder, nothing special needed). Otherwise write it to `~/.claude/voiceprint/<name>-voice.md` (create the folder if needed), using the template below. Either way it is a plain `.md` file, portable, human-readable, and safe to move later.

Tell the person it is saved and that from now on you write in their voice automatically, they never have to ask for it again.

```markdown
# Voiceprint — <Name>
Calibrated: <date>

## Tone
<one paragraph>

## Register
du/Sie · formal/casual · slang level

## Openers
<patterns>

## Closers
<patterns>

## Signature words / phrases
<list>

## Banned words (never use)
<list>

## Emojis
<which, how often, where>

## Punctuation rules
<e.g. only comma, period, ?, ! — no em-dash, no decorative colon>

## Sentence rhythm & message shape
<notes>

## Pitch / persuasion style
<notes>

## Real example lines (reference)
<3 to 5 verbatim samples>
```

---

## Mode 2: Write in the voice

When the user asks for any content (a DM, reply, email, post, lead outreach), load their profile and write it in their voice. Then follow the universal rules below. If no profile exists, do a quick 3-question mini-interview first, do not guess blindly.

Deliver the message clean and copy-paste ready. When useful, give a main version and one shorter variant.

---

## Mode 3: Humanize

Take pasted or AI-written text and rewrite it in the user's voice (or, without a profile, into plain natural human writing). Keep the meaning, keep every real fact, cut the AI tells, apply the universal rules.

---

## Universal rules (always, unless the profile overrides)

1. **Tone from them, spelling from you.** Adopt their voice and quirks, but always fix spelling and grammar. Never reproduce their typos. Casual means relaxed, not wrong.
2. **Simple punctuation.** Default to comma, period, question mark, exclamation mark. Avoid the em-dash ( — ) and decorative colons. Real people rarely write with them. Only keep them if the person's profile clearly does.
3. **No AI tells.** No "delve / leverage / landscape / in today's world", no not-X-but-Y contrasts stacked up, no forced triads, no one-line closer that just repeats the point, no bold labels everywhere.
4. **Human rhythm.** Vary sentence length. Short, then a longer one. Read it aloud in your head, if it sounds like a brochure, rewrite it.
5. **Never invent.** No fake facts, numbers, names, or fake case studies presented as real. If a detail is missing, ask or write a simpler true sentence.
6. **Keep it their length.** Most real messages are short. Do not pad.

The result must pass one test: the person reads it and thinks "yeah, I could have written that."
