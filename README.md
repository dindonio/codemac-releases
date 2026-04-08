<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="CodeMax++ Icon">
</p>

<h1 align="center">CodeMax++</h1>

<p align="center">
  A native macOS code editor with a custom Core Text rendering engine.<br>
  Professional-grade performance. Instant large file loading. Built with Swift 6.0.
</p>

<p align="center">
  <a href="https://apps.apple.com/app/codemac/id6760980848"><img src="https://img.shields.io/badge/Mac_App_Store-Download-blue?logo=apple" alt="Mac App Store"></a>
  <img src="https://img.shields.io/badge/macOS-15%2B-blue?logo=apple" alt="macOS 15+">
  <img src="https://img.shields.io/badge/Swift-6.0-orange?logo=swift" alt="Swift 6.0">
  <img src="https://img.shields.io/badge/Languages-31_(+10_tree--sitter)-green" alt="31 Languages">
  <img src="https://img.shields.io/badge/Themes-6-purple" alt="6 Themes">
  <img src="https://img.shields.io/badge/Engine-Custom_Core_Text-red" alt="Custom Engine">
  <img src="https://img.shields.io/badge/License-Proprietary-red" alt="Proprietary">
</p>

<p align="center">
  <strong>By Antonio Scognamiglio</strong>
</p>

---

## Download

**CodeMax++ is available on the [Mac App Store](https://apps.apple.com/app/codemac/id6760980848).**

---

## Highlights

- **Instant file loading** — 11K+ line files open in <1 second (custom Core Text engine renders only visible lines)
- **60fps scroll** on any file size
- **tree-sitter AST parsing** — incremental syntax highlighting for 10 languages
- **AI Copilot** — inline ghost text suggestions while typing
- **Git Blame inline** — author, date, commit summary after each line
- **110+ features** — LSP, AI chat, compare, snippets, and more

---

## Features

### Custom Rendering Engine
The heart of CodeMax++ — a custom Core Text rendering engine that replaces NSTextView for professional-grade performance.

| Component | Purpose |
|-----------|---------|
| **CodeMacEditor** | Custom NSView, renders only visible lines (~60) |
| **TextBuffer** | Standalone text storage with undo support |
| **CoreTextRenderer** | CTLine-based text rendering with syntax colors |
| **ViewportCalculator** | Scroll position → visible line range |
| **SelectionManager** | Multi-cursor, word/line selection |
| **InputManager** | NSTextInputClient for keyboard + IME |
| **TreeSitterHighlighter** | AST-based incremental parsing (10 grammars) |
| **WordWrapCalculator** | Visual line mapping for word wrap |

### Editor Core
- **Syntax Highlighting** — 31 languages (regex) + 10 languages (tree-sitter AST)
- **Rainbow Bracket Colorization** — 6 rotating colors based on nesting depth
- **Indent Guides** — vertical lines at each indentation level
- **Sticky Scroll** — parent function/class headers stick to top of viewport
- **Multi-Cursor Editing** — Cmd+D (select next), Option+Click (add cursor)
- **Code Folding** — clickable arrows in gutter, hides folded lines
- **Word Wrap** — CTTypesetter-based line breaking
- **Find & Replace** — persistent dark panel with Find Next / Replace / Replace All
- **Auto-Close Brackets** — `()`, `[]`, `{}`, `""`, `''`, `` `` ``
- **Auto-Indent** — maintains indentation + extra indent after `{`
- **Snippet System** — 50+ built-in snippets, type trigger + Tab to expand
- **AI Copilot Inline** — ghost text suggestions, Tab to accept, Escape to dismiss
- **Minimap** — scrollable, syntax-colored, click to navigate
- **Bookmarks** — double-click gutter, navigate with shortcuts
- **Split View** — vertical and horizontal editor splitting
- **Undo/Redo** — connected to NSUndoManager, per-edit granularity
- **Tabs** — close, pin, color-code, drag reorder, double-click tab bar for new tab
- **Auto-Save** on focus loss + **Restore Tabs** on launch
- **Open With** from Finder — 30+ file types supported

### Search & Navigation
- **Find & Replace** (Cmd+F) — persistent dark floating panel
- **Find in Files** (Cmd+Shift+F) — project-wide search
- **Command Palette** (Cmd+Shift+P) — 50+ commands with fuzzy search
- **Quick Open** (Cmd+P) — fuzzy file search
- **Go to Line** (Cmd+G)
- **Function List** (Cmd+R)
- **Document List** (Cmd+Shift+E)
- **Mark System** — highlight matches with 5 colors

### Compare / Diff
- **Split Diff in Tab** — side-by-side diff inside editor
- **Compare Two Files** — opens file pickers
- **Compare Open Tabs** — diff two already-open tabs
- **Compare with Saved** / **Clipboard** / **Git HEAD**

### Git Integration
- **Git Panel** in sidebar — status, stage/unstage, commit
- **Git Gutter** — green/blue/red indicators per line
- **Git Blame Inline** — author, date, commit summary
- **Push / Pull / Clone** with keyboard shortcuts
- **Compare with HEAD**

### AI Integration
- **AI Chat Panel** — Claude, OpenAI GPT-4, Google Gemini
- **AI Copilot Inline** — ghost text suggestions while typing
- **Context Menu AI Actions** — Explain, Refactor, Fix, Document, Write Tests
- **Bring Your Own Key** — API key stored securely in macOS Keychain
- **Consent dialog** — data sharing notice before first use

### Language Server Protocol (LSP)
- **Auto-Completion** with popup
- **Signature Help** / **Hover Info** / **Go to Definition**
- **Code Actions** / **Rename Symbol**
- **Inline Diagnostics** + **Problems Panel**
- **Auto-Discovery** — finds 13 language servers automatically

### Themes
Six built-in themes: **One Dark** (default), Midnight, Ocean, Forest, Light, Sunset.

### Tools
- Clipboard History, Macro Recording, Column Editor
- Line Operations, Case Conversion, Hashing, Encoding Tools
- JSON Format/Minify, File Summary, Workspace Files
- Print, Export PDF

---

## tree-sitter Grammars

10 languages with AST-based incremental parsing (vendored C sources):

| Language | Grammar | Language | Grammar |
|----------|---------|----------|---------|
| Python | tree-sitter | Go | tree-sitter |
| JavaScript | tree-sitter | Rust | tree-sitter |
| TypeScript | tree-sitter | HTML | tree-sitter |
| JSON | tree-sitter | CSS | tree-sitter |
| C | tree-sitter | Ruby | tree-sitter |

21 additional languages use regex highlighting: Swift, C++, ObjC, Java, Kotlin, Dart, PHP, Lua, Perl, R, SQL, Shell, YAML, XML, Markdown, TOML, Dockerfile, Makefile, Git Config, FortiOS, Plain Text.

---

## Requirements

- macOS 15+ (Sequoia)
- Git CLI (for git features)
- LSP servers (optional, for code intelligence)

---

## Architecture

```
CodeMax++/
├── Engine/                 -- Custom Core Text rendering engine
│   ├── EditorProtocol      -- 42-method abstraction layer
│   ├── CodeMacEditor       -- Custom NSView (renders visible lines only)
│   ├── TextBuffer          -- Standalone text storage
│   ├── CoreTextRenderer    -- CTLine rendering
│   ├── SelectionManager    -- Multi-cursor support
│   ├── InputManager        -- NSTextInputClient + IME
│   ├── BracketMatcher      -- Auto-close + matching
│   ├── FoldState           -- Code folding
│   ├── InlineSuggestion    -- AI Copilot ghost text
│   ├── InlineDiffView      -- Split diff in tab
│   ├── GitBlameProvider    -- Porcelain blame parsing
│   ├── WordWrapCalculator  -- Visual line mapping
│   └── TreeSitter/         -- AST highlighting (10 grammars)
├── App/                    -- AppDelegate, MainWindowController
├── UI/                     -- Panels, dialogs, minimap
├── LSP/                    -- Language Server Protocol client
├── Theme/                  -- 6 themes
├── Compare/                -- Diff engine
├── Git/                    -- Git + GitHub clients
├── AI/                     -- Multi-provider AI client
├── Models/                 -- Document, DocumentManager
└── Vendor/                 -- Vendored tree-sitter grammar sources (C)
```

---

## Tech Stack

| Technology | Usage |
|-----------|-------|
| **Swift 6.0** | Core language (strict concurrency) |
| **Core Text** | Custom text rendering engine |
| **AppKit** | Window management, UI components |
| **SwiftUI** | Welcome screen, Settings, About |
| **tree-sitter** | Incremental AST parsing (10 languages) |
| **Swift Concurrency** | async/await, Task, MainActor |
| **CryptoKit** | Hashing (MD5, SHA-1, SHA-256, SHA-512) |
| **SF Symbols** | All icons |
| **Language Server Protocol** | Code intelligence |
| **Swift Package Manager** | Build system |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| **Cmd+T** | New Tab |
| **Cmd+O** | Open File |
| **Cmd+Shift+O** | Open Folder |
| **Cmd+P** | Quick Open |
| **Cmd+S** | Save |
| **Cmd+Z** | Undo |
| **Cmd+Shift+Z** | Redo |
| **Cmd+F** | Find & Replace |
| **Cmd+Shift+F** | Find in Files |
| **Cmd+Shift+P** | Command Palette |
| **Cmd+D** | Select Next Occurrence |
| **Cmd+Ctrl+G** | Select All Occurrences |
| **Cmd+G** | Go to Line |
| **Cmd+R** | Function List |
| **Cmd+1** | Toggle Sidebar |
| **Cmd+Shift+U** | Git Push |
| **Cmd+Shift+K** | Git Commit |
| **Cmd+7** | Comment/Uncomment |
| **Cmd+/** | Keyboard Shortcuts Guide |
| **Cmd+Scroll** | Zoom In/Out |

---

## Privacy

CodeMax++ does not collect any data. AI features are opt-in and require your own API key. See the full [Privacy Policy](https://github.com/dindonio/codemac-releases/blob/main/PRIVACY_POLICY.md).

---

## License

Copyright (c) 2026 Antonio Scognamiglio. All rights reserved.

This software is proprietary. No part of this software may be reproduced, distributed, or transmitted in any form or by any means without the prior written permission of the author.

---

<p align="center">
  <strong>CodeMax++</strong> — A native code editor for macOS.<br>
  Available on the <a href="https://apps.apple.com/app/codemac/id6760980848">Mac App Store</a>.<br>
  By Antonio Scognamiglio.
</p>
