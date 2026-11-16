# Verifiable Compute Foundation website

A plain static site: HTML files, one small stylesheet, no build step. Whatever is in this folder is what gets served.

## What is in here

| File | What it is |
|---|---|
| `index.html` | Home page |
| `people.html` | People page |
| `research.html` | Research & News page (the list of articles) |
| `news-research-cluster-open.html` | An article |
| `template-article.html` | Blank article to copy. Not linked from anywhere. |
| `template-page.html` | Blank page to copy. Not linked from anywhere. |
| `assets/site.css` | Shared base styles (link colours, focus outline) |
| `assets/favicon.svg`, `assets/logo-mark-*.svg` | Browser tab icon and the logo mark |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

Most styling is written directly on each element (`style="..."`). To change how something looks, edit it where it is.

## Preview on your computer

Double-click any `.html` file to open it in a browser. Links between pages work locally.

## Publish with GitHub Pages

1. Create a new repository on GitHub and push this folder to it:

   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR-ORG/YOUR-REPO.git
   git push -u origin main
   ```

2. In the repository on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. To use `verifiablecompute.ai`, enter it under **Custom domain** on the same screen and follow GitHub's instructions for the DNS records.

After that, every push to `main` updates the live site within a minute or two. Cloudflare Pages and Netlify work the same way: connect the repository, leave the build command empty, and set the output folder to the root.

## Edit text

Open the page's `.html` file, find the sentence (search for a few words of it), change it, save, commit, push. Only change the words between the tags, not the tags themselves.

## Add an article

1. Copy `template-article.html` and rename the copy `news-short-title.html` (lower case, hyphens, no spaces).
2. In the copy, replace every placeholder in CAPITALS: `ARTICLE TITLE` (three times: the `<title>` near the top, the headline, and `ARTICLE%20TITLE` in the email share link), `ONE-SENTENCE SUMMARY` (twice), `NEWS, EVENT OR RESEARCH`, `MONTH YEAR`, `IMAGE CAPTION`, and the `LABEL` / `FACT` pairs in the At a glance box.
3. Delete the line near the top that contains `noindex`. It keeps the template out of search engines and must not stay in a real article.
4. Write the article between `<!-- ARTICLE BODY -->` and `<!-- END ARTICLE BODY -->`, copying the paragraph, subheading and list lines that are already there.
5. Open `research.html`, find `<!-- NEW ARTICLES GO HERE`, copy one of the `<article> ... </article>` blocks below it, paste it directly under that comment, and change the date, type, title, summary and the `href` to your new file name.
6. Optional: on `index.html`, the three cards under `<!-- RESEARCH & NEWS -->` show the newest items. Replace the oldest one.
7. Commit and push.

To add a lead image, put the file in `assets/` and replace the striped placeholder `<div aria-hidden="true" ...> ... </div>` under `<!-- LEAD IMAGE -->` with:

```html
<img src="assets/your-image.jpg" alt="Describe the image" style="width: 100%; aspect-ratio: 21 / 9; object-fit: cover">
```

## Add a page

1. Copy `template-page.html` and rename the copy, for example `about.html`.
2. Replace `PAGE TITLE`, `ONE-SENTENCE SUMMARY`, `SHORT LABEL`, `PAGE HEADLINE` and the intro sentence, and delete the `noindex` line.
3. Write the content in the section under `<!-- CONTENT -->`. Copy the whole `<section> ... </section>` block for each further section.
4. Link to it. To underline the current page in the menu, copy the `aria-current="page" style="..."` attributes from the People link in `people.html` onto your page's own menu link. The navigation and footer are repeated in every `.html` file, so a new menu link has to be added to each of them: search all files for `<nav aria-label="Main"` and add `<a href="about.html">About</a>` in the same place in each. A project-wide find-and-replace in an editor such as VS Code does this in one step.

## Change the navigation or footer

They are copied into every page (including the two templates), so make the same change in each file. Search for `<!-- NAV -->` and `<!-- FOOTER -->`.

## Before launch

- The **Subscribe** forms on the home and research pages do nothing yet. They need to be connected to a newsletter service.
- The **Privacy policy** link in the footer points nowhere.
- The **LinkedIn** and **X** links point at those sites' home pages, not at VCF accounts.
- Team photos and the article's lead image are striped placeholders, and three job titles on the People page read `TITLE`.
- The font (Hanken Grotesk) loads from Google Fonts. To avoid sending visitors' requests to Google, download the font files into `assets/` and load them from `assets/site.css` instead.
- The site has no analytics and no cookie banner, and does not need one as it stands.

## Brand

- Colour: anthracite blue `#22303F` on white, and white on `#22303F`.
- Typeface: Hanken Grotesk, medium weight for headings and the logo.
