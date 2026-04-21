# Content Sharpening Agent — Run Instructions

## What this agent does

On each scheduled run, this agent reviews unsharpened marketing content from the VRM Sales Library, applies the voice and style rules in `voice_guide.md`, and overwrites the original file with the sharpened version. It then updates `processing_log.json` and commits all changes back to this repo.

---

## Step-by-step run process

### 1. Read reference files first
Before touching any content, read these two files in full:
- `voice_guide.md` — Chad's voice rules, formatting rules, and what to sharpen vs. leave alone
- `style_samples.md` — before/after calibration samples; use these to set your sharpening standard

Do not skip this step. These files are your operating instructions.

### 2. Check the processing log
Read `processing_log.json`. Find all files with `"status": "pending"`.

Process a maximum of **5 files per run** to keep each commit focused and reviewable. Pick the first 5 pending files in the order they appear in the log.

If there are no pending files, commit nothing and stop. The run is complete.

### 3. For each file, identify the content type
- `linkedin/post_*.txt` → LinkedIn post
- `newsletter/newsletter.txt` → LinkedIn newsletter
- `twitter/posts.json` → X (Twitter) posts

Apply the rules from `voice_guide.md` specific to that content type.

### 4. Sharpen the content

**For `.txt` files (LinkedIn posts and newsletters):**
- Read the file
- Apply all relevant voice, tone, and formatting rules
- Overwrite the file with the sharpened version in place
- Do not rename the file or change the folder structure

**For `posts.json` files (Twitter):**
- Read the file
- Sharpen the `text` field of each post and each tweet in threads
- Apply X-specific rules: no em dashes, no hedging, no weak openers, under 280 characters per standalone post
- Overwrite the file with sharpened content in place
- Do not alter any structural keys (`id`, `type`, `post_role`, `best_timing`, `source_trace`, etc.)

### 5. Update the processing log
After sharpening each file, update its entry in `processing_log.json`:
- Set `"status"` to `"sharpened"`
- Set `"sharpened_date"` to today's date in `YYYY-MM-DD` format

### 6. Handle new files
If you find a file in the `output/` folder that matches the target patterns below but is **not listed** in `processing_log.json`, add it to the log with `"status": "pending"` before this run's processing begins. It will be picked up on a future run.

Target file patterns:
- `output/{book}/linkedin/post_*.txt`
- `output/{book}/newsletter/newsletter.txt`
- `output/{book}/twitter/posts.json`

Ignore all other files (`review_*.json`, `gold_set_v1.json`, `tweets.json`, `threads.json`, `posting_log.json`, etc.).

### 7. Commit and push
After processing the batch of files, make a single commit with all changes including the updated `processing_log.json`.

Commit message format:
```
Sharpen [N] files: [book_slug/file, book_slug/file, ...]
```

Example:
```
Sharpen 5 files: gap_selling/linkedin/post_1, gap_selling/linkedin/post_2, gap_selling/newsletter, the_jolt_effect/linkedin/post_1, the_jolt_effect/twitter/posts
```

Push to `origin master`.

---

## What not to do

- Do not modify `voice_guide.md`, `style_samples.md`, or `AGENT_INSTRUCTIONS.md`
- Do not modify `output/OUTPUT_CONVENTIONS.md` or `output/TWITTER_OUTPUT_CONVENTIONS.md`
- Do not modify `output/migration_map.json`
- Do not rename files or restructure folders
- Do not alter structural keys in JSON files
- Do not process more than 5 files per run
- Do not re-process files already marked `"sharpened"` unless the file has been reset to `"pending"` manually

---

## If something is unclear

If a file has a structural problem that sharpening cannot fix (circular argument, script contradicts the framework, field note restates the paragraph above it), sharpen what you can and add a comment at the top of the file in this format:

```
[AGENT FLAG - YYYY-MM-DD]: Brief description of the structural issue that needs human review.
```

Then mark the file as `"sharpened"` in the log and continue. Do not leave a file unprocessed because of a structural issue.
