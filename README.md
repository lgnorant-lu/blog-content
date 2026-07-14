# blog-content

Private content repository for [blog-tui](https://github.com/lgnorant-lu/blog-tui).

## Layout

```
posts/       published articles (YYYY-MM-DD-slug.md)
drafts/      work in progress (not shown as published)
pages/       static pages (about, etc.)
templates/   post templates (not scanned by the engine)
config.yaml  site configuration
AGENTS.md    writing rules for agents and humans
```

## Local development

Clone next to the engine as `content/`:

```bash
git clone git@github.com:lgnorant-lu/blog-tui.git
git clone git@github.com:lgnorant-lu/blog-content.git blog-tui/content
cd blog-tui
make run
```

## Writing

1. Copy `templates/post-template.md` or use engine `make new-post SLUG=...`
2. Edit under `drafts/` until ready
3. Move to `posts/`, set `draft: false`, ensure TOC section exists
4. Push to `main` — server webhook pulls and rebuilds the index

See [AGENTS.md](AGENTS.md) for frontmatter and Markdown rules.

## CI

Push / PR runs TOC presence check only (no Go build).

## Line endings

`.gitattributes` forces LF for Markdown and YAML (Windows-safe).
