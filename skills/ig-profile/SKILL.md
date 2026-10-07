---
name: ig-profile
description: >-
  Grade an Instagram profile out of 100 on a 12-item rubric, then rewrite the
  pieces that cost the most points - name field, bio, link, highlights, the
  three pinned posts, the grid. Use when the user says "optimize my profile",
  "fix my bio", "score my Instagram", "why aren't people following me", or
  pastes their profile and asks how it comes across.
---

# ig-profile

Most people polish the wrong part of their profile. Nobody browses it like a
shop window. They land on it from a single reel, and it has roughly three
seconds to answer one thing: is there more of what I just watched, and is it
meant for me.

## What to ask for

Get the user to paste or screenshot: the name field, the handle, the bio, where
the link goes, the highlight titles, the pinned posts, and the first nine grid
covers. One screenshot of the top of the profile and the first two rows of the
grid is plenty to start.

Never log into Instagram for them.

## Grade it

Open `rubric.json` in this folder. It has twelve items worth 100 points total,
and each one describes what a perfect score looks like and the usual way it
goes wrong. Grade every item, print the table, give the total. Don't be kind.
Most profiles score in the 30s or 40s the first time, and an inflated score
helps nobody.

```
PROFILE SCORE  38/100

  name field       2/12   just a name, nothing anyone would search for
  bio first line   3/12   three nouns and a coffee emoji
  pinned three     0/10   nothing pinned
  highlights       2/8    "Random", "Life", "2023"
  grid legibility  4/8    six of nine covers are a face mid-word
  ...
```

## Rewrite in this order

Start with whatever lost the most points. Don't rewrite the whole thing in one
go, because the user has to go into the app and change every field by hand.

**1. Name field (30 characters).** This is the bold line under the profile
photo, not the handle. Instagram search matches against it, and most accounts
waste it on a name alone. A format that works:
`{Name} | {what you do, in words people search}`. Offer three versions.

**2. First line of the bio.** Who it's for and what changes for them. Not a job
title, not a stack of adjectives, not a list of identities split by pipes. Use
the rest of the 150 characters for one piece of proof or one plain offer.

**3. The three pinned posts.** Three slots with three separate jobs: your
strongest proof, the clearest explanation of what you offer, and the best
introduction to you as a person. It's the biggest win on the whole profile and
it takes four taps. If nothing is pinned, visitors see whatever went up last,
and that's luck.

**4. Highlights.** Four to six, titled after the questions a buyer would ask:
Pricing, Results, How it works, About. Drop "Random" and everything like it.

**5. The link.** One destination that delivers what the bio just promised. You
can add five, but two is already a menu, and a menu converts worse than a single
door.

**6. Grid covers.** Look at the first nine at thumbnail size. Pick reel covers
on purpose instead of accepting a random frame. Four words of text per cover
makes the whole grid readable at a glance.

## Output

The score table first, then each rewrite as a copy-ready block in fix-first
order, all of them passed through `/ig-human`. Re-grade at the end and report
the change honestly. If the new version reaches 84 and not 98, say 84, and
explain what's left. Usually that's a grid, a regular stories habit and a pinned
post that hasn't been made yet, and none of those are a rewrite.

This skill never saves anything to Instagram. The user changes each field.
