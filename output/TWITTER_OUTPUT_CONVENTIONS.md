# Twitter Output Conventions

## Purpose
This file defines the output structure for Twitter/X content generated from the Book-to-LinkedIn Content Factory.

## Folder Structure
Store Twitter outputs inside each per-book folder under `output/{slug}/twitter/`.

Example:
- `output/the_jolt_effect/twitter/`
- `output/gap_selling/twitter/`

## Core Files
Inside each Twitter folder, use:
- `tweets.json` — standalone tweets and engagement tweets
- `threads.json` — short educational or diagnostic threads
- `review.json` — editorial review/status for Twitter outputs
- `schedule.json` — optional scheduling metadata
- `posting_log.json` — optional posted-state tracking

## Review State Suggestions
Use these values when tracking state:
- `draft`
- `approved`
- `scheduled`
- `posted`
- `archived`

## Tweet Record Shape
```json
{
  "id": "tweet_1",
  "type": "standalone_insight",
  "source_theme": "no decision vs competitor",
  "text": "Most stalled owner deals aren't lost to another manager. They're lost to no decision.",
  "engagement_prompt": false,
  "status": "draft",
  "source_trace": {
    "book_slug": "the_jolt_effect",
    "source_file": "newsletter.txt",
    "theme": "fear_of_messing_up",
    "related_linkedin_post": "post_1.txt"
  }
}
```

## Thread Record Shape
```json
{
  "id": "thread_1",
  "type": "short_thread",
  "source_theme": "JOLT framework",
  "tweets": [
    "If an owner says they need more time, your problem may not be persuasion.",
    "It may be transition friction."
  ],
  "status": "draft",
  "source_trace": {
    "book_slug": "the_jolt_effect",
    "source_file": "newsletter.txt",
    "theme": "jolt_framework",
    "related_linkedin_post": "post_1.txt"
  }
}
```

## Scheduling Guidance
Keep schedule data separate from content.
Use `schedule.json` only for scheduling metadata, not for editorial notes.

## Posting Log Guidance
Use `posting_log.json` to track:
- platform/account
- posted date/time
- URL if available
- notes on performance or manual edits

## Legacy Compatibility
Legacy flat files in `output/` may remain for reference.
All new Twitter content should use the per-book folder format.
