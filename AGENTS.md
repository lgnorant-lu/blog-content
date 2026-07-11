# Content Writing Rules

> Blog content management. Applies when editing files under `content/`.
> See `docs/content-spec.md` for full specification and
> `docs/specs/frontmatter.md` for complete field definitions.

## File Naming

```
YYYY-MM-DD-slug.md      ← published posts
drafts/*.md              ← unpublished drafts
pages/*.md               ← static pages
templates/*.md           ← post/page templates (not scanned)
```

## Frontmatter Reference

All fields and their semantics are defined in
[frontmatter.md](../docs/specs/frontmatter.md).
Quick reference:

| Field | Required | Type | Example |
|-------|----------|------|---------|
| `title` | yes | string | `"Hello World"` |
| `date` | yes | string | `2026-07-09` |
| `updated` | no | string | `2026-07-11` |
| `author` | no | string | `"lgnorant-lu"` |
| `cover` | no | string | `"/images/cover.png"` |
| `draft` | no | bool | `false` |
| `slug` | no | string | `"hello-world"` |
| `summary` | no | string | auto from body |
| `tags` | no | string list | `["go", "tui"]` |
| `categories` | no | string list | `["tech"]` |
| `keywords` | no | string | `"golang, ssh, tui"` |
| `series` | no | string | `"blog-tui series"` |
| `weight` | no | int | `10` |

### tags vs categories vs keywords

Three orthogonal fields — each serves a distinct purpose:

- `categories`: broad area (3-5 values, browsable in TUI)
- `tags`: dimension labels (5-15 values, browsable in TUI)
- `keywords`: fine-grained search terms (comma-separated string, FTS5 indexed)

## Markdown Rules

- Use standard GFM (Tables, fenced code blocks, task lists)
- Headings: `##` for sections (reserve `#` for title)
- Code blocks with language: ` ```go `
- No raw HTML
- No emoji
- English terms keep English casing (e.g. "SSH TUI Blog", not "SSH TUI 博客")

## TOC

Each post MUST have a TOC at the top (after frontmatter). Run `make toc` to generate.

## Drafts

- Work in `content/drafts/` while writing
- Set `draft: true` to hide from published view
- Remove `draft: true` and move to `content/posts/` when ready
- Template: copy `content/templates/post-template.md` to start a new post
