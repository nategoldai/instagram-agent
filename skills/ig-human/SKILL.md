---
name: ig-human
description: >-
  Remove the machine fingerprint from any draft - em dashes, AI slop words,
  invisible watermark characters - and score it on a five-check detection panel
  before it goes out. Use whenever text needs to sound human, when the user says
  humanize, "does this sound like AI", "remove the em dashes", "de-slop this",
  "this sounds like ChatGPT", or before showing the user any caption, script,
  comment, reply or DM.
---

# ig-human

There are two tools in this folder and both of them really run. Use them. Don't
judge this by eye.

```bash
python3 humanize.py draft.txt --report        # clean it, show what changed
python3 detect.py draft.txt                    # score it, five checks
python3 detect.py before.txt after.txt         # show the improvement
```

Both read `slop.json`: 154 stock words and phrases with plain-English swaps, 18
classes of invisible character, 11 typographic substitutions and 16 structural
tells. The last block of each list is Instagram-specific, the words that only
turn up in captions and voiceovers. It's meant to be edited. If the user has a
word they always say that the list strips out, remove it from the file.

## Why this matters more on Instagram than you'd think

Captions are short and scripts are spoken. One written-sounding line in a
600-character caption is a bigger chunk of the text than the same line in an
essay, and a voiceover nobody could say naturally gives itself away on the first
take. The giveaway isn't a detector flagging the post. It's someone scrolling
past something that sounds like a brand, or a creator tripping over their own
script.

## What gets fixed automatically

**1. Invisible characters.** Zero-width spaces and joiners, word joiners, soft
hyphens, byte-order marks, Unicode tag characters, invisible separators,
non-breaking and narrow spaces. Keyboards don't type these. They survive
copy-paste, no editor shows them, and they're the most mechanical trace in
generated text. `humanize.py` removes all of them, plus any other Unicode format
character it doesn't have a name for.

**2. Typography.** Em dash to comma, en dash to hyphen, curly quotes to
straight, ellipsis to three dots, bullet character to hyphen. The em dash pass
is the important one: it turns the dash into a comma, then tidies up the double
punctuation and stray periods that leaves behind.

**3. The slop list.** delve, leverage, robust, seamless, crucial, testament to,
"in today's fast-paced world", plus the Instagram block: "stop scrolling", "in
today's video", "follow for more", "tag someone who needs this", "the algorithm
loves", "run don't walk". Each one gets swapped for a plain word or removed,
with capitals kept and URLs left alone.

## What does NOT get fixed automatically

Structural tells get **flagged, not rewritten**, because reshaping a sentence
takes judgement:

- "It's not just X, it's Y" and "not only X but also Y"
- Groups of three
- One-word rhetorical question lines: "The result?"
- The video intro: "in this video I'm going to show you"
- Emoji bullet lists
- Three or more shouted words in a row
- Walls of hashtags
- Reflex bait: "follow for more", "tag someone who", "double tap if"

That list is on you. Rewrite every flagged line by hand, keep the meaning, then
run `detect.py` again. This is what moves the score from REVIEW to PASS, and
it's the part no script can do.

## The five checks

`detect.py` scores five signals from 0 to 100, where higher is more human:

| check | what it measures | machine-like looks like |
| --- | --- | --- |
| BURSTINESS | variation in sentence length | every sentence the same length |
| SPECIFICITY | numbers, names, concrete details per 100 words | abstract nouns, no figures |
| SLOP DENSITY | list hits per 100 words | stock vocabulary |
| FINGERPRINT | invisible chars, em dashes, curly quotes per 1k chars | typographically perfect |
| VOICE | contractions, person, structural tells | no contractions, staged reveals |

The verdict is 60% the average and 40% the **single weakest check**, because one
bad signal is enough to give it away. PASS needs 70+ overall and no check under
55.

## Be honest about this

These are five local heuristics based on the signals public detectors look for.
They run entirely on the user's computer and nothing is uploaded. They are
**not** GPTZero, Originality, Copyleaks, Winston or Turnitin, they don't call
those services, and they can't guarantee those results. Fixing what they measure
usually does move those scores, because they're measuring the same underlying
things. That's the claim. Don't make a bigger one for the user, and never tell
them their text is undetectable.

## Order of steps

1. `humanize.py draft.txt -o clean.txt --report`
2. Read the structural flags. Rewrite those lines yourself.
3. `detect.py draft.txt clean.txt` to show before and after.
4. If it's not PASS, fix the weakest check named in the output and go again.
   Two rounds is normal. Five means the draft was written to a formula, and the
   answer is a new draft, not more rounds.
5. Show the user the cleaned text and the score together. Never just the score.
