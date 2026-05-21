# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Site

Jekyll static site for **Lab Data dan Komputasi Geoteknik** (Lab DataGeo) at ITB, hosted on GitHub Pages at `lab-datageo.github.io`. Uses Bootstrap 4.4.1 for styling. Brand color: `#052049` (dark navy).

## Development Commands

```bash
# Install dependencies
bundle install

# Serve locally (available at localhost:4000)
bundle exec jekyll serve

# Build only
bundle exec jekyll build
```

To create an isolated environment via conda:
```bash
conda create -n jekyll -c conda-forge rb-jekyll
conda activate jekyll
bundle install
bundle exec jekyll serve
```

## Content Architecture

All content is managed as individual Markdown files in Jekyll collections. Page layouts assemble content dynamically via Liquid templating — there is no CMS or database.

### Collections (content directories)

| Directory | Purpose | Output page? |
|---|---|---|
| `_members/` | Current and past lab members | Yes |
| `_publications/` | Academic publications | Yes |
| `_projects/` | Engineering/consulting projects | Yes |
| `_funded_projects/` | Research grants and collaborations | No (rendered inline in `/research`) |
| `_student_research/` | Student thesis and research projects | Yes (detail cards) |
| `_research_themes/` | Research theme descriptions | No (currently commented out) |
| `_posts/` | News/blog posts | Yes |
| `_tags/` | Publication tag pages | Yes |
| `_authors/` | Author profile pages | Yes |

### Site pages

Pages are located in top-level directories (e.g., `members/index.html`, `research/index.html`). The `group:` front-matter field controls which nav link is highlighted as active — it must match the `group` field in `_data/navigation.yml`.

### Navigation

Edit `_data/navigation.yml` to add, remove, or reorder nav items. Commented-out entries (news, join) exist in the file but are hidden.

### Layouts and includes

- `_layouts/default.html` — base: header + content + footer
- `_layouts/home.html` — homepage: banner image left, content right
- `_layouts/members.html` — members page with alumni sidebar
- `_layouts/project.html`, `student_research.html` — detail pages for those collections
- `_includes/member_card.html` — reusable card component for displaying a member
- `_includes/header.html` — Bootstrap navbar; reads nav links from `_data/navigation.yml`

## Adding Content

Each collection has a `_template.md` with required/optional front-matter fields. Copy the template when creating new entries.

**Member** (`_members/`): Required fields are `name`, `startdate`, `image`, `altimage`, `position`, `email`, `orcid`, `scholar`, `description`. Images should be 365×365px, 72 dpi, placed in `/static/img/members/`. Active members have blank `enddate`; alumni have a date set.

**Publication** (`_publications/`): Bold lab member names in the `authors` field using `**Surname FM**`. Use `&#42;` (not `*`) for co-first/corresponding author asterisks to avoid breaking bold formatting.

**Funded project** (`_funded_projects/`): The `order` field controls card sort order on the research page (lower = displayed first).

**Student research** (`_student_research/`): The `order` field controls card sort order. `status: "Ongoing"` renders a green badge; anything else renders grey.

**Project** (`_projects/`): Use `service_type` and `market_sector` for categorization.
