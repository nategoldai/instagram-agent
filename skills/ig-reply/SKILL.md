---
name: ig-reply
description: >-
  Deal with the comments on the user's own reels and posts - sort them by which
  are worth answering, then draft the replies. Use when the user pastes their
  comments, says "reply to these", "handle my comments", "someone said X on my
  reel", or is dealing with a critic, a troll or a lead in the comments.
---

# ig-reply

The comments under your own post are where its reach gets decided. Each reply
adds another interaction, replies in the first hour do most of the lifting, and
on Instagram you can reply with a whole Reel, which is the most underused move
on the app.

Comments aren't all worth the same, though, so this skill sorts them before it
writes anything.

## Input

The user pastes the comments, with handles if possible. Screenshots work too.
Don't scrape the thread with a browser tool.

## Sort first

Put every comment in one of six buckets and say how many landed in each:

| bucket | what it is | what it gets |
| --- | --- | --- |
| **KEYWORD** | the word you asked people to comment | the promised thing, sent by hand or by your approved tool |
| **LEAD** | someone describing the problem you solve | a real answer in public, then an open door |
| **SUBSTANCE** | adds data, pushes back, builds on it | the longest reply in the thread |
| **QUESTION** | a question lots of people have | becomes a Reel, not just a reply |
| **SUPPORT** | "🔥", "great post", a tag | a like and 3 to 8 words, max |
| **NOISE** | pitches, spam, bad faith, bait | nothing, or one line and done |

Write replies in that order and stop once they stop being worth it.

## The move most people skip

If a comment asks something thirty other people are also wondering, **answer it
with a Reel**. Instagram pins the comment to the new video as a sticker, the
person who asked gets a notification, and a question people clearly want
answered becomes a post with its hook already written. Flag every QUESTION that
fits and pass it to `/ig-reel` as formula #16.

## How to reply

- **Answer what they asked.** If someone asks how, tell them how, right there.
  Don't send them to DMs for an answer they could have had in the thread.
- **Use their name once**, at the start, no exclamation mark.
- **Match their length.** A four-word comment doesn't get a four-line reply.
- **To a critic:** agree with the part that's true first, in their words, then
  hold your position. Never delete, never get defensive, never reply twice in
  the same thread.
- **To a troll:** nothing. Replying gives them reach, which is what they came
  for. Hide it if it's abusive. Instagram's comment controls are there to be
  used and using them isn't losing.
- **To a lead:** answer completely, in public. The door is one sentence at the
  end, offered as help, not a pitch. The public answer is what gets the next
  person to DM you.

## Keyword comments

If the post asked for a keyword, those comments are the reason the post exists.
Each one is someone raising their hand. Reply to every one, then send what you
promised. If the user has automation running through Instagram's own tools or an
approved partner, say so and let it do the work. If not, replying by hand is
fine at this volume. Never mass-DM anyone who didn't comment.

## Output

One block, grouped by bucket, every reply ready to paste and already humanized:

```
REPLIES  ·  84 comments  ·  41 KEYWORD, 2 LEAD, 3 SUBSTANCE, 2 QUESTION, 34 SUPPORT, 2 NOISE

KEYWORD  (41)  send the clause. One line each, same warmth, not copy-paste.

LEAD
@handle - "we had this exact thing happen in June"
> What fixed it for us was taking the payment trigger off approval
> completely. Happy to send the wording if that helps.

QUESTION -> REEL
@handle - "what do you do if they refuse to sign it?"
  34 likes on this comment. That's a Reel, not a reply. Formula #16.

NOISE  (2)  skipped. Replying gives them reach.
```

Then the gate: nothing goes live until the user says yes. They paste the
replies themselves.
