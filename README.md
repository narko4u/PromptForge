PromptForge stores prompt data in a local `.promptforge/` directory inside your project:

## Architecture

![PromptForge Architecture](promptforge-architecture.svg)

PromptForge stores prompt data in a local `.promptforge/` directory. Every command flows through a simple pipeline:

```
Developer CLI
    │
    ├── pf init     ──▶  Creates .promptforge/ repo
    ├── pf add      ──▶  Version Store (SQLite)
    ├── pf diff     ──▶  Diff Engine (line-by-line)
    ├── pf tag      ──▶  Tag Manager (labels)
    └── pf export   ──▶  JSON output
                            
         ┌─────────────────────┐
         │   .promptforge/     │
         │                     │
         │  ┌───────────────┐  │
         │  │ Version Store │  │
         │  │  (SQLite DB)  │  │
         │  │  v1 → v2 → v3 │  │
         │  └───────┬───────┘  │
         │          │          │
         │  ┌───────▼───────┐  │
         │  │  Diff Engine  │  │
         │  │  comparison   │  │
         │  └───────┬───────┘  │
         │          │          │
         │  ┌───────▼───────┐  │
         │  │ Tag Manager   │  │
         │  │ label+export  │  │
         │  └───────────────┘  │
         └─────────────────────┘
```

