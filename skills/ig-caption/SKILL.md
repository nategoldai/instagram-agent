---
name: ig-caption
description: >-
  Write the Instagram caption - the line that survives the "... more" cutoff,
  the body, the one ask, the search terms and up to five hashtags - and lint it
  before it goes out. Use when the user says "write the caption", "caption
  this", "what goes in the description", has a reel or carousel ready and needs
  the text, or asks about hashtags.
---

# ig-caption

There's one tool in this folder and it runs:

```bash
python3 caption.py caption.txt
python3 caption.py caption.txt --keywords "client proposals,agency pricing"
```

It prints the caption the way the feed shows it: the first 125 characters in a
box, and everything else hidden behind the tap. Read that box before anything
else you wrote.

## First, work out which job this caption has

Skipping this step is what ruins captions.

**Job A: the video already did the hooking.** A Reel has its own hook in the
first two seconds, spoken and on screen. The caption isn't a second hook, and
fighting the video for attention loses both. Its job is the ask, the context
that makes the ask make sense, and the words people search for.

**Job B: the caption is the content.** A photo, a single image, or a carousel
cover that opens a loop. Here the first line is the hook, and it works just like
a Reel hook: concrete, short, and cut off at a cliffhanger instead of mid-phrase.

Work out which one you're writing. If the user has a Reel with a strong hook,
write Job A and explain why.

## The shape

```
Line 1      125 characters of visible space. Job A: the ask, said plainly.
            Job B: the hook.
            Never a greeting, never a hashtag, never an emoji as the first
            character.
Body        short paragraphs with a blank line between each. Two to six of
            them. The search terms go here.
The ask     one. Comment a keyword, save it, or DM. Just one.
Hashtags    up to five, on their own line at the bottom, or none.
```

The limit is 2,200 characters and hardly anything needs that many. A caption
that earns the tap and then gives 600 characters beats one that gives 1,800.

## Hashtags, honestly

Hashtags don't drive reach any more, and Instagram has said so with an actual
product change. **On 18 December 2025 Instagram capped hashtags at five per
post**, down from thirty, telling creators that "using fewer (up to 5) more
targeted hashtags, rather than many generic ones" works better. Adam Mosseri had
already said in February 2025 that hashtags don't increase reach and work as
labels, not as a distribution lever.

So: up to five, specific, used as topic labels. If the user has a saved block of
twenty in their notes app, that block is dead weight now and the linter will
fail it.

`#viral`, `#fyp`, `#explorepage` and `#foryou` describe nothing. Cut them.

## Search terms now matter more than hashtags

Instagram search reads caption text. So the phrase the user wants to be found
for goes in the caption the way a person would type it, inside a normal
sentence. "Client proposals" as words in line three, not "#clientproposals" in a
block at the bottom.

Ask for two or three of those phrases, then give them to the linter:

```bash
python3 caption.py draft.txt --keywords "client proposals,agency pricing"
```

## Rules

- **No links in the caption.** Captions aren't clickable. A URL in the body is
  dead text that says "I don't really use this app". Use the bio or a DM.
- **One ask.** Two asks equals none. `caption.py` counts them.
- **A keyword ask needs a word people can type.** One word, no spaces, no emoji,
  and say it out loud in the video as well. `Comment CONTRACT` works.
  `Comment "the contract guide"` doesn't.
- **Write the first comment separately** if there's a link involved. Mention it
  in the receipt.
- **Emoji are punctuation, not decoration.** The linter flags anything over 4
  per 100 characters.
- **Alt text is worth 20 seconds.** Write it for carousels and photos. Screen
  readers and Instagram both read it.

## The loop

1. Decide Job A or Job B and say which one.
2. Write the draft.
3. Run it through `/ig-human`. Captions are short, so slop sticks out more here
   than anywhere else in the pack.
4. Run `caption.py` with the user's search terms. Fix every FAIL. Make a call on
   every WARN out loud, not quietly.
5. Print the ready-to-paste block, then the receipt:

```
CAPTION READY
job:        A - the reel carries the hook
visible:    118 of 125 characters used before the cut
ask:        one, comment CONTRACT
hashtags:   3
search:     "client proposals" in line 3, "agency pricing" in line 5
linter:     READY
```

Nothing gets posted. The user pastes it in.
