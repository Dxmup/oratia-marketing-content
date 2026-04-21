# Content Factory Migration Plan

## Goal
Move the Content Factory to a uniform per-book folder structure while adding Twitter as a first-class content medium.

## Recommendation
Use one canonical folder per book under `output/{book_slug}/`.
This should become the single source of truth for all future work.

Recommended structure:
- `output/{book_slug}/linkedin/post_1.txt`
- `output/{book_slug}/linkedin/post_2.txt`
- `output/{book_slug}/linkedin/post_3.txt`
- `output/{book_slug}/newsletter/newsletter.txt`
- `output/{book_slug}/twitter/tweets.json`
- `output/{book_slug}/twitter/threads.json`
- `output/{book_slug}/twitter/review.json`
- `output/{book_slug}/twitter/schedule.json` (optional)
- `output/{book_slug}/twitter/posting_log.json` (optional)
- `output/{book_slug}/nuggets.json`
- `output/{book_slug}/strategy.json`
- `output/{book_slug}/editor_review.json`
- `output/{book_slug}/draft_queue.json` (optional)
- `output/{book_slug}/schedule.json` (optional)

## Why this system
- Keeps all assets for a book in one place
- Makes orchestration simpler and more uniform
- Reduces ambiguity when adding new channels later
- Supports source tracing and future automation
- Makes migration finite and easy to audit

## Migration Rule
Do not keep two competing canonical systems.
Flat files can remain temporarily during migration, but once a book is migrated, the folder version should be treated as canonical.

## Migration Approach
For existing books:
1. Create `output/{book_slug}/`
2. Move legacy `post_*.txt` files into `linkedin/`
3. Move legacy `newsletter_*.txt` file into `newsletter/newsletter.txt`
4. Leave missing internal handoff files absent rather than inventing them
5. Add Twitter files only when generated
6. Update `PROCESSED_BOOKS.md` notes if needed

## Stability Principle
The workflow should be stable and uniform going forward:
- same per-book layout
- same stage outputs
- same traceability rules
- same approval flow across mediums

## Short Answer
If you want stable and uniform, migrate all 58 legacy files into the new per-book folder structure once, then make that the only format going forward.
