# Dance with Depression: Design Document

Static replica of dancewithdepression.org (originally WordPress on Hostinger). Plain HTML and CSS, no build step, no database. Store it in a Git repository (GitHub is free) so every change is versioned.

## 1. Structure

| File | Page | Notes |
|---|---|---|
| `index.html` | Home | Hero, mission, approach, about teaser |
| `about.html` | About Us | Story, core values, name, board bios, projects |
| `approach.html` | Approach | Financial and hands-on support, NAMIWalks example |
| `donate.html` | Donate | Podcast matching grant (1 Dec 2026 – 1 Mar 2027), NAMIWalks outcome |
| `contact.html` | Contact | Email and form |
| `css/styles.css` | Styles | All colors, fonts, and layout |

The header and footer are copied into each HTML file. If you change the menu, edit all five files (search for `<header class="top">`).

## 2. Design tokens (top of `css/styles.css`)

Matched to screenshots of the live site (Nov 2026).

| Token | Value | Use |
|---|---|---|
| `--purple` | #6e5f9b | Buttons, About Us heading, links, heading underline, footer bar |
| `--ink` | #222 | Body text |
| `--gray` | #efefef | Section band behind About Us |
| `--hero` | mountain photo + blue overlay | Hero background (`images/hero.jpg`) |
| `--foot` | wildflower photo | Footer background (`images/footer.jpg`) |

Fonts (Google Fonts): Playfair Display for headings (tight letter-spacing, purple rule underneath), Lato for body, nav, and buttons. The header is transparent over the hero, with a white outlined Donate button. Colors are eyeballed from screenshots; confirm exact values in WordPress (Appearance → Customize).

## 3b. How to make common edits
- **Text:** open the page file, find the paragraph, edit it.
- **Colors or fonts:** change the tokens in `styles.css`.
- **New page:** copy `approach.html`, rename it, edit `<main>`, add a link in each header and footer.
- **New project or news:** copy a `<figure>` in `about.html` or a `<section class="band">` block.

## 4. Things to finish before going live
1. **Hero and footer photos:** save the mountain hero photo and wildflower footer photo from the WordPress media library as `images/hero.jpg` and `images/footer.jpg`. Until then a blue gradient and green gradient stand in.
1b. **Other images:** pages currently load images from the old WordPress site (`dancewithdepression.org/wp-content/uploads/...`). Download them from the WordPress media library into an `images/` folder and update the `src` paths, or they will break when the old site is removed.
2. **Contact form:** replace `YOUR_FORM_ID` in `contact.html` with a free form ID from formspree.io (or another form service). Static sites cannot send email by themselves.
3. **Donations:** the Donate page links to Zeffy. Add a general donation link if you want one.
4. **Copy:** long bios and the About quote are condensed. Compare against the live site and paste in any full text you want kept.
5. **Hosting:** upload the folder to Hostinger (public_html), or use Netlify, Cloudflare Pages, or GitHub Pages. Point the domain at the new host.
6. **Accessibility:** alt text is included; add more descriptive alt text for new photos.
