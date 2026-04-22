# Output Conventions

## Folder Structure
Use one folder per book/run under `output/`.

Example:
- `output/the_jolt_effect/`
- `output/gap_selling/`

## Internal Handoff Files
Inside each book folder, use structured files for machine handoff between agents:
- `nuggets.json` — Analyst output
- `strategy.json` — Strategist output
- `editor_review.json` — Editor output
- `draft_queue.json` — approved posts queued for drafting
- `schedule.json` — optional scheduling metadata

## Final Human-Use Files
Inside each book folder, organize final content by medium:
- `linkedin/post_1.txt`
- `linkedin/post_2.txt`
- `linkedin/post_3.txt`
- `newsletter/newsletter.txt`
- `newsletter/cover_image_prompt.txt` — AI image generation prompt for the newsletter header
- `newsletter/cover_image.png` — generated image (added after production)
- `twitter/tweets.json`
- `twitter/threads.json`

If a run produces only one post or a different number of posts, use the same numbering pattern consistently.

## Legacy Compatibility
Older flat files in `output/` can remain for reference, but all new runs should use the per-book folder format.

## Naming Pattern
Use lowercase snake case for the folder name based on source title, for example:
- `sell_without_selling_out/`
- `the_jolt_effect/`
- `way_of_the_wolf/`

## Draft Queue Shape
```json
[
  {
    "post_id": "post_1",
    "source_file": "post_1.txt",
    "final_text": "plain text post content",
    "media": [],
    "notes": "optional"
  }
]
```

## Optional Schedule Shape
```json
{
  "post_1": { "date": "2026-04-21", "time": "10:00", "timezone": "America/New_York" },
  "post_2": { "date": "2026-04-23", "time": "10:00", "timezone": "America/New_York" },
  "post_3": { "date": "2026-04-24", "time": "10:00", "timezone": "America/New_York" }
}
```
