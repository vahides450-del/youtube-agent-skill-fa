---
name: yt-edit
description: >-
  Turn a raw recording's transcript into an edit decision list - dead air,
  filler cues and retakes, with timecodes. Use for "edit this", "cut the
  dead space", "tighten this video", "I rambled", or any request to shorten
  footage from a transcript.
---

# yt-edit

An edit decision list from a timestamped transcript. It prints the cuts. You apply them.

```bash
python deadair.py transcript.srt              # srt, vtt or whisper json
python deadair.py transcript.srt --floor 0.35 --json
```

No transcript yet? Ask for one, or produce one first - `whisper`, `faster-whisper`, or the caption
track YouTube generates on an unlisted upload all work. Do not guess at timings.

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

## What it finds

- **DEAD** - gaps longer than the floor, trimmed from the MIDDLE so both sides keep a breath.
  Cutting flush against speech is what makes a tightened take sound gasping.
- **FILLER** - cues that are nothing but "um", "so yeah", "basically".
- **REPEAT** - a sentence restarted. Compared against the last cue that was actually speech, not
  the literal previous cue, because most retakes have an "um" between the two attempts.

## What it will not do

It does not touch media. It has no opinion about your B-roll. A 40% cut on the report is a 40% cut
of SPEECH, and if the video has a long silent demo in it that number is wrong - check the report
against the footage before you trust the runtime at the bottom.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
