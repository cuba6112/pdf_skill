# PDF Generator Skill

Cross-platform PDF generator from JSON. Pre-compiled binaries - no build required.

## Binaries

| Binary | Platform |
|--------|----------|
| `pdf_generator-macos-arm64` | macOS Apple Silicon |
| `pdf_generator-macos-x64` | macOS Intel |
| `pdf_generator-linux-x64` | Linux x64 |
| `pdf_generator-windows-x64.exe` | Windows x64 |

## Usage

```bash
./bin/pdf_generator-macos-arm64 input.json output.pdf --themes-file themes/themes.json
./bin/pdf_generator-macos-arm64 input.json output.pdf --theme ocean_blue --themes-file themes/themes.json
./bin/pdf_generator-macos-arm64 --list-themes --themes-file themes/themes.json
```

## JSON Format

```json
{
  "metadata": { "title": "Doc Title", "author": "Name" },
  "config": {
    "toc": { "enabled": true },
    "header_footer": { "show_footer": true, "show_page_numbers": true }
  },
  "content": [
    {
      "type": "chapter",
      "title": "Chapter 1",
      "sections": [{
        "title": "Section",
        "content": [
          { "type": "paragraph", "text": "Text here." },
          { "type": "list", "items": ["A", "B"], "ordered": false },
          { "type": "code", "code": "print('hi')", "language": "python" },
          { "type": "table", "headers": ["Col1"], "rows": [["Val"]] },
          { "type": "callout", "text": "Note", "callout_type": "info" }
        ]
      }]
    }
  ]
}
```

## Content Types

`paragraph` | `list` | `code` | `table` | `callout` | `image` | `heading` | `spacer` | `page_break` | `chapter` | `appendix` | `glossary`

## Themes

40+ themes: `default`, `corporate_blue`, `ocean_blue`, `midnight`, `forest_green`, `sunset_orange`, `tech_dark`, `minimalist`

```
pdf_skill/
├── bin/           # Binaries
├── themes/        # themes.json
├── examples/      # Sample JSON
└── SKILL.md
```
