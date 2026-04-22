# Book-to-LinkedIn Content Factory

This folder contains the working system for turning source books and related material into LinkedIn posts, newsletter drafts, and X/Twitter amplification content in Chad's VRM operator voice.

## Front Door
In a new chat, the intended command is plain English:
- `Run the Content Factory for [book title]`
- `Run the Content Factory for the next unprocessed book`
- `Audit the Content Factory`
- `Prepare approved posts for drafting`

The orchestrator prompt is the entry point:
- `prompts/0_the_orchestrator.md`

## Cover Images
Each newsletter gets one AI-generated cover image. Prompts are stored per-book in `output/{slug}/newsletter/cover_image_prompt.txt`. Standards and tool recommendations are in `COVER_IMAGE_CONVENTIONS.md`. Recommended tool: Ideogram (ideogram.ai).

## Required Files
- `prompts/0_the_orchestrator.md` — front-door orchestration rules
- `prompts/1_the_analyst.md`
- `prompts/2_the_strategist.md`
- `prompts/3_the_writer.md`
- `prompts/4_the_drafter.md`
- `prompts/5_the_editor.md`
- `prompts/6_the_twitter_writer.md`
- `main_config.yaml` — stage definitions and outputs
- `output/OUTPUT_CONVENTIONS.md` — output structure rules
- `output/TWITTER_OUTPUT_CONVENTIONS.md` — Twitter output structure rules
- `BOOK_HITLIST.md` — canonical queue for what to process next
- `PROCESSED_BOOKS.md` — books already completed and verified

## Workflow
1. Audit what is actually on disk.
2. Confirm whether the requested book is already processed.
3. If no specific book is named, use `BOOK_HITLIST.md` to select the next highest-priority unprocessed title.
4. Locate source material.
5. Run Analyst → Strategist → Writer → Twitter Writer → Editor.
6. For X, optimize for amplification: the sharpest observation, strongest reaction-worthy line, useful story detail, natural operator engagement, and occasional natural Oratia context.
7. Treat X as an amplifier and conversation surface for the VRM Sales Library, not a miniature LinkedIn channel.
8. Only prepare drafting assets after editorial approval.
9. Only run the Drafter when explicitly requested.
10. Keep X/Twitter outputs in the per-book folder under `twitter/`.

## Output Standard
All new runs should use one canonical folder per book in `output/`.
Example:
- `output/gap_selling/`
  - `nuggets.json`
  - `strategy.json`
  - `editor_review.json`
  - `draft_queue.json`
  - optional `schedule.json`
  - `linkedin/`
    - `post_1.txt`
    - `post_2.txt`
    - `post_3.txt`
  - `newsletter/`
    - `newsletter.txt`
  - `twitter/`
    - `tweets.json`
    - `threads.json`
    - optional `review.json`
    - optional `schedule.json`
    - optional `posting_log.json`

Legacy flat files may remain temporarily during migration, but the per-book folder is the canonical system and all new work should target it directly.

## Trust Rule
Do not trust prior chat claims about files unless the files actually exist on disk.
The workspace is the source of truth.
