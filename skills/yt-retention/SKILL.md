---
name: yt-retention
description: >-
  Read a YouTube Studio audience-retention export and find where viewers
  actually leave, then say what to change. Use for "why do people stop
  watching", "my retention is bad", a pasted retention chart or CSV, or "fix
  my pacing".
---

# yt-retention

The retention graph is the only honest feedback YouTube gives you. Almost nobody exports it.

```bash
python retention.py retention.csv --duration 600
python retention.py retention.csv --transcript transcript.srt
```

Getting the file: Studio -> a video -> Analytics -> Engagement -> the audience-retention chart ->
the download icon -> "Audience retention".

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

## Three different problems

- **HOOK LEAK** - what is lost in the first 30 seconds. Under 25% is healthy. This is always the
  first thing to fix and it is always the first fifteen seconds of script, never the edit.
- **CLIFFS** - single steep drops. A cliff is a moment: a topic change with no signposting, a
  sponsor read, a long setup. With `--transcript` the tool prints what was being said there, which
  is what makes the report actionable instead of interesting.
- **SLIDE** - the steady bleed across the middle. A flat slide is pacing. The fix is cutting, not
  rewriting.

## What to hand back

Name the single biggest leak and one change for it. Not a list of five. Then, only if asked, the
rest. And if the hook leak is healthy and the slide is flat, say the video is fine and the problem
is packaging - send them to `/yt-package`.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
