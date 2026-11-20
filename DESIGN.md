# Dance with Depression: Design Document

Last updated: 19 Nov 2026

A static replica of dancewithdepression.org (originally WordPress on Hostinger), rebuilt from screenshots and text of the live site. Plain HTML and CSS: no build step, no database, no plugins. Keep it in a Git repository (GitHub) so every change is versioned.

## 1. Files

| File | Page | Contents |
|---|---|---|
| `index.html` | Home | Full-width hero, Our Mission, Our Approach, About Us band |
| `about.html` | About Us | Our Inspiring Journey, Our Story, Core Values, Our Name, Board of Directors, Projects |
| `approach.html` | Approach | Split hero, Our Approach, Financial Support, Hands-on Support, NAMIWalks Utah 2026 example |
| `donate.html` | Donate | Podcast initiative card, NAMIWalks Utah 2026 card |
| `contact.html` | Contact | Get in Touch hero, email, contact form |
| `css/styles.css` | Styles | All colors, fonts, and layout (one file) |
| `images/` | Local images | Add `hero.jpg` and `footer.jpg` here (see section 6) |
| `DESIGN.md` | This document | |

The header and footer are copied into every HTML file, so a menu change means editing all five files (search for `<header class="top">` and `<footer class="foot">`).

## 2. Design tokens

Defined at the top of `css/styles.css`. Values were estimated from screenshots; confirm exact brand values in WordPress (Appearance → Customize).

| Token | Value | Use |
|---|---|---|
| `--purple` | #6e5f9b | Buttons, links, About Us heading, footer bar |
| `--ink` | #222 | Body text |
| `--gray` | #efefef | Gray section bands |
| `--serif` | Playfair Display | Headings (tight letter-spacing) |
| `--sans` | Lato | Body, menu, buttons |
| `--hero` | mountain photo + blue overlay | Home hero (`images/hero.jpg`) |
| `--foot` | wildflower photo | Footer (`images/footer.jpg`) |

Other colors set directly in the CSS: lavender card `#f1eff8` (`.card`), Core Values box `#f5f4f9` (`.values`), sage green `#7d8a6a` (Core Values heading), light purple rule `#a99fd0` (Approach headings), Approach hero `#e4e2e6`, Contact hero `#f5f7f4`, form border `#6f8a5a`.

Fonts load from Google Fonts in each page's `<head>`.

## 3. Layout and components

- **Header:** transparent over the home hero with white text and an outlined Donate button. On inner pages `<body class="sub">` switches it to dark text, with the current page in light purple.
- **Heading style:** Playfair Display with a purple rule underneath (`h2::after`). Variants: `h2.plain` (no rule), `h2.purple-h` (purple, no rule), `h2.sage`.
- **Buttons:** `.btn` (solid purple, square corners), `.btn.alt` (outline), `.btn-line` (white outline in header).
- **Sections:** `.band` (gray background), `.soft` (light gray), `.values` (lavender box with shadow), `.card` (lavender box with shadow, used on Donate).
- **Grids:** `.two` (two columns), `.cols3` (three columns), `.cards` (project photos), `.ex` (text left, photos right).
- **Hero variants:** `.hero` (photo, home), `.hero.sm` (white title area), `.hero.tint` (Contact), `.split` (Approach).
- **Mobile:** columns stack below about 700px. Mobile has not been tested in a real browser.

## 4. Page notes

- **Home:** logo above the title, tagline in spaced capitals, About Us copy matches the live site.
- **About:** board photos and project photos are loaded from the old site (see section 6).
- **Approach and Donate:** both contain the full NAMIWalks Utah 2026 text and photos. This duplicates content, so any edit must be made in both files (look for `NAMIWalks Utah 2026`). One option is to keep it on a single page and link from the other.
- **Donate:** podcast card links to the Zeffy donation form and the Spotify show.
- **Contact:** the form posts to Formspree (see section 6).

## 5. How to make common edits

- **Change text:** open the page file and edit the paragraph.
- **Change colors or fonts:** edit the tokens at the top of `styles.css`.
- **Add a page:** copy `approach.html`, rename it, replace the contents of `<main>`, then add a link in the header and footer of every page.
- **Add a project card:** copy a `<figure>` inside `.cards` on `about.html`.
- **Add a board member:** copy an `<article>` inside `.bios` on `about.html`.

## 6. Open items before going fully live

1. **Hero and footer photos:** save the home-page mountain photo as `images/hero.jpg` and the wildflower footer photo as `images/footer.jpg`. Until then gradients stand in.
2. **Other images:** pages load photos from `dancewithdepression.org/wp-content/uploads/`. Download them from the WordPress media library into `images/` and update the `src` paths, or they will disappear when the old site is removed.
3. **Contact form:** replace `YOUR_FORM_ID` in `contact.html` with a form ID from formspree.io. Static sites cannot send email on their own. The country-code list has six options; the live form lists every country.
4. **Links not copied:** in Eva Chan's bio, Community Board 11, Greater Harlem Coalition, NAMIWalks Utah and the Health Committee are plain text here. Add their web addresses if wanted.
5. **Wording kept from the live site:** "suicidal prevention training", "We raised 90,000 of funding", and "a nonprofit Hong Kong". Fix on both sites if desired.
6. **Corrected link:** the live site links to `namitwalks.org/utah`; this version links to `namiwalks.org/utah`.
7. **Header and footer** are repeated in each file, and the Home hero text and photos were matched to screenshots only. Compare each page side by side with the live site.

## 7. Deploying

1. Upload the folder contents to a GitHub repository (Add file → Upload files).
2. Host with GitHub Pages, Netlify, Cloudflare Pages, or upload the files to Hostinger's `public_html`.
3. Keep `css/` and `images/` next to the HTML files, and remove old WordPress files from `public_html` first.
4. Point the domain at the new host.

## 8. Change log

- **19 Nov 2026:** CSS link now ends in `?v=20261119`; change the number after each CSS edit so browsers and Hostinger fetch the new file.
- **19 Nov 2026:** first version, then restyled to match screenshots of Home, About, Approach, Donate, Contact. Podcast initiative moved into a lavender card on Donate.
