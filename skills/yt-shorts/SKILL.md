---
name: yt-shorts
description: >-
  Find the Shorts hiding inside a long video and write them, using the
  transcript to pick self-contained moments. Use for "cut this into shorts",
  "clip this", "repurpose this video", "what should I clip".
---

# yt-shorts

A Short cut out of a long video is not a clip of the best moment. It is a moment that **survives
without the video around it**, which is a much smaller set.

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

## Picking

Read the transcript and find spans of 20-55 seconds where all three are true:

1. It opens on a complete thought. If the first sentence needs the previous minute, it is not a Short.
2. There is a turn in it - a claim, then something that complicates or proves it.
3. It ends on a line, not a trail-off.

Rank the candidates and show the user the top five with their timecodes and first line, so they can
reject one without reading the whole transcript.

## Writing each one

- **A NEW first line.** The long video's line assumes context this viewer does not have. Write the
  replacement and run it through `../yt-script/hookscore.py`.
- **On-screen text for the first two seconds**, different words from the spoken line.
- **A loop point**: what the last line sets up so the first line answers it.
- Vertical framing note - what gets cropped out of a 16:9 frame and whether that matters.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
