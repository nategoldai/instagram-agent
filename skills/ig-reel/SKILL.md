---
name: ig-reel
description: >-
  Write an Instagram Reel from a rough idea - hook options from 26 formulas,
  the spoken script, the on-screen text, and a timed beat sheet - in the user's
  own voice, scored before they film. Use whenever the user wants a Reel, a
  short-form video script, a hook, a voiceover, "make a reel about X", "what
  should I say in this video", or is about to record without a first line.
---

# ig-reel

Turns one rough idea into a Reel people actually watch to the end.

There are two tools in this folder and both really run. Use them. Don't guess
whether the hook is good, and don't guess the length.

```bash
python3 hookscore.py hooks.txt              # rank your hook options
python3 hookscore.py --hook "one line"      # score just one
python3 beats.py script.txt --target 30     # timed beat sheet before filming
```

## Before writing

1. Read `~/.claude/instagram/voice.md` if it exists. It's the user's voice
   profile: how they talk on camera, what they'd never say, who they're talking
   to. If it's missing, ask for **three of their own reels**, transcribe or read
   them, work out the voice, and write the file. A script in the wrong voice is
   useless, because they have to say it out loud.
2. Read `hooks.json` in this folder. 26 formulas, each with a template, a filled
   example, the on-screen version, what it's for, and how it goes wrong. Four of
   them are in there because they kept showing up in real hooks, not to round
   out a pattern.
3. If the idea is thin, don't pad it out. Ask one combined question: what
   happened, to who, and what did it cost or earn. A Reel needs one specific
   true thing. Get it before you write.
4. If `~/.claude/instagram/swipe.md` exists, read it. `/ig-viral` writes it, and
   it's the user's own proof of which formulas are working in their niche right
   now. It outranks the defaults in this file.

## The shape

A Reel is won in the first two seconds and held by the next five.

```
0:00 - 0:02   HOOK        the claim. Spoken line and on-screen line, written
                          separately. Movement in frame one, not a still face.
0:02 - 0:07   THE STAKE   why the viewer should care. One line.
0:07 - ...    THE BODY    one idea per beat, and the shot changes every beat.
LAST 3s       THE PAYOFF  deliver what the hook promised, then the one ask.
LAST LINE     THE LOOP    repeat a word from the hook so the replay flows.
```

Length: 15 to 45 seconds is the sweet spot. Reels can run 3 minutes and almost
nobody should. Under 7 seconds, replays inflate and nothing else does.

## The loop

**1. Write three hooks, not one.** Run the idea through `hooks.json`, pick three
formulas that truly fit, and write the spoken line and on-screen line for each.
Three different formulas, not one rewritten three times.

**2. Score them.** Put the three spoken lines in a file, one per line, and run
`hookscore.py`. Show the user the ranking. If the best one is under 50, you
don't have the hook yet and editing won't fix it.

**3. Write the script** on the winning hook. Plain spoken language, the way the
user really talks. Contractions. Short lines. Nothing they'd need to rehearse.

**4. Time it.** Run `beats.py script.txt --target {length}`. Fix every flag: a
hook longer than 3 seconds, any beat over 4 seconds, a stretch of beats with
nothing concrete, no loop. Run it again until it's clean.

**5. Humanize it.** Pass the script through `/ig-human` before showing it. A
line that sounds written is obvious the second someone says it out loud.

**6. Print the block.** The script in a fenced block, the on-screen text as its
own timed list, and then:

```
REEL READY
hook:       #3 Nobody Tells You, scored 86 STRONG
length:     28.4s across 9 beats at 165 wpm
on-screen:  6 cards
humanizer:  4 artefacts stripped, human score 81 PASS
caption:    run /ig-caption next

Reply "yes" to log it, or tell me what to change.
```

**7. Never publish.** This skill makes a script. The user films it and posts
it. On "yes", add a line to `~/.claude/instagram/log.md` with the date, the hook
formula and the first line, so `/ig-audit` has a history to work from later.

## On-screen text is its own script

Write it separately every time. People read it before they hear anything.

- **Six words max per card.** It's read at arm's length by someone who isn't
  listening yet.
- **The hook card is up at frame 1**, not after a pause.
- **Stay inside the safe zone.** On a 1080x1920 frame, nothing above y=230 or
  below y=1440, and keep the right 230 pixels empty. Instagram's interface
  covers everything outside that box: caption, action buttons, audio bar.
- **Never put the hook where the caption sits.** That's the bottom of the frame
  and it's covered.
- **Burn in captions for the body.** Most people watch on mute first.

## Rules that make the difference

- **One idea per Reel.** If the script has two, that's two Reels. Say so.
- **Numbers beat adjectives.** "$4,200" beats "a lot". If the user hasn't given
  a number, ask for one instead of writing around the gap.
- **Skip the intro.** No hello, no "in this video", no name, no logo sting. Start
  at the sentence you'd normally reach around second six.
- **Change the shot every beat.** Eight seconds of the same shot is where people
  leave, and `beats.py` flags it.
- **One ask at the end.** Comment a keyword, save it, or follow. Just one.
- **Never make things up.** No invented stats, clients, revenue or results under
  the user's name, not even as placeholders. If a number is needed and unknown,
  put `{{your number}}` in the script and flag it.
- **Don't build a script around trending audio the user can't use.** If the idea
  needs the user's own voice, say so.

## Example

```
/ig-reel we cut proposal time from 5 hours to 20 minutes with one template
```

```
HOOKS  (scored)
  86  STRONG  #5  Time Collapse   "Proposals used to take me five hours. Now it's twenty minutes."
                                  on screen: 5 HOURS -> 20 MIN
  71  STRONG  #1  Cost Confession "For two years I billed four hours a week for formatting."
                                  on screen: 2 YEARS WASTED
  54  OK      #9  The Steal       "Steal the proposal template that did it."
                                  on screen: STEAL THIS

Filming #5: the ratio is believable, it reads in one glance on screen,
and the number is really yours.
```
