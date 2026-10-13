# Instructions for Claude: Flowers for Joy website

You maintain a one-page static website for Flowers for Joy, a nonprofit initiative that
delivers donated flowers to cancer patients. Requests come from volunteers, usually as a
GitHub issue or comment. Work carefully: the site is public and represents real people.

## How the site is built
- Everything is in `index.html`: one `<style>` block at the top, the page, one `<script>` at the bottom.
- Sections are marked `<!-- ==== EDIT n · NAME ==== -->`. README.md has the section map and a
  copy-paste recipe for every common change. **Follow those recipes and match the existing markup.**
- Images live in `images/`, partner logos in `images/logos/`, the video in `video/`.
- No build step, no frameworks, no external libraries. Don't add any.

## Rules
1. **Only use content the requester gives you.** Never invent names, bios, quotes, numbers,
   dates, links or claims. If something needed is missing, ask in a comment instead of guessing.
2. **Change only what was asked.** Don't restyle, reorganize or "improve" other parts.
3. **Leave the `<script>` and `<style>` blocks alone**, except the settings in EDIT 14
   (contact email, first-delivery date) and the colors in EDIT 15, and only when asked.
4. **Keep class names and structure** so the existing styles and scripts keep working.
5. **Don't change the donation QR (`images/donate-qr.png`), the Zelle recipient text, or the
   contact email** unless the request explicitly asks for it, and say so clearly in the PR.
6. **Patient privacy.** Photos should show volunteers, nurses or florists. If a photo appears to
   show a patient in a medical setting and the request doesn't confirm written consent for
   website use, don't publish it. Ask in a comment first.
7. **Write `&` as `&amp;`** inside HTML text and attributes.
8. **Always work through a pull request** with a short plain-English summary of what changed
   and which EDIT section(s) you touched. Never push straight to the main branch.
9. If you add a new section, file name pattern or setting, **update README.md** to match.

## Handling files people upload
New files usually arrive in `uploads/`. Process each one, move it to its final place, and
delete the original from `uploads/`. Install tools if missing:
`pip install pillow` (images), `sudo apt-get install -y ffmpeg` (video).

- **Always apply the photo's rotation tag first** (`PIL.ImageOps.exif_transpose`). Phone photos
  otherwise appear sideways.
- **Team photo:** square crop centered on the face, 300×300 px, JPEG quality ~85, saved as
  `images/team-<firstname>.jpg` (lowercase), matching the `data-img` in that person's card.
- **Gallery photo:** longest side 1600 px, JPEG quality ~82, under 500 KB, saved as
  `images/gallery-<n>.jpg` using the next free number. Add its line in EDIT 7.
- **Partner logo:** PNG, transparent background if available, height about 200 px, saved as
  `images/logos/<partner-slug>.png` matching the box's `data-logo`. Add `data-logo` if missing.
- **Video:** convert to 720p H.264 with fast start, then grab a poster frame:
  ```
  ffmpeg -i in.mp4 -vf "scale=1280:-2" -c:v libx264 -preset slow -crf 26 -pix_fmt yuv420p -c:a aac -b:a 96k -movflags +faststart video/story.mp4
  ffmpeg -ss 3 -i video/story.mp4 -frames:v 1 -q:v 4 video/poster.jpg
  ```
  Keep it under about 20 MB.

## Before opening the PR
- Check that every tag you added is closed and every new image path points to a real file.
- List any request you couldn't complete, and why.
