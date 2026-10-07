---
name: ig-plan
description: >-
  Plan the week on Instagram - what goes up, in which format, when, and who to
  engage with. Use when the user says "plan my week", "what should I post",
  "content calendar", "I've got nothing to post", or wants a posting schedule
  and an engagement list.
---

# ig-plan

This is mission control. The rest of the pack does the work; this decides what
work gets done. Run it once a week, same day each time.

## Input

If `~/.claude/instagram/voice.md`, `swipe.md` and `log.md` exist, read them. The
swipe file is the user's own proof from `/ig-viral` of which formulas are
working in their niche right now, and it beats anything written in this file.
The log keeps the plan from repeating a theme from the past two weeks.

If those files don't exist, ask four questions and save the answers:

1. What does the user sell, and to who?
2. Which three or four themes do they want to be known for?
3. What actually happened this week? A client call, a number, a mistake,
   something they built, an argument. Posts come from here.
4. Which ten accounts are worth being seen by?

## What to post

Four or five posts a week, at least three of them Reels. Reels are the only
format that dependably reaches people who don't already follow the account.
Carousels go deeper with the people who do. Stories happen daily and get planned
on their own.

Spread the types across the week and never put two of the same back to back:

| type | how often | job |
| --- | --- | --- |
| **Proof** | 1 a week | something real that happened, with a number. Reel. |
| **Teach** | 1 to 2 a week | one thing the viewer can do today. Reel or carousel. |
| **Opinion** | 1 a week | a stance that might cost you followers. Reel. |
| **Story** | 1 every two weeks | a scene where something was lost. Reel. |
| **Offer** | 1 every two weeks | what you sell, said plainly, no apologising. Carousel or stories. |

For every slot give the theme, the exact angle from what happened this week, the
format, and the hook formula number from `ig-reel/hooks.json`. An angle, not a
topic. "AI" isn't a plan. "The proposal we lost because the draft had an em dash
in it" is a Reel.

## When to post

Post when the audience is awake and off work. For most consumer audiences that
means early evening in their time zone; for business audiences, early morning.

But be clear about this: **the time of day matters much less than the first two
seconds.** Instagram will keep pushing a Reel for days if it's doing well, and
bury a perfectly timed one that isn't. If the user is tuning posting times while
their hooks still don't work, they're working on the wrong thing, and you
should tell them.

Use the audience's time zone, not the user's, when they're different.

## The engagement round is not optional

Twenty minutes a day, before posting, not after. Build a list of ten:

- **5 reach** - accounts with the audience the user wants, where a good comment
  gets noticed. Get in early, before there are 200 comments.
- **3 peers** - similar size, same field. These are the ones who return the
  favour.
- **2 buyers** - people who could actually buy. Comment for weeks before any DM,
  and never pitch in the comments.

Pass the list to `/ig-comment`.

## Output

```
WEEK OF SEP 15

MON  engage only  (20 min, list below)
TUE  7:30pm  REEL      PROOF    #5  Time Collapse   - 5hr proposal to 20 min
WED  stories only + engage
THU  7:00pm  CAROUSEL  TEACH    Job B caption       - the 4-slide clause breakdown
FRI  7:30pm  REEL      OPINION  #2  Negative Command - stop doing discovery calls
SAT  -
SUN  6:00pm  REEL      STORY    #21 Mid-Sentence    - the refund email

STORIES  every day, 3 to 5 frames, question box on Thursday.

ENGAGE  (5 reach / 3 peers / 2 buyers)
  ...

Say "write Tuesday" and I'll draft it.
```

Save the plan to `~/.claude/instagram/plan.md` so the other skills can read it.
Nothing gets scheduled or posted. It's a plan, and the user carries it out.
