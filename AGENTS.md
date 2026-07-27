# AGENTS.md

Orientation for agents working in this Obsidian vault.

## Vault Structure

```text
vault/
├── .obsidian/    # Obsidian app config (don't modify)
├── Assets/       # Static files (images, icons)
├── Notes/        # All editable content (markdown + excalidraw)
└── Templates/    # Note templates
```

**Folder rules:**
- **Assets/** — Static files only: images, icons, attachments. Not edited in
  Obsidian.
- **Notes/** — All editable content goes here flat. This includes markdown
  notes and Excalidraw diagrams (`.excalidraw.md`). No subfolders.
- **Templates/** — Obsidian templates for note creation.

Organization is done through **tags and links**, not folders.

## Note Naming Convention

Notes use a **prefix pattern** for easy scanning:

```text
<Topic> - <Subject>.md
```

Examples:
- `Azure - Storage Accounts.md`
- `Linux - User Management.md`
- `Git - Signing Commits.md`

Excalidraw diagrams can use either:
- `<Topic> - <Subject>.excalidraw.md`
- `<topic>-<subject>.excalidraw.md`

## Frontmatter and Tags

Every note must include YAML frontmatter with hierarchical tags:

```markdown
---
tags:
  - azure/storage
  - diagram
---
```

**Tag conventions:**
- Use lowercase with `/` for hierarchy: `azure/networking`, `linux/admin`
- Use `diagram` tag for all Excalidraw files
- Tags are the primary discovery mechanism — be generous with them

## Linking

- Link to related notes: `[[Azure - Virtual Networks]]`
- Link liberally — connections surface through the graph view and backlinks
- Prefer links over duplicating content

## Content Style

- Use standard markdown formatting
- Use code blocks with language hints for commands/code
- Keep content concise and actionable
- Include error messages when documenting fixes (aids searchability)
- Add a "References" section at the bottom for source docs/articles

## Creating Notes

1. Place in `Notes/` (flat, no subfolders)
2. Use the prefix naming convention
3. Add frontmatter with relevant tags
4. Link to related notes

## Anti-patterns

- Don't create subfolders in `Notes/` for organization — use tags
- Don't create MOC (Map of Content) notes — use tag searches instead
- Don't put editable content in `Assets/`
