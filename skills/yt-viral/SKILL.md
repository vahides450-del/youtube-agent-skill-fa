---
name: yt-viral
description: >-
  Find what is actually working in the user's niche on YouTube and rank it
  by how far each video beat its own channel, then name the formula. Use for
  "what's working right now", "find viral videos in my niche", "why did this
  blow up", competitor research, or a swipe file.
---

# yt-viral

Raw view counts rank channel size, not ideas. This ranks by **multiple over each channel's own
median**, which is the only version of the question that is about the video.

```bash
python swipe.py collected.json --min 2.0
```

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

## Collecting the input

You need at least **four videos per channel** or a median means nothing, and the tool will skip the
channel and tell you it did. Collect them however the user prefers - `yt-dlp --flat-playlist -J`
against a channel URL is the fastest, the public page works, a manual list works.

```json
[{"channel":"...","title":"...","views":412000,"url":"...","duration":613}]
```

**Read, do not scrape.** Public listings only, never a logged-in session, never the user's own
account credentials.

## Reading the output

The multiple is the signal. The formula line is a judgement about the TITLE, matched against
[the 21 formulas](../yt-script/hooks.json) - it is not a claim about why the video worked, and you
should say so when you present it.

What to hand back: the top five with their multiples, the formula each used, and the ONE structural
thing they share. Then the harder line - which of those the user could actually make this week, in
their voice, with what they have.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
