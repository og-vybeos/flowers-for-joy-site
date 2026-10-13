# Flowers for Joy website: editing guide

This guide is for anyone with basic HTML experience who needs to update the site:
adding a donor, a press article, a team member, a photo, or changing some text.
Most changes take a few minutes and only touch one file, `index.html`.

---

## 1. What's in this folder

```
index.html     The whole website: all text, sections, links and styles
images/        All photos, the logo, and the donation QR code
images/logos/  Partner and donor logos (optional; see "Add a partner logo")
video/         The story video (story.mp4) and its preview image (poster.jpg)
uploads/       Drop folder for the AI assistant (see section 8)
README.md      This guide
CLAUDE.md      Instructions the AI assistant follows (see section 8)
.github/       The AI assistant's setup file (inactive until switched on)
```

There is no database, no login and no build step. The site is plain files, so it runs on
any web host (Vercel, Netlify, Cloudflare Pages, GitHub Pages, or a regular host such as
GoDaddy or Bluehost).

---

## 2. How to make a change

1. **Open `index.html`** in a plain-text code editor. Free options: VS Code, Sublime Text,
   or the GitHub website's edit button. Don't use Word or Pages; they add hidden formatting.
2. **Find the section.** Every section starts with a marker like this:
   ```html
   <!-- ==================== EDIT 11 · PARTNERS AND DONORS ==================== -->
   ```
   Press **Ctrl+F** (Windows) or **⌘+F** (Mac) and search for `EDIT 11`, or for any
   word you can see on the page.
3. **Make the change** by copying an existing line and editing it. Recipes are in section 4.
4. **Preview it.** Double-click `index.html` to open it in your browser and check the change.
5. **Publish it.**
   - If the site is connected to GitHub, save, then commit and push. The host republishes
     automatically within about a minute.
   - If the site is on a regular host, upload the changed file(s) to replace the old ones.

**Back up first.** Before a big change, copy `index.html` to something like
`index-backup.html`. If something breaks, copy the backup back.

---

## 3. Section map

| Marker  | What's there |
|---------|--------------|
| EDIT 1  | Top menu (links to each section) |
| EDIT 2  | Opening: headline, intro paragraph, the two buttons, the Monday Ledger |
| EDIT 3  | Numbers strip (first delivery, volunteers, cities) |
| EDIT 4  | Story video |
| EDIT 5  | Our story (text + Seema's photo) |
| EDIT 6  | How it works (the three steps) |
| EDIT 7  | Photo gallery |
| EDIT 8  | Chapters (Austin, New York, Kuwait, Your city) |
| EDIT 9  | Team (leadership, volunteers, vendor partners, NYC chapter chairs) |
| EDIT 10 | Press articles |
| EDIT 11 | Partners and donors; partners and business advisors |
| EDIT 12 | Get involved: volunteer form, donation QR, start a chapter |
| EDIT 13 | Footer: about line, links, Instagram, allergy note, copyright year |
| EDIT 14 | Settings: contact email and first-delivery date (at the bottom of the file) |
| EDIT 15 | Colors (at the top of the file) |
| EDIT 16 | Blog (built but hidden; see "Turning on the blog") |

---

## 4. Common changes (copy, paste, edit)

### Add a partner, donor or advisor (EDIT 11)

Copy one line and change the website, the logo file name and the business name:

```html
<a class="partner" href="https://www.example.com" target="_blank" rel="noopener" data-logo="images/logos/example.png"><span class="p-name">Business Name</span></a>
```

For a long name, add a smaller second line (like the NextGen box):

```html
<a class="partner" href="https://www.example.com" target="_blank" rel="noopener" data-logo="images/logos/example.png"><span class="p-name">Short Name</span><span class="p-sub">Rest of the name</span></a>
```

- Put it in the right group: **Partners and Donors** or **Partners and Business Advisors**.
- In the Partners and Donors group, keep the dashed **"Your business here"** box last.
- If the name contains `&`, write it as `&amp;` (for example `Smith &amp; Sons`).
- To start a new group, copy a whole block: the `<div class="p-group">…</div>` heading
  plus its `<div class="partners">…</div>` box.

### Add a partner logo (EDIT 11)

Each partner box already has a logo slot. Save the logo into `images/logos/` with the
name in that box's `data-logo`, and the box switches from text to the logo automatically:

| Partner | Logo file name |
|---------|----------------|
| Whole Foods | `images/logos/whole-foods.png` |
| Trader Joe's | `images/logos/trader-joes.png` |
| La Fleur Florist | `images/logos/la-fleur.png` |
| Venus et Fleur | `images/logos/venus-et-fleur.png` |
| The DRIPBaR | `images/logos/dripbar.png` |
| NextGen | `images/logos/nextgen.png` |

- Use a PNG with a transparent background if possible, about 200 px tall.
- **Ask permission before using a company's logo.** Large brands (Whole Foods, Trader
  Joe's) have strict logo rules. Ask your store contact first. Until a logo is added,
  the box simply shows the name.

### Add a press article (EDIT 10)

```html
<a class="pcard" href="https://link-to-article" target="_blank" rel="noopener"><span class="p-src">Publication Name</span><span class="p-title">Article Title</span><span class="p-go">Read article &rarr;</span></a>
```

New articles usually go first, at the top of the list.

### Add a team member (EDIT 9)

1. Copy one whole `<div class="bio">…</div>` block and paste it in the right group.
2. Change the initials, name, role and bio:

```html
<div class="bio"><div class="ph bio-ph" data-img="images/team-firstname.jpg">FL</div><div><div class="m-name">First Last</div><div class="m-role">Volunteer</div>
  <p>Their bio paragraph goes here.</p></div></div>
```

3. Add their photo to `images/` with the same name as in `data-img`
   (here, `team-firstname.jpg`). Until the photo exists, the circle shows the initials.

**To remove someone,** delete their whole `<div class="bio">…</div>` block.

### Add or change a team photo

No HTML change is needed if the name matches. Save a square-ish photo, face centered,
under 500 KB, into `images/` using the name below:

| Person          | File name           | Status |
|-----------------|---------------------|--------|
| Seema Govil     | `avatar-seema.jpg`  | in place |
| Chris Kary      | `avatar-chris.jpg`  | in place |
| Pi              | `team-pi.jpg`       | in place |
| Lauren          | `team-lauren.jpg`   | in place |
| Missy Payne     | `team-missy.jpg`    | in place |
| Neelu           | `team-neelu.jpg`    | in place |
| Kevin           | `team-kevin.jpg`    | in place |
| Timothy Kary    | `team-timothy.jpg`  | in place |
| Kim             | `team-kim.jpg`      | in place |
| Ren Hogue       | `team-ren.jpg`      | **needed** |
| Serena Govil    | `team-serena.jpg`   | **needed** (a shared photo of both NYC chairs is `nyc-chairs.jpg`) |
| Karina Redkar   | `team-karina.jpg`   | **needed** |

### Add a gallery photo (EDIT 7)

- **Easiest:** save a photo as `images/gallery-7.jpg`. That slot already exists and
  appears as soon as the file is there.
- **More photos:** copy a line, change the file name, and add the file:
  ```html
  <div class="ph ph-sq" data-img="images/gallery-8.jpg"><div><span>✿</span>Short label</div></div>
  ```
- The **first** photo in the list is displayed large.
- **Photo policy:** photos should show volunteers, nurses or florists. Patient photos may
  only be used with the patient's written consent covering website use.

### Update the numbers (EDIT 3)

Change the text inside `stat-n` (the big number) or `stat-l` (the small label):

```html
<div class="stat"><div class="stat-n">7</div><div class="stat-l">Volunteers</div></div>
```

Also check the Austin chapter text in EDIT 8 ("a team of seven volunteers") and the
cities line at the top of EDIT 2.

### Add or update a chapter (EDIT 8)

```html
<div class="ch">
  <div class="ch-city">City Name</div>
  <div class="ch-status soon">Starting</div>
  <p>One or two sentences about this chapter.</p>
</div>
```

Use `class="ch-status live"` (pink label) once a chapter is delivering, and
`class="ch-status soon"` (grey label) while it's starting. Keep "Your city" last.

### Change the email that receives messages (EDIT 14)

At the bottom of `index.html`, change this one line:

```js
var CONTACT_EMAIL = 'Seema@thefranchiseconsultingcompany.com';
```

Both the volunteer form and the "Start a chapter" button use it.
Note: the volunteer form opens the visitor's own email app with their details filled in.
It doesn't send anything by itself.

### Replace the donation QR code (EDIT 12)

Save the new QR image as `images/donate-qr.png` (same name). If the recipient changes,
also update "MDJunior Inc" in the Donate card (EDIT 12): it appears in the paragraph, the image description and the small note under the QR.

### Replace the video (EDIT 4)

Overwrite `video/story.mp4` with the new video and `video/poster.jpg` with a still
image from it (shown before it plays). Keep the video under about 20 MB. The current one is
720p and about 7.6 MB. Free tools such as HandBrake can shrink a large video.

### Change the menu (EDIT 1)

```html
<a href="#press">Press</a>
```

The part after `#` must match a section's `id` (for example `id="press"`).
Section ids: `watch`, `story`, `how`, `gallery`, `chapters`, `team`, `press`,
`partners`, `help`.

### Footer, Instagram, allergy note, year (EDIT 13)

Edit the text directly. Each year, update `© 2026` at the bottom.

### Colors (EDIT 15)

At the top of the file, each color has a name and a value, such as `--forest:#22372A;`.
Change the value and it updates everywhere. Main brand colors:

| Name       | Used for |
|------------|----------|
| `--forest` | Dark green: buttons, the Get Involved band |
| `--bloom`  | Soft pink: Send button, status labels |
| `--sage`   | Sage green: "Email us" button |
| `--rose`   | Darker pink: the word *flowers* in the headline, links on hover |
| `--paper`  | Cream page background |

### Turning on the blog (EDIT 16)

The blog section is already built but hidden.

1. Find `EDIT 16` and, on the line `<section id="blog" hidden>`, delete the word `hidden`.
2. In `EDIT 1` (top menu), turn the Blog link on by changing
   `<!-- <a href="#blog">Blog</a> -->` to `<a href="#blog">Blog</a>`.
3. Replace the sample post with a real one. For each new post, copy one whole
   `<article class="post">…</article>` block and put the newest post first:

```html
<article class="post">
  <div class="post-date">October 2026</div>
  <h3 class="post-title">Post title</h3>
  <p class="post-excerpt">A one- or two-sentence summary shown before "Read more".</p>
  <details>
    <summary>Read more</summary>
    <p>First paragraph of the full post.</p>
    <p>Second paragraph.</p>
  </details>
</article>
```

A blog works best when someone commits to posting regularly. If posts stop, an old
"latest post" can make the site look abandoned, so keep it hidden until there's a plan.

### Logo

The menu and footer use `images/logo-mark.png`. Replace it with a new square image
(transparent background works best), keeping the same name.

---

## 5. Things to leave alone

- **The `<script>` block at the bottom,** except the two settings in EDIT 14.
  It powers the volunteer form, the photo loading and the Monday Ledger dots.
- **The `<style>` block at the top,** except the colors in EDIT 15.
- **Class names** such as `class="partner"` or `class="bio"`. Change the words between
  the tags, not the tags themselves.

---

## 6. Accounts and settings outside these files

| Item | Where it lives | Notes |
|------|----------------|-------|
| Donations | Zelle, MDJunior Inc | The QR image only points to MDJunior's Zelle account. |
| Volunteer and chapter emails | The email in EDIT 14 | Currently Seema's address. |
| Domain (flowersforjoy.org) | The domain registrar | Point it to whichever host serves these files. |
| Hosting | Vercel (current) | Any static host works. See section 1. |
| Instagram | @flowersforjoy24 | Linked in the footer. |

---

## 7. Quick check after any change

- [ ] The page opens and looks right on a computer **and** a phone
- [ ] Any new link opens the right website
- [ ] Any new photo shows (not a blank or initials circle)
- [ ] The video plays
- [ ] The volunteer form opens an email to the right address

---

## 8. Using the AI assistant (@claude)

The repository includes an optional AI assistant: Claude, made by Anthropic. Anyone with
write access to the GitHub repository can ask it, in plain English, to make a change.
Claude edits the site, then opens a **pull request** (a proposed change) that a person
reviews before anything goes live.

### One-time setup (a repository admin, about 10 minutes)

1. **Install the Claude GitHub App** on this repository: https://github.com/apps/claude
2. **Add a secret** in the repository: **Settings → Secrets and variables → Actions →
   New repository secret**. Use one of:
   - `ANTHROPIC_API_KEY`: an API key from https://platform.claude.com (pay per use), or
   - `CLAUDE_CODE_OAUTH_TOKEN`: a token from a Claude Pro, Max, Team or Enterprise
     subscription. If you use this, edit `.github/workflows/claude.yml` and swap the
     two lines marked there.
3. **Test it:** open an issue that says `@claude What sections does this site have?`
   and check that Claude replies.

Official instructions: https://code.claude.com/docs/en/github-actions

### Asking for a change

1. **If there are files** (photos, logos, a video), upload them first: on GitHub, open the
   `uploads/` folder → **Add file → Upload files**.
2. **Open a new issue** describing the change and mention `@claude`. Be specific:
   > @claude Add "Austin Flower Co." to Partners and Donors, linking to
   > https://www.austinflowerco.com. Their logo is uploads/austin-flower.png.

   > @claude Use uploads/ren.jpg as Ren Hogue's team photo.

   > @claude Add this press article: "Title", Publication Name, https://link
3. **Claude replies in the issue** and opens a pull request. Open it, check the summary
   and the changed files, then click **Merge**. The site updates within about a minute.

### Good to know
- **Nothing goes live without a person approving it.** Always look over the pull request.
- **Claude follows `CLAUDE.md`.** It won't make up bios, quotes or numbers, and it asks
  before publishing a photo that may show a patient without stated consent.
- **Cost:** each request uses GitHub Actions minutes (free allowance on most plans) plus
  Claude usage, either API charges or the subscription, depending on the secret you chose.
- **First run:** test it with one small change (like a photo) before relying on it.

