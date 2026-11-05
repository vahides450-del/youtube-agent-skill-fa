---
name: yt-audit
description: >-
  Audit a YouTube channel end to end - packaging, consistency, the first
  fifteen seconds, and what to fix first. Use for "audit my channel", "why
  isn't my channel growing", "review my videos", or a pasted channel URL.
---

# yt-audit

An audit that lists twenty problems is a way of avoiding the one that matters. This ends in ONE fix.

## فارسی (Persian patch, 2026-11-05)

- Reply in natural spoken Persian (محاوره‌ای), the way the creator talks on camera, never a translated English
  template. Tool and brand names stay in Latin script (Claude, YouTube, CapCut).
- `hooks.json` carries `name_fa`, `shape_fa` and `example_fa` for each formula. The Persian examples are shapes
  only: rewrite them in the creator's own voice.
- The Python tools read Persian: Persian digits, ZWNJ (نیم‌فاصله), Persian fillers (اِ، خب، یعنی) and Persian
  formula patterns. Run them with `python` (on Windows `python3` is often a dead store stub).
- `hookscore.py` on Persian is a rough guide: its word lists are short, so never drop a hook only for its score.
  Judge it by ear too.
- Persian speech runs slower than English: estimate runtimes at about 115 words per minute, not 150.
- Never invent a number, result, price or claim. Write `{{عدد تو}}` and ask.

## Before you write

1. Read `~/.claude/youtube/voice.md` if it exists. That is the user's voice profile: how they talk
   on camera, the words they never use, who they are talking to, what they will not claim. If it
   does not exist, ask for **three of their own videos**, read or transcribe them, infer the voice,
   and write the file. A script in the wrong voice is worse than no script, because they have to
   read it out loud.
2. Never invent a number, a result or a source. If a figure would strengthen it and you do not have
   one, ask for it or write the line without it.

## What to look at, in this order

1. **The last ten titles, as a set.** Read them as a list, the way the channel page shows them. Do
   they promise different things? Run them through `../yt-package/title.py`. A channel where every
   title is the same shape has a format problem, not a title problem.
2. **The thumbnails, at feed size.** Shrink them. What survives? If three of them are unreadable at
   that size, that is the fix and nothing else matters yet.
3. **The first fifteen seconds of the three most recent.** Transcribe them and score with
   `../yt-script/hookscore.py`. This is where most channels lose.
4. **Upload rhythm.** Not frequency - CONSISTENCY. Six videos in one week and then nothing for a
   month is worse than one a fortnight forever.
5. **The retention shape**, if they can export it. `/yt-retention`.

## What to hand back

- The single biggest fix, named, with what to do this week.
- Three things that are already working, so they do not break them. Be specific; "your energy is
  good" is not an observation.
- What NOT to do yet, and why.

Never open an audit with praise you do not mean, and never end one with a list of twenty things.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
