---
name: add-lesson-entry
description: "Fetch content from local document or remote webpage and create a properly formatted lesson entry for the Sweden AI Factory Zola site at learn.swedenaifactory.se. Extract metadata, structure content, and include any recordings."
---

# Add Lesson Entry for Sweden AI Factory

Create lesson entries for learn.swedenaifactory.se from existing workshop materials, documentation, or web pages.

## Project-Specific Flow

1. **Fetch**: Read source (local Markdown/HTML file or remote URL)
2. **Extract**: 
   - Title from heading or metadata
   - Description (first paragraph or summary)
   - External URL (canonical location)
   - Skill areas, difficulty, maturity
   - Tags for filtering
   - Video recordings (YouTube IDs)
3. **Reformulate**: Write front matter + Markdown body
4. **Save**: Create file in `content/lessons/<slug>.md`

## Target Format

See [template](./template.md)

## Required Fields

- **title**: Workshop/lesson name
- **description**: One sentence (used in cards)
- **external_url**: Where the actual content lives
- **skill**: 1+ from [ai, agentic, gen_ai, hpc, cloud_computing, programming, julia, data_science, life_science, machine_learning, mlops, pytorch, devops, external] (see zola.toml for up to date list of valid skills)
- **difficulty**: beginner, intermediate, or advanced
- **maturity**: alpha, beta, or stable

## Optional

- **tags**: Additional keywords for search
- **YouTube recordings**: Add embed for each video

## Tips

- Use `{{ <external/> }}` tag to link to external content
- Filename: lowercase, hyphen-separated (e.g., `deep-learning-workshop.md`)
- Keep descriptions under 200 characters
- Include recordings if available
- Reference existing lessons for style
