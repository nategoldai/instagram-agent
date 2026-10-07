---
name: ig-audit
description: >-
  Review what the user has already posted - which reels actually worked, why,
  and what to stop making. Use when the user pastes their Instagram insights or
  past posts and asks "what's working", "why did this flop", "read my
  analytics", "audit my content", or wants to know what to make more of.
---

# ig-audit

The only reliable source on what works for an account is the account itself.
Every rule in every Instagram guide, this pack included, is a starting guess.
The user's last 30 posts are the actual evidence.

## Input

Ask for whatever the user has:

- Per-post insights: views, reach, interactions, watch time, saves, shares,
  follows, and what share of reach came from non-followers. Screenshots are
  fine.
- Or the retention graph for their best and worst recent reels. That one
  screenshot is worth more than everything else put together.
- Or just the posts with their view counts, which is enough to start.

Also read `~/.claude/instagram/log.md` if it's there, since it records which
hook formula each post used.

## What to measure

Raw views is the least useful number on the screen, because it mostly reflects
how many people already follow the account. Work these out instead and show the
maths:

| metric | how | what it tells you |
| --- | --- | --- |
| **Outlier multiple** | views / the account's own median views | whether it was a real hit or just a normal day |
| **Non-follower reach** | % of reach from non-followers | whether it travelled at all |
| **Hold at 3s** | viewers still watching at 3s / viewers who started | whether the hook worked. This is the hook's grade. |
| **Average watch time** | straight from insights | whether the middle worked |
| **Sends per reach** | shares / reach | the strongest single signal there is. A send is someone putting their name on it. |
| **Follows per reach** | follows / reach | whether the profile turned attention into followers |

Rank by outlier multiple and sends per reach, not views. A reel with 4,000
views and 90 sends beat one with 60,000 views and 11.

## Find the pattern

Put the top five and bottom five next to each other and look for what separates
them. Be ready to say something the user won't like:

- **Hold at 3 seconds.** If top and bottom differ here, it's the hook and
  nothing else, and everything after it is a distraction.
- **Hook formula.** Which ids from `ig-reel/hooks.json` show up in the top five?
- **Format.** Reel, carousel, single image.
- **Length.** Bucket into under 15s, 15 to 30s, 30 to 60s, over 60s.
- **Theme.**
- **Whether the user replied to comments in the first hour.**
- **Day and time.** Look at this **last**, and only if nothing else shows up.
  It's almost never the reason, and it's where people want the reason to be.

Write each finding as a claim with the evidence next to it, and say how sure you
are. Thirty posts can show a pattern. Six can't, and saying so beats making one
up.

## The distinction that saves months

**A reel that gets views but no follows didn't fail. That's a profile problem.**
A reel that gets no views is a hook problem. Separate the two before you
recommend anything. If non-follower reach is high and follows per reach is low,
stop rewriting hooks and go to `/ig-profile`.

## Output

```
AUDIT  ·  31 posts  ·  Jun 12 - Sep 5  ·  median views 4,100

TOP 5 BY OUTLIER MULTIPLE
  18.2x  #3  Nobody Tells You   74,600 views  62% non-follower  hold@3s 71%  128 sends
   6.4x  #1  Cost Confession    26,300 views  48% non-follower  hold@3s 64%   71 sends
  ...

BOTTOM 5
   0.3x  #11 Numbered            1,200 views  9% non-follower   hold@3s 31%    2 sends
  ...

WHAT THE DATA SAYS
1. Hold at 3 seconds explains it all. Top five average 66%, bottom five 33%.
   Everything else you're worrying about comes after the first two seconds.
2. Posts where you were the one who looked bad: mean 8.1x vs 0.9x for
   everything else. n=5. Strongest signal here by a wide margin.
3. Tool listicles get views and nothing more. Big reach, no sends, no follows.
   Three of your bottom five.
4. Day of the week shows nothing. Tuesday and Friday are within the noise.
   Stop tuning it.

STOP: listicles.
DO MORE: posts with a cost you paid and a number attached.
```

Then pass the conclusions to `/ig-plan`, so next week is built on the user's own
data instead of defaults, and to `/ig-viral`, so the swipe file gets narrowed to
the formulas that work for this particular account.
