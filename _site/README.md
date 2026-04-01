# Danais Lab Website

This site is built with Jekyll. All editable content lives in YAML files under `_data/`.
The `_sections/*.md` files are just wrappers that include HTML templates from `_includes/sections/`.

## Working With LLMs / Codex

This repo is friendly to LLM-based editors if they follow a few simple rules.

### Source of truth

- Edit source files only.
- Do not edit `_site/` directly; it is generated output.
- Most content changes should start in `_data/*.yml`.
- Layout and rendering changes usually belong in `_includes/`, top-level `.html` pages, `styles.css`, or `main.js`.

### Editing rules

- Keep YAML indentation consistent with the existing files (2 spaces).
- Preserve the existing order and structure unless the task requires changing it.
- Put people images under `images/people/`.
- Put publication PDFs that should be served by this site under `files/papers/`.
- If a person has no image yet, keep `initials` so the site can render a fallback.
- Use full URLs for external links.
- After content edits, prefer checking the generated page instead of editing generated HTML.

## Where to edit content

- Hero: `_data/hero.yml`
- About: `_data/about.yml`
- News: `_data/news.yml`
- Projects: `_data/projects.yml`
- People: `_data/people.yml`
- Publications: `_data/publications.yml`
- Sponsors: `_data/sponsors.yml`
- Contact: `_data/contact.yml`
- Footer: `_data/footer.yml`

## Common Tasks

- Add or update homepage hero text: `_data/hero.yml`
- Add or update the about section: `_data/about.yml`
- Add or update news items: `_data/news.yml`
- Add or update projects: `_data/projects.yml`
- Add or update people: `_data/people.yml`
- Add or update publications: `_data/publications.yml`
- Change how a section is rendered: `_includes/sections/*.html`
- Change page-level structure or metadata: top-level `.html` files
- Change styles or interactions: `styles.css` and `main.js`

## Examples

### Add a person
Edit `_data/people.yml` and append to a group.

```yml
  - title: "Current Members"
    people:
      - name: "New Student"
        title: "PhD Student (2025-)"
        note: "Co-supervised with A. Advisor."
        url: "https://example.com"
        image: "images/people/new-student.jpg"
        initials: "NS"
```

### Add a project
Edit `_data/projects.yml` and append to `projects`.

```yml
projects:
  - title: "New Project Title"
    text: "One-sentence description of the project."
```

### Add a publication
Edit `_data/publications.yml`. Add a new entry under the correct year.

```yml
years:
  - year: 2025
    entries:
      - venue: "SIGMOD"
        title: "Paper title here"
        authors: "A. Author, B. Author, and C. Author"
        links:
          - label: "PDF"
            url: "https://example.com/paper.pdf"
          - label: "BibTex"
            url: "https://example.com/paper.bib"
        note: "(to appear)"
```

If you do not have an external PDF URL yet, add the PDF file to `files/papers/` and point the `PDF` link to the site path instead.

```yml
years:
  - year: 2026
    entries:
      - venue: "VLDB"
        title: "Toward Drift-Aware Database Benchmarking"
        authors: "G. Liu and R. Borovica-Gajic"
        links:
          - label: "PDF"
            url: "/files/papers/toward-drift-aware-database-benchmarking.pdf"
        note: "(to appear)"
```

## Local preview

From the repo root:

```bash
bundle install
bundle exec jekyll serve
```

For a one-off validation build:

```bash
bundle exec jekyll build
```

## Done Checklist

- The change was made in source files, not in `_site/`
- YAML remains valid and consistently indented
- New images, if any, were added to the correct folder
- `bundle exec jekyll build` succeeds
- The updated page looks correct in local preview

## Example Prompts For LLMs

- Add a new publication under the correct year in `_data/publications.yml` and keep the existing ordering style.
- Add a new lab member to `_data/people.yml`; if no photo is available, keep `initials` so the fallback renders correctly.
- Update the homepage hero content in `_data/hero.yml` without changing the page structure.
- Change the rendering of the people section in `_includes/sections/people.html` and keep existing data fields compatible.
- Update the about page copy and verify the site still builds with Jekyll.
