## Guitar teacher website – Kitara Studio

This is a single‑page website for a guitar instructor focused on **adult beginners and advanced students**, with an emphasis on **modern fingerstyle**, **improvisation**, **instrumental covers**, and **original instrumental music**.

The site is fully static (**HTML/CSS/JS only**) so you can deploy it easily to any static host (Netlify, GitHub Pages, Vercel, shared hosting, etc.).

---

### Files

- **`index.html`**: Main page markup (sections: hero, what I teach, technique videos, pricing, contact).
- **`styles.css`**: Layout and styling (responsive, dark high‑end aesthetic).
- **`script.js`**: Language switching, navigation, smooth scrolling and contact form behavior.

---

### Bilingual content (English / Slovenian)

All text on the page is driven by a small translation dictionary in `script.js`:

- **English keys** are in `translations.en`.
- **Slovenian keys** are in `translations.sl`.

The language switch in the header (EN / SL) calls `setLanguage(lang)`, which:

- Updates the page text via `data-i18n` attributes on elements.
- Updates placeholders via `data-i18n-placeholder`.
- Stores the selected language in `localStorage` so it persists on refresh.

If you want to change wording:

1. Open `script.js`.
2. Find the `translations` object.
3. Edit the English and/or Slovenian strings for the keys you care about.

You can also add new keys (e.g. for extra sections), just make sure:

- The element in `index.html` has a matching `data-i18n="your.key"`.
- You add that key to both `translations.en` and `translations.sl`.

---

### Prices and lesson details

Prices and lesson structure are visible in two places:

- **Text in `script.js`** (for translation).
- **The visual formatting in `index.html` / `styles.css`**.

To change lesson prices or duration, **only edit the strings in `script.js`**:

- `pricing.online.price` → currently `25 € / 45‑minute lesson or 30 € / 60‑minute lesson`.
- `pricing.inperson.price` → currently `40 € / 45‑minute lesson or 50 € / 60‑minute lesson`.
- Anywhere the free introductory lesson is mentioned (search for `freeNote` and `hero.badge` / `pricing.title`).

If you ever change the actual lesson length (e.g. from 45 min to 60 min), update:

- The hero badge (`hero.badge`, `pricing.title`, etc.).
- The stat labels in the hero (`hero.stat1Number`, `hero.stat1Label`).

---

### Contact email and form

The contact email is currently set to:

- `tstepisnikp@gmail.com`

To change it later, search for `tstepisnikp@gmail.com` in both `index.html` and `script.js` and replace it.

The contact form uses `mailto:`:

- On submit, it opens the user’s email client with a pre‑filled subject and body.
- This avoids needing a backend and works fine for a solo instructor site.

If you later want a more advanced form (with a backend or a service like Formspree), you can:

- Remove the `mailto:` logic in `initContactForm()` in `script.js`.
- Replace it with an API call or form service integration.

---

### Video placeholders

The “Technique videos” section currently uses the same sample video URL as a placeholder:

- Defined directly in `index.html` in the `#videos` section.
- Each `<video>` tag points to `https://www.w3schools.com/html/mov_bbb.mp4`.

To use your own technique clips:

1. Upload your `.mp4` videos to your hosting (or YouTube / Vimeo).
2. Replace each `src` attribute with your real URL.
3. Optionally add `poster="path-to-thumbnail.jpg"` for a custom thumbnail.

You can also replace the `<video>` tags with embeds (YouTube iframe etc.) if you prefer.

---

### Running the site locally

Since this is a static site, you can open it directly:

1. Double‑click `index.html` to open it in your browser, **or**
2. Run a small static server (recommended, especially for later expansions), e.g.:

```bash
cd /Users/timen/Desktop/kitara-web
python3 -m http.server 4173
```

Then open `http://localhost:4173` in your browser.

---

### Deploying the site

You can deploy this folder as‑is to any static host. A few common options:

- **Netlify**
  - Create a new site, drag‑and‑drop the project folder or connect a Git repo.
  - No build step needed; publish directory is just the project root.

- **Vercel**
  - Create a new project, select “Other” / static.
  - Set the root directory to the project (where `index.html` lives).

- **GitHub Pages**
  - Create a repo with these files.
  - Enable GitHub Pages on the `main` branch (root).

Once deployed, you’ll get a public URL which you can share with students.

---

### Customizing for your teaching brand

Ideas you can easily adjust:

- **Colors & feel** → tweak CSS variables at the top of `styles.css` (e.g. `--accent`, `--bg`).
- **Name & logo text** → in the header (`.logo-text` in `index.html`) and translations in `script.js`.
- **Copy for adult beginners vs. advanced players** → mainly `hero.*`, `lessons.*`, `videos.*` keys in `script.js`.
- **Extra sections** → create a new `<section>` in `index.html`, then add matching `data-i18n` keys and CSS blocks.

This setup is intentionally minimal but high‑end, so you can extend it without needing a full framework.


