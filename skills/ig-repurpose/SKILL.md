---
name: ig-repurpose
description: >-
  Break one long piece - a YouTube video, podcast, livestream, newsletter, blog
  post or client call - into a week of reels and carousels. Use when the user
  says "repurpose this", "turn this into reels", "I've got a video/podcast/
  transcript", "chop this up", or pastes something long and wants it on
  Instagram.
---

# ig-repurpose

A single good long piece usually holds four to six posts. Most people pull one
out and bin the rest.

## Input

A transcript, article, newsletter, script, call summary or livestream. If the
user sends a URL and the session has a transcript tool, use it. Otherwise ask
them to paste the text. Read all of it before you pull anything out.

If it's a video the user owns, ask for the file as well. A Reel cut from their
real footage beats one where they read their own words back to camera.

## Pull things out, don't summarise

Nobody wants a summary of a video as a Reel. Go through the source and lift out
anything that works on its own:

| pull | what counts |
| --- | --- |
| **Claims** | any sentence someone would argue with |
| **Numbers** | any figure, cost, duration or percentage |
| **Stories** | any moment with a person, a setting and a price paid |
| **Mechanisms** | any "here's how this actually works..." |
| **Mistakes** | any admission that something went wrong |
| **Lines** | any sentence that's quotable exactly as said |

List what you found, with a count for each, before you write a word. If the
source gives you fewer than four, it's thin, and four posts stretched out of it
will be thin as well. Tell the user.

## Choose a format for each one

Not everything should be a Reel.

- **Claims, mistakes, stories** become Reels. They need a voice and a face.
- **Mechanisms, numbered lists** become carousels. People need to re-read them.
- **A quotable line** becomes a story frame, not a post.

## Build the week

Every pull turns into one post, and every post works completely on its own. The
viewer hasn't seen the original and won't. Never write "like I said in my last
video". The post is the whole thing.

Give each post a hook formula from `ig-reel/hooks.json`, and mix them up. Five
posts from the same source all using one hook shape reads like a content mill,
because that's what it is.

If the source is the user's own video, **cut the real footage**. The clip where
they actually said it, with their real reaction, beats re-recording every time.
Cut on the end of a sentence, not on a breath.

Order the week so the strongest claim leads, the story lands in the middle, and
the mechanism comes last, when the people who liked the first few are looking
out for it.

## Output

```
SOURCE: "Why we killed discovery calls" (42 min podcast, 8,900 words)

FOUND  5 claims, 9 numbers, 3 stories, 4 mechanisms, 2 mistakes, 7 quotable lines

WEEK
TUE  REEL      #2  Negative Command  Stop running discovery calls
                                     use the 14:20 clip, he laughs at the end
WED  CAROUSEL  Job B caption         The 4-question form that replaced the call
FRI  REEL      #21 Mid-Sentence      "...and he asked for a refund nine days later"
SUN  REEL      #5  Time Collapse     Six hours a week back, one deleted link

Say "write Tuesday" and I'll draft it.
```

Then write them when asked, one at a time, each through `/ig-reel` and
`/ig-human`. Don't hand over four finished scripts at once. They'll all sound
alike and the user won't film any of them.
