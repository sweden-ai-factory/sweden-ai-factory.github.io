---
name: add-youtube-recording
description: "Fetch recent video recordings from the Sweden AI Factory YouTube channel and embed them under the current-year section (e.g. ## 2026) of the matching lesson pages in learn.swedenaifactory.se."
---

# Add YouTube Video Recordings to Lesson Pages

Find recent workshop recordings on the Sweden AI Factory YouTube channel and embed them in the relevant lesson files.

## Workflow

1. **Fetch the channel RSS feed** to get video IDs, titles, and publish dates:
   ```bash
   curl -s "https://www.youtube.com/feeds/videos.xml?channel_id=UCo4lx4Wwmdo7qFwwdQJ3Nqw" \
     -H "User-Agent: Mozilla/5.0" | grep -E "<(yt:videoId|title|published)>"
   ```

2. **Filter by date**: Keep only videos published less than 1 month ago. Compute the cutoff from the current date. Determine the current year from the video publish dates or system clock.

3. **Exclude webinars**: Only include hands-on workshops and lesson recordings. Skip pure webinar/talk formats.

4. **Match each video to a lesson page** in `content/lessons/` by topic. Read the lesson files to find the best fit.

5. **Embed** under the year section matching the recording's year (e.g. `## 2026` for videos published in 2026) of each matching lesson file:
   ```markdown
   {{ <youtube id="VIDEO_ID"/> }}
   ```
   If the lesson has no section for that year yet, append `## <YEAR>` at the end of the file.

## Reference

- YouTube component: `templates/components/youtube.html`
- Channel ID: `UCo4lx4Wwmdo7qFwwdQJ3Nqw` (handle: `@sweden-ai-factory`)
- Lesson files: `content/lessons/*.md`
- Existing embeds use `{{ <youtube id="..." playlist="..."/> }}` — omit `playlist` when unknown
