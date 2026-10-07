---
name: ig-comment
description: >-
  Write comments on other people's Instagram posts and reels that sound like a
  person with a point of view, not a bot. Use when the user pastes a post or a
  reel and wants a comment, says "comment on this", "engage with this", "what
  should I say here", or wants a batch for their daily engagement round.
---

# ig-comment

Commenting is the best twenty minutes you can spend on Instagram, and the
easiest to waste. A comment near the top of a reel with 40,000 views gets seen
by more people than most accounts' own posts, and it's the one spot where a
stranger can tap straight onto your profile.

A generic comment is worse than none. It costs a tap that leads nowhere, and it
flags the account as an engagement-pod account to the one person whose opinion
counts: the creator.

## Input

The user pastes the post or reel text, or a screenshot, plus the account name.
If they share a URL you can't open, ask them to paste it. Don't use a browser
tool to scrape the feed, and don't post anything.

## Nine kinds of comment

Choose by what the post really is. Never default to type 1.

| # | type | when | shape |
| --- | --- | --- | --- |
| 1 | **Add a datum** | the post makes a claim you can back with a number | "Same here: 40% of..." |
| 2 | **Add the missing case** | the post is right but leaves something out | "True until {condition}." |
| 3 | **Respectful disagree** | you honestly think it's wrong | say what you agree with, then where you split |
| 4 | **Extend one line** | one line in it is the good one | quote it, build on it |
| 5 | **Ask the real question** | the post skipped the hard bit | one specific question |
| 6 | **The receipt** | you've done the thing they describe | what happened, two sentences |
| 7 | **The correction** | there's a factual mistake | be right, brief, kind and sure |
| 8 | **The reframe** | right facts, wrong frame | "Another way to look at it:" |
| 9 | **The one-liner** | the post needs nothing, you just want to show up | under 10 words, has to be funny or true |

## Rules

- **One to three sentences.** Comments are read in a skinny column under a
  video. A paragraph gets folded behind "more" and nobody opens it.
- **Never start with** "Great post", "Love this", "So true", "This 👏", "Needed
  this today", or the creator's first name plus an exclamation mark. Nobody
  sees any of them.
- **No comments that are only emoji**, and no emoji as the first character.
- **Don't repeat the reel back.** Everyone reading just watched it.
- **One idea.** Two points in a comment looks like a hijack.
- **Be specific.** If the comment would fit under any post on the topic, it
  isn't a comment, it's noise.
- **Never pitch.** Not the offer, not the link, not "check out my page". It's
  the quickest way to get blocked by exactly the person you wanted to reach.
- **Being early counts more here than anywhere.** A comment in the first hour
  on a reel that then takes off gets carried along with it.

## Output

Give **two options of different types**, labelled, and one line on which you'd
post and why. Run both through `/ig-human` first. Comments are short, so an em
dash or a stock phrase stands out even more than in a caption.

```
COMMENT OPTIONS  (on @acct's reel about pricing)

[6 · Receipt]
We put ours up 40% last March and lost exactly one client, the one eating half
our inbox. It took eight months to stop being scared of it.

[3 · Respectful disagree]
Agree on the anchoring. Where I'd push back is doing it mid-project. We tried
that and it cost us a renewal that was otherwise fine.

Post the first one. It gives something away and it has a number.
```

## Batch mode

For an engagement round, ask for 5 to 10 posts pasted in one message, send back
one comment for each in a single block, and keep a running list in
`~/.claude/instagram/log.md` of who's been commented on this week. Commenting on
the same three accounts every day is obvious, and it looks like exactly what it
is.

## Never

Don't auto-post, don't automate comments, and don't use a browser tool to
publish for the user. Automated engagement breaks Instagram's Terms of Use and
gets accounts action-blocked. This skill writes the comment. The user posts it.
