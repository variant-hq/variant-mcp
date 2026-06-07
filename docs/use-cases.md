# Use Cases

## Create A First Draft

Ask an MCP client to create a deck, generate a set of slides, then open the result in Variant for visual cleanup.

Example prompt:

```txt
Create a six-slide Variant deck for a Q3 launch review. Use concise executive copy, include speaker notes, and preview the title slide when done.
```

## Edit One Slide In Place

Use `slide.get`, `slide.edit`, and `slide.preview` for scoped edits.

Example prompt:

```txt
In my launch deck, change only the headline on slide 4 to "Launch readiness is improving". Do not rewrite the rest of the slide.
```

## Apply Brand Context

Use `brand.context` before creating or restyling slides.

Example prompt:

```txt
Read my Variant brand context, then update the new deck so the typography, colors, and logo treatment match our guidelines.
```

## Export For Handoff

Use `deck.export` when a finished deck needs to move to another format.

Example prompt:

```txt
Export this Variant deck as PPTX for the client handoff and as HTML for internal review.
```

## Review Without Editing

Use a read-only token when an agent should summarize or QA a deck.

Example prompt:

```txt
Review this deck for unclear slide titles, repeated claims, and missing evidence. Do not edit the deck.
```

