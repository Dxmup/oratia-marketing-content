# Cover Image Conventions
# VRM Sales Library — Newsletter Cover Images

## Purpose
Each newsletter edition gets one cover image. It serves as the visual header for the LinkedIn newsletter and can double as a social share card on X/Twitter.

## Recommended Tool
**Ideogram** (ideogram.ai) — handles embedded text better than most generators. DALL-E 3 via ChatGPT is the fallback.

## Dimensions
- **Primary format:** 1200 x 644 px (LinkedIn newsletter cover, ~1.9:1 ratio)
- **Secondary format:** 1200 x 628 px (Open Graph / social share card)
- Ideogram: use "Landscape" with the 16:9 or custom ratio

## Brand Style — Consistent Across All Books
These elements should appear in every cover image to make the series feel cohesive:

### Visual Language
- Editorial, not corporate
- Warm and grounded, not cold and tech-heavy
- Hospitality-adjacent imagery: interiors, natural light, property settings, human interaction
- No clipart, stock-photo cheese, or generic "business handshake" imagery
- Avoid showing actual book covers (copyright)

### Color Palette (Consistent Across Series)
- Background: deep navy (#1A2B45) or warm cream (#F5F0E8)
- Text: white on dark, or near-black on cream
- Accent: warm amber (#C8843A) as the highlight color
- Book-specific tints are allowed as a secondary tone but should not override the base palette

### The VRM Sales Library Textmark
The series does not have a logo file. The textmark is a typographic treatment applied consistently across all covers.

**Typographic spec:**
- Text: `VRM SALES LIBRARY`
- Weight: Bold or ExtraBold
- Case: ALL CAPS
- Font: Montserrat (preferred) or Inter as fallback — geometric sans-serif only
- Color: Amber (#C8843A) on dark backgrounds, deep navy (#1A2B45) on light backgrounds
- Letter-spacing: slightly expanded (tracking: +100 to +150 in Canva terms)
- Optional: a 1–2px rule beneath the textmark in the same amber color to separate it from the visual

**Placement:** Upper left corner or upper center of the image, small relative to the book title.

### Full Text Hierarchy on Cover
- Line 1 (small, uppercase, amber, tracked): `VRM SALES LIBRARY` — the textmark
- Line 2 (large, bold, white or cream): `[Book Title]`
- Line 3 (medium, regular weight, white or warm cream): `[Author Name]`

**Production recommendation:** AI image generators cannot reliably reproduce exact typographic treatments. Generate the background scene without text, then composite all three text elements as layers in Canva using the spec above. This guarantees consistency across the full series. Use Canva's "Text" tool with Montserrat Bold for the textmark and title, Montserrat Regular for the author line.

### Visual Concept Per Book
Each book gets a concept image that reflects its core theme — not a literal illustration of the title, but an evocative scene or abstract composition. See book-specific prompt files for the concept.

## File Naming
Store in the book's newsletter folder:
- `output/{book_slug}/newsletter/cover_image_prompt.txt` — the generation prompt
- `output/{book_slug}/newsletter/cover_image.png` — the generated image (once produced)

## Prompt Structure Template

Use this structure for every book-specific prompt:

```
Editorial newsletter cover image for a professional sales and hospitality publication called "VRM Sales Library."

VISUAL CONCEPT:
[2-3 sentences describing the scene or abstract composition specific to this book's theme]

STYLE:
Warm, editorial photography style. Natural light. Hospitality-adjacent setting (vacation rental interior, lobby, property exterior at golden hour, or similar). Cinematic but understated. Not corporate. Not stock-photo.

COLOR:
Deep navy and warm cream base. Amber accent tones. [Any book-specific secondary tone.]

TEXT OVERLAY (embed in image):
- Top: "VRM SALES LIBRARY" in small uppercase amber sans-serif
- Center-large: "[Book Title]" in bold white serif or sans-serif
- Below title: "[Author Name]" in smaller white or cream weight

FORMAT: Landscape, 1200x644px
STYLE REFERENCE: Editorial magazine header, think Bloomberg Businessweek or Fast Company feature spread — professional but warm
```

## Processing Log Note
Cover image prompts are not tracked in `processing_log.json` (that file tracks text content for the sharpening agent). Track cover image production manually or with a separate image log if needed.
