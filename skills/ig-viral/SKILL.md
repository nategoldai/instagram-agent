---
name: ig-viral
description: >-
  Find the reels that are genuinely working right now in the user's niche, rank
  them by how far each one beat its own account, name the hook formula behind
  each, and turn it into a swipe file they can film from. Use when the user says
  "find viral videos", "what's working right now", "what are people posting in
  my niche", "reverse engineer this account", "build me a swipe file", "why is
  this reel blowing up", or asks what to make next with no evidence to go on.
---

# ig-viral

The research skill. Everything else in the pack writes; this one goes out and
looks. Run it once a month, not every day. Formulas last about a season.

There's one tool in this folder and it runs:

```bash
python3 swipe.py captured.tsv --out ~/.claude/instagram/swipe.md
```

## The one idea that makes this worthwhile

**Raw views prove nothing.** An account with two million followers getting
400,000 views just had a slow Tuesday. An account with four thousand followers
getting 400,000 views found something, and that something can be copied.

So everything here is ranked by **outlier multiple**: views divided by that
account's own recent median. Over 3x is a signal. Under 1.5x is just that
account's normal day and teaches you nothing, however big the number looks.

Pick accounts **within roughly 10x of the user's own size**. Something that
works at 2M followers often only works because it's at 2M followers.

## Step 1: choose the accounts

Ask the user for 6 to 12 accounts, or suggest some and get a yes:

- **4 direct** - same niche, same offer, a bit further along.
- **4 adjacent** - different niche, same audience. Formats get borrowed from
  here before anyone in the niche has them.
- **2 to 4 outsized** - much bigger accounts, for format only, never for how
  often they post or their tone.

Also ask them to open their own **Saved collection**. It's the quickest, most
relevant source there is, and it's already filtered by their taste.

## Step 2: go and look

Use whatever browser tool this session has: an in-app browser, an extension
connected to the user's own Chrome, or a computer-use tool. There's no API for
this and there doesn't need to be, because the amount is small enough to read
by hand.

**Non-negotiable rules:**

- **Never log into Instagram for the user and never ask for a password.** If a
  page needs a login, the user is the one already logged in. Drive their browser
  with them there, or ask them to paste.
- **This is reading, not scraping.** Ten accounts, about a dozen reels each, at
  human speed. Automated collection at scale breaks Instagram's Terms of Use and
  gets accounts action-blocked. Don't build a crawler, don't use a scraping
  service, and don't run this in a background loop.
- **Copy the formula, never the video.** The hook shape, the structure, the
  length, the pattern of cuts. Not their script, not their voice, not their
  edit. Credit every row in the swipe file to the account it came from.

**What to record for each reel**, in the creator's own words:

| field | notes |
| --- | --- |
| account | handle |
| followers | from the profile |
| median | look at the last 12 reels and take the middle view count |
| views | this reel |
| hook | the first line, spoken or on screen, word for word, bad grammar included |
| on-screen | the first text card, if it's different |
| length | seconds |
| cta | what they asked for at the end |

Median is the one that matters. Without it you're back to ranking by follower
count, which is exactly what this skill is here to stop.

**When Instagram won't show you enough:** the same hook patterns run on YouTube
Shorts, where view counts and transcripts are public and no login is needed.
It's a legitimate second source, and the spoken hook is easier to get:

```bash
# view counts for a channel's shorts
python3 -m yt_dlp --flat-playlist --playlist-end 40 -J \
  "https://www.youtube.com/@HANDLE/shorts" > channel.json

# the spoken first line of one short, from its auto-captions
python3 -m yt_dlp --skip-download --write-auto-subs --sub-langs "en.*" \
  --sub-format json3 -o hook "https://www.youtube.com/watch?v=VIDEO_ID"
```

Take every caption word stamped under 3.0 seconds. That's the hook as it was
said, not as it was written.

## Step 3: rank it

Fill in a tab-separated file with a header row and run the script:

```
account	followers	median	views	hook
@someone	48000	11000	412000	nobody tells you your first 30 reels are supposed to flop
```

```bash
python3 swipe.py captured.tsv --out ~/.claude/instagram/swipe.md
```

It works out the outlier multiple, names the hook formula using the same 26
formulas `/ig-reel` writes from, scores each hook with `hookscore.py`, and
prints what sets the top third apart from the bottom third.

## Step 4: explain what it means, carefully

Report three things, nothing more:

1. **Which formulas show up most** in the top third, with counts. Two formulas
   showing up four times each across six accounts is a finding. One showing up
   twice isn't.
2. **What the top third share structurally** that the bottom third don't: hook
   length, whether the payoff is visual, whether the first frame moves, where
   the ask sits.
3. **The unclassified rows.** Every hook the classifier couldn't name is either
   noise or a formula `hooks.json` doesn't have yet. Read them yourself. It's
   the most valuable part of the output, and it's why the script prints the
   count.

Then state the sample size and how confident you are, in plain words. Forty
reels across six accounts backs up a claim. Twelve doesn't, and saying so is the
difference between research and horoscopes.

## Step 5: turn it into something to film

For the top three formulas, write **the user's own version**: their story,
their number, in the shape that's working. Pass each one to `/ig-reel` with the
formula id already picked.

Never hand back "make a reel like this one". Hand back a hook line they could
say tomorrow.

## Output

```
SWIPE  ·  38 reels  ·  7 accounts  ·  baseline: account median

OUTLIERS (above 3x)
  38.4x  hook 86  #3  Nobody Tells You   @acct_a    412,000  (median 10,700)
  11.2x  hook 79  #9  The Steal          @acct_c    180,000  (median 16,100)
  ...

WHAT IS OVER-INDEXING
  #3 Nobody Tells You   x5 in the top third, 0 in the bottom
  #2 Negative Command   x4
  median hook length    8 words up top, 19 at the bottom

UNCLASSIFIED (6)
  Two of these share a shape that isn't in hooks.json: a hook that opens by
  reading someone else's comment out loud. Worth adding.

YOUR VERSION
  #3  "Nobody tells you your first 20 proposals are meant to lose."
  ...
```

Save the swipe file to `~/.claude/instagram/swipe.md`. `/ig-reel` and
`/ig-plan` both read it, and that's the point: after one run, the rest of the
pack works from the user's own evidence instead of defaults.

This skill doesn't post, follow, like or message anything. It only reads.
