# Data Analyst Portfolio

A single-file, responsive portfolio site themed around an analyst's everyday tools —
a SQL console, a dataframe-style "about" card, a skills heatmap, project "notebook
cells", and a changelog-style experience timeline.

Everything lives in **`index.html`** — one file, no build step, no dependencies
(besides Google Fonts, loaded from a CDN link in the `<head>`).

---

## 1. Customize the content

Open `index.html` and scroll to the `<script>` tag near the bottom. Right under
the comment:

```
/* ============ EDIT YOUR CONTENT HERE ============ */
```

you'll find plain JavaScript objects/arrays:

| Object       | Controls                                                            |
|---------------|----------------------------------------------------------------------|
| `PROFILE`     | Name, role, location, bio, links, résumé URL, status pill           |
| `METRICS`     | The 4 stat counters (e.g. "120+ Dashboards shipped")                 |
| `SKILLS`      | Skill groups + proficiency bars (level 1–5)                          |
| `PROJECTS`    | Project / case-study cards (the "notebook cells")                   |
| `EXPERIENCE`  | Work history timeline, most recent first                             |

**To add a new project**, copy one object inside the `PROJECTS` array (between
`{` and `}`, including the trailing comma) and edit the copy — a new card appears
automatically, no HTML editing required. Same idea for `SKILLS` and `EXPERIENCE`.

### Adding a résumé
Drop a PDF (e.g. `resume.pdf`) in the same folder as `index.html`, then set:
```js
resumeUrl: "resume.pdf",
```

### Contact form
The form posts to [FormSubmit](https://formsubmit.co/) — a free service that
forwards form submissions to an email address, no signup required. Find this
line in `index.html`:

```html
<form class="contact__form reveal" id="contact-form" action="https://formsubmit.co/REPLACE_WITH_EMAIL@example.com" method="POST">
```

Replace `REPLACE_WITH_EMAIL@example.com` with a real email address. The **first**
submission triggers a one-time confirmation email from FormSubmit — click the
link in it to activate the form.

---

## 2. Preview locally

Just open `index.html` in a browser — no server needed. (Some browsers restrict
`fetch`/module imports from `file://`, but this page uses neither, so it works
fine directly from disk.)

---

## 3. Deploy

### Option A — GitHub Pages
1. Create a new GitHub repository and push this folder to it (the `index.html`
   should be at the repo root, or in a `/docs` folder).
2. In the repo, go to **Settings → Pages**.
3. Under **Source**, choose the branch (e.g. `main`) and folder (`/` or `/docs`).
4. Save — your site will be live at `https://<username>.github.io/<repo-name>/`
   within a minute or two.

### Option B — Cloudflare Pages
1. Push the project to a GitHub (or GitLab) repository, as above.
2. In the Cloudflare dashboard, go to **Workers & Pages → Create → Pages →
   Connect to Git**, and pick the repository.
3. Build settings: leave the **build command empty** and set the
   **output directory** to `/` (this is a static, no-build site).
4. Deploy — Cloudflare gives you a `*.pages.dev` URL immediately, and you can
   attach a custom domain for free afterwards.

Both options are free for a personal portfolio. See the chat response for a
quick comparison of which to pick.
