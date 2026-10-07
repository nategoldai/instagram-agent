---
name: ig-carousel
description: >-
  Make an Instagram carousel - a cover that earns the swipe, copy for each
  slide, and the 1080x1350 files to upload. Use when the user says "carousel",
  "slides", "swipe post", "turn this into a carousel", or has an idea shaped like
  a list or a set of steps that would fall flat as one image.
---

# ig-carousel

Carousels hold attention longer than anything else on the grid, because a swipe
counts as an interaction and a scroll doesn't. They also get a second shot:
Instagram can re-show a carousel from a later slide to someone who skipped it
the first time, so slide two has to work by itself too.

The format rewards one idea split into steps. It punishes a caption chopped
into pieces.

## Carousel or Reel?

Go with a carousel when the idea **has an order and needs re-reading**: steps, a
framework with parts, a before and after, a list worth screenshotting. Go with a
Reel when the idea has movement, a face, or a payoff people need to see happen.

If the idea is a single claim, it's neither. Pass it to `/ig-reel` and say why.

## Structure

6 to 10 slides. The maximum is 20, and 20 is nearly always a book nobody gets
through. Under 5 and nobody starts swiping.

```
1         COVER     the hook. 6 words max, big enough to read in the grid at
                    thumbnail size. One line of promise underneath.
2         THE STAKE why it matters, in one sentence. This slide doubles as a
                    second cover, so it can't be setup.
3 to N    ONE IDEA PER SLIDE. A 3 to 7 word headline, 25 words max under it.
                    If a slide needs a paragraph, it's two slides.
N+1       RECAP     everything as a list. The screenshot slide.
LAST      CTA       one action. Save, comment a keyword, or follow. Just one.
```

## Rules for the slide copy

- **The cover does 80% of the work.** Six words, big. Nothing later in the deck
  rescues a cover nobody swipes.
- **Design for the grid crop.** The profile grid crops posts to a tall portrait
  shape, and the exact ratio has changed more than once. Build at 1080x1350 and
  keep the cover text well into the middle, at least 120 pixels in from every
  edge, and the crop stops being a problem.
- **Number the slides** (3/8). People finish more often when they can see the
  end coming.
- **No paragraphs on slides.** If it won't fit in 25 words, split it.
- **The recap is what gets screenshotted and sent.** Sends are the strongest
  signal you can get. Make it readable on its own with no context.
- **Your handle on every slide**, small, in a bottom corner. Screenshots travel
  without you attached.
- **Alt text on the cover at the very least.** Screen readers and Instagram both
  read it.

## Making the files

Instagram wants 1080x1350 (4:5), JPEG or PNG, up to 20 items. Build it as HTML
and export each slide:

```bash
# one <section> per slide, 1080x1350, page-break-after: always
# then Chrome headless --print-to-pdf, or whatever HTML-to-image tool you use
```

Set `width:1080px; height:1350px` in the HTML, use one accent colour, and keep
text at 32px or bigger, because it'll be read on a phone at about a third of its
real size. If the project has a brand skill or design system, use it instead of
inventing a palette.

## Output

First the copy, slide by slide, as a numbered list the user can scan in ten
seconds and edit before anything gets rendered. Then the **caption**, which for
a carousel is Job B in `/ig-caption`: the caption has real work to do here,
because the cover already spent its six words.

Put both through `/ig-human`. Only build the files once the user signs off on the
copy.

```
CAROUSEL  ·  8 slides

1  COVER   THE $18,000 CLAUSE
           One line I now put in every contract.
2  STAKE   I approved the work. Nine days later they wanted their money back.
3          WHAT IT SAYS
           Payment on delivery, not on approval.
...
7  RECAP   All four lines, in order.
8  CTA     Comment CONTRACT and I'll send you the full clause.

Caption: Job B, hook in line 1, one ask, 3 tags.
```

Nothing gets uploaded. The user posts it.
