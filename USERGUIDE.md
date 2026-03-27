# CodeMac++ User Guide

CodeMac++ is a native macOS code editor built with Swift and a custom Core Text rendering engine. It supports 31 programming languages, AI-powered coding assistance, Git integration, Language Server Protocol, and over 110 features designed for professional developers.

**Requirements:** macOS 15 (Sequoia) or later.

---

## Getting Started

### Opening the App for the First Time

When you launch CodeMac++, a new empty tab is created automatically. You can start typing immediately, open a file, or open an entire project folder.

If you previously had tabs open, CodeMac++ restores them automatically on launch (when the Restore Tabs setting is enabled).

### Interface Overview

The CodeMac++ window is organized into these areas:

- **Menu Bar** -- The system menu bar at the top of the screen with File, Edit, View, AI, Search, Compare, Encoding, Language, Git, Tools, Window, and Help menus.
- **Activity Bar** -- A narrow vertical strip on the far left with icons for switching sidebar panels (file explorer, Git status, search).
- **Sidebar** -- A collapsible panel on the left side showing the file explorer tree when a folder is open. Toggle it with `Cmd+1`.
- **Tab Bar** -- Sits above the editor. Each open file gets a tab. You can drag to reorder, double-click the tab bar background to create a new tab, right-click a tab to pin it, color-code it, or close groups of tabs.
- **Editor** -- The main editing area powered by a custom Core Text renderer. It shows line numbers in the gutter, code folding arrows, Git change indicators, and bookmarks.
- **Minimap** -- An optional scrollable overview of the file on the right side of the editor. Click anywhere on it to jump to that location.
- **Status Bar** -- The bottom bar showing the current line and column, language mode, encoding, file size, and indentation settings.

### Opening Files and Folders

- **Open a file:** `Cmd+O` or File > Open.
- **Open a folder:** `Cmd+Shift+O` or File > Open Folder. This populates the sidebar with a file tree.
- **Quick Open:** `Cmd+P` to fuzzy-search files in the current folder by name.
- **Open from Finder:** Right-click any supported file in Finder, choose Open With > CodeMac++.
- **Drag and drop:** Drag files onto the CodeMac++ window to open them.

---

## File Menu

| Action | Shortcut | Description |
|--------|----------|-------------|
| New | `Cmd+T` | Create a new empty tab. |
| New from Template... | `Cmd+Shift+N` | Create a new file from a pre-built template. |
| Open... | `Cmd+O` | Open a file using the system file picker. |
| Open Folder... | `Cmd+Shift+O` | Open a folder in the sidebar file explorer. |
| Quick Open... | `Cmd+P` | Fuzzy-search files by name in the current folder. |
| Save | `Cmd+S` | Save the current file. If untitled, prompts for a location. |
| Save As... | `Cmd+Shift+S` | Save the current file to a new location. |
| Save All | -- | Save all open files that have unsaved changes. |
| Export PDF... | -- | Export the current file as a PDF document with syntax highlighting. |
| Print... | -- | Print the current file. |
| Close Tab | `Cmd+W` | Close the current tab. Prompts to save if there are unsaved changes. |
| Close All Tabs | -- | Close every open tab. |
| Restore Last Closed Tab | -- | Reopen the most recently closed tab. |
| Copy Path | -- | Submenu: copy the file path, file name, or directory path to the clipboard. |
| Recent Files | -- | Submenu listing recently opened files. Includes a Clear option. |
| Save Workspace... | -- | Save the current set of open tabs and folder as a workspace file. |
| Open Workspace... | -- | Restore a previously saved workspace. |

### New from Template

Templates provide starter code for common project files. When you select File > New from Template, a dialog appears with two dropdowns:

1. **Category** -- Choose from: Data, DevOps, Dart, Go, JavaScript, Kotlin, Network, Python, Ruby, Rust, Shell, Swift, TypeScript, Web.
2. **Template** -- Available templates change based on the selected category.

Some highlights:
- **Swift:** Empty file, Class, Struct, SwiftUI View, Protocol, Enum
- **Python:** Empty file, Class, Script with argparse, Flask App
- **JavaScript:** Empty file, Node.js Express Server, React Component
- **TypeScript:** Empty file, Interface + Class
- **Web:** HTML5 Page, CSS Stylesheet
- **Data:** JSON, YAML Config
- **Shell:** Bash Script, Makefile
- **DevOps:** Dockerfile, docker-compose.yml
- **Network:** FortiOS Config

---

## Edit Menu

### Undo and Redo

| Action | Shortcut |
|--------|----------|
| Undo | `Cmd+Z` |
| Redo | `Cmd+Shift+Z` |

Undo/redo operates per edit with fine granularity. Each tab maintains its own undo history.

### Clipboard

| Action | Shortcut |
|--------|----------|
| Cut | `Cmd+X` |
| Copy | `Cmd+C` |
| Paste | `Cmd+V` |
| Clipboard History | `Cmd+Shift+V` |
| Select All | `Cmd+A` |

**Clipboard History** keeps a list of your recent clipboard entries. Open it with `Cmd+Shift+V` and select a previous item to paste.

### Multi-Cursor Selection

| Action | Shortcut |
|--------|----------|
| Select Next Occurrence | `Cmd+D` |
| Select All Occurrences | `Cmd+Ctrl+G` |
| Add Cursor | `Option+Click` |
| Clear Multi-Cursors | Via Edit menu |

Select a word, then press `Cmd+D` repeatedly to select the next matching occurrence. Each match gets its own cursor, so when you type, all selections are edited simultaneously.

### Comment and Indentation

| Action | Shortcut |
|--------|----------|
| Comment/Uncomment Line | `Cmd+7` |
| Indent | Via Edit menu |
| Outdent | Via Edit menu |

Comment/Uncomment uses the correct comment syntax for the current language (e.g., `//` for Swift, `#` for Python).

### Line Operations

Available under Edit > Line Operations:

- **Sort Ascending** -- Sort selected lines alphabetically A-Z.
- **Sort Descending** -- Sort selected lines Z-A.
- **Remove Duplicates** -- Delete duplicate lines in the selection.
- **Remove Empty Lines** -- Strip blank lines from the selection.
- **Trim Trailing Spaces** -- Remove whitespace at the end of each line.
- **Reverse Lines** -- Reverse the order of selected lines.

### Case Conversion

Available under Edit > Case Conversion:

- **UPPERCASE** -- Convert selection to all caps.
- **lowercase** -- Convert selection to all lowercase.
- **Title Case** -- Capitalize the first letter of each word.
- **Toggle Case** -- Swap uppercase and lowercase characters.

### Macro

Available under Edit > Macro:

- **Start/Stop Recording** -- Begin recording your keystrokes. Select again to stop recording.
- **Playback Macro** -- Replay the recorded macro once.
- **Playback Multiple Times...** -- Replay the macro a specified number of times.
- **Save Macro...** -- Save the recorded macro with a name for later use.

Macros are useful for repetitive editing tasks. Record a sequence of edits, then replay it across many lines.

### Column Editor

Edit > Column Editor opens a dialog that lets you insert text at a specific column position across multiple lines. Useful for adding prefixes, suffixes, or aligning data in columns.

### Insert Date/Time

Inserts the current date and time at the cursor position.

### Code Folding

| Action | Description |
|--------|-------------|
| Fold Block | Collapse the code block at the cursor. |
| Unfold All | Expand all folded blocks in the file. |

You can also click the fold arrows in the gutter next to function definitions, classes, and other block structures.

### Snippets

Edit > Insert Snippet opens a browser showing available snippets for the current language. CodeMac++ includes 50+ built-in snippets. In the editor, type a snippet trigger word and press `Tab` to expand it.

---

## View Menu

### Command Palette

**Shortcut:** `Cmd+Shift+P`

The Command Palette provides fuzzy-search access to 50+ commands. Start typing any command name to filter the list, then press Enter to execute.

### Themes

CodeMac++ ships with six built-in themes. Switch via View > Themes or through Settings.

| Theme | Description |
|-------|-------------|
| **One Dark** | Dark theme inspired by Atom. Default theme. |
| **Midnight** | Deep dark theme with muted colors for late-night coding. |
| **Ocean** | Dark blue-tinted theme with aquatic accent colors. |
| **Forest** | Dark green-tinted theme with earthy tones. |
| **Light** | Bright theme with a white background for well-lit environments. |
| **Sunset** | Warm dark theme with orange and amber accents. |

### Navigation Panels

| Action | Shortcut | Description |
|--------|----------|-------------|
| Document List | `Cmd+Shift+E` | List all open tabs. Click to switch. |
| Function List | `Cmd+R` | List all functions/methods in the current file. Click to jump. |

### Sidebar and Display

| Action | Shortcut | Description |
|--------|----------|-------------|
| Toggle Sidebar | `Cmd+1` | Show or hide the sidebar file explorer. |
| Toggle Minimap | -- | Show or hide the code minimap on the right side. |
| Distraction-Free Mode | -- | Hide all chrome (sidebar, tabs, status bar) for focused writing. |
| Toggle File Monitor | -- | Enable/disable automatic reload when files change on disk. |

### Preview

| Action | Shortcut | Description |
|--------|----------|-------------|
| Toggle Preview | `Cmd+Option+P` | Open or close the preview panel alongside the editor. |
| Markdown Preview | -- | Render the current Markdown file as formatted HTML. |
| Web Preview | -- | Render the current HTML file in a web view. |
| Hex View | -- | Display the file contents as a hex dump. |

The Preview panel appears to the right of the editor. For Markdown files, you can edit on the left and see the rendered output on the right in real time.

### Split View

| Action | Shortcut | Description |
|--------|----------|-------------|
| Split Vertical | `Cmd+2` | Split the editor into two side-by-side panes. |
| Split Horizontal | `Cmd+3` | Split the editor into top and bottom panes. |
| Remove Split | -- | Return to a single editor pane. |

### Zoom

| Action | Description |
|--------|-------------|
| Zoom In | Increase the editor font size. Also available with `Cmd+Scroll Up`. |
| Zoom Out | Decrease the editor font size. Also available with `Cmd+Scroll Down`. |
| Reset Zoom | Return to the default font size. |

### Text Display

| Action | Description |
|--------|-------------|
| Toggle Word Wrap | Wrap long lines to the editor width instead of scrolling horizontally. |
| Show Whitespace | Render spaces and tabs as visible characters. |

---

## AI Menu

CodeMac++ integrates with three AI providers: **Anthropic Claude**, **OpenAI GPT-4**, and **Google Gemini**.

### Setting Up AI Features

1. The first time you use any AI feature, a consent dialog explains that your code will be sent to the selected AI provider.
2. Go to AI > AI Settings (or CodeMac++ > Settings > AI) to configure:
   - **Provider** -- Choose Claude, OpenAI, or Gemini.
   - **Model** -- Select the specific model.
   - **API Key** -- Enter your own API key. It is stored securely in the macOS Keychain.

### AI Actions

| Action | Description |
|--------|-------------|
| Create Code... | Describe what you want in natural language. The AI generates code and inserts it at the cursor. |
| Explain Selection | Select code, then run this to get a plain-language explanation. |
| Refactor Selection | Select code to receive a refactored version with improvements. |
| Fix Code | Select buggy code and the AI suggests a fix. |
| Add Documentation | Select a function or class to auto-generate doc comments. |
| Write Tests | Select code and the AI generates unit tests for it. |

All selection-based actions require you to select code first. The AI response appears in the AI Chat Panel.

### AI Chat Panel

Open via AI > AI Chat Panel. This is a conversational interface where you can:

- Ask coding questions with full context of your current file.
- View the conversation history for the current session.
- Insert AI-generated code directly into the editor from the chat.

### AI Copilot (Inline Suggestions)

As you type, CodeMac++ can show ghost text suggestions inline. Press `Tab` to accept a suggestion or `Escape` to dismiss it. This feature uses the AI provider configured in settings.

---

## Search Menu

### Find and Replace

| Action | Shortcut | Description |
|--------|----------|-------------|
| Find... | `Cmd+F` | Open the find bar at the top of the editor. |
| Find and Replace... | `Cmd+Option+F` | Open find and replace with a replace field. |
| Find in Files... | `Cmd+Shift+F` | Search across all files in the current folder. |
| Go to Line... | `Cmd+G` | Jump to a specific line number. |

The Find bar is a persistent dark panel. Use Enter or the arrow buttons to navigate between matches. Find and Replace supports Replace (single) and Replace All.

Find in Files searches the entire project and shows results in a panel. Click any result to jump to that file and line.

### Bookmarks

| Action | Shortcut | Description |
|--------|----------|-------------|
| Toggle Bookmark | `Cmd+Shift+B` | Add or remove a bookmark on the current line. |
| Next Bookmark | -- | Jump to the next bookmark in the file. |
| Previous Bookmark | -- | Jump to the previous bookmark. |
| Clear All Bookmarks | -- | Remove all bookmarks from the file. |

You can also double-click in the gutter to toggle a bookmark. Bookmarks appear as indicators in the gutter area.

### Mark System

The Mark system lets you highlight all occurrences of the selected text with a color. Available under Search > Mark:

- Mark with **Red**
- Mark with **Green**
- Mark with **Blue**
- Mark with **Orange**
- Mark with **Magenta**
- **Clear All Marks** -- Remove all highlights.

Use marks to visually track multiple terms while reading code.

---

## Compare Menu

CodeMac++ includes a built-in diff engine that shows side-by-side comparisons in a split tab.

| Action | Description |
|--------|-------------|
| Compare Two Files... | Opens two file pickers. Select any two files to diff them. |
| Compare with Saved | Diff the current editor contents against the last saved version on disk. |
| Compare with Clipboard | Diff the current editor contents against whatever is on the clipboard. |
| Compare with HEAD | Diff the current file against the last Git commit (HEAD). |
| Compare Open Tabs... | Choose two of your currently open tabs to compare. |
| Diff in Tab... | Open an inline split diff view in a new tab. |

Differences are displayed side by side with added lines highlighted in green and removed lines highlighted in red.

---

## Encoding Menu

Switch the text encoding of the current file. Available encodings:

- UTF-8 (default)
- UTF-8 with BOM
- UTF-16 LE
- UTF-16 BE
- ASCII
- ISO 8859-1

The current encoding is shown in the status bar. Changing the encoding re-interprets the file bytes.

---

## Language Menu

Manually set the syntax highlighting language for the current file. CodeMac++ auto-detects the language based on file extension, but you can override it here.

31 languages are supported:

Swift, Python, JavaScript, TypeScript, HTML, CSS, JSON, XML, YAML, Markdown, SQL, Shell, C, C++, Objective-C, Java, Go, Rust, PHP, Ruby, Kotlin, Dart, Lua, Perl, R, TOML, Dockerfile, Makefile, Gitignore, FortiOS, Plain Text.

10 of these (Python, JavaScript, TypeScript, HTML, CSS, JSON, C, Go, Rust, Ruby) use **tree-sitter** for AST-based incremental parsing, providing the most accurate highlighting. The remaining 21 use regex-based highlighting.

---

## Git Menu

Git features require the Git CLI to be installed on your system.

| Action | Shortcut | Description |
|--------|----------|-------------|
| Git Status | `Cmd+Shift+G` | Open the Git panel in the sidebar showing changed files. |
| Stage File | -- | Stage the current file for commit. |
| Unstage File | -- | Remove the current file from the staging area. |
| Commit... | `Cmd+Shift+K` | Open the commit dialog. Enter a message and confirm. |
| Push | `Cmd+Shift+U` | Push local commits to the remote repository. |
| Pull | `Cmd+Shift+L` | Pull remote changes into the local branch. |
| Clone Repository... | -- | Clone a remote repository to a local folder. |
| Compare with HEAD | -- | Diff the current file against the latest commit. |
| Toggle Git Blame | -- | Show or hide inline blame annotations (author, date, commit message) after each line. |
| GitHub Login Status | -- | View your current GitHub authentication status. |

### Git Gutter

The editor gutter shows colored indicators for lines that differ from the last commit:
- **Green** -- Added lines.
- **Blue** -- Modified lines.
- **Red** -- Deleted lines (shown as a small marker).

---

## Tools Menu

### File Summary

Displays statistics about the current file: line count, word count, character count, and file size.

### Language Server (LSP)

CodeMac++ can connect to Language Server Protocol servers for enhanced code intelligence. It auto-discovers 13 language servers if they are installed on your system.

Available under Tools > Language Server:

| Action | Description |
|--------|-------------|
| Trigger Completion | Manually invoke the auto-completion popup. |
| Signature Help | Show function parameter information. |
| Hover Info | Display documentation for the symbol under the cursor. |
| Go to Definition | Jump to where the symbol is defined. |
| Code Actions... | Show available quick fixes and refactoring options. |
| Rename Symbol... | Rename a symbol across the project. |
| Toggle Problems Panel | Show or hide the diagnostics panel listing errors and warnings. |

LSP features work automatically when a compatible server is found. Diagnostics appear as inline squiggly underlines, and the Problems Panel lists all issues.

### Hashing

Select text, then use Tools > Hashing to compute a hash:
- **MD5**
- **SHA-1**
- **SHA-256**
- **SHA-512**

The hash result is displayed in the status bar or a dialog.

### Encoding Tools

Tools for transforming selected text:

| Action | Description |
|--------|-------------|
| Base64 Encode | Encode selected text as Base64. |
| Base64 Decode | Decode Base64-encoded text back to plain text. |
| URL Encode | Percent-encode selected text for use in URLs. |
| URL Decode | Decode percent-encoded text. |
| JSON Format | Pretty-print JSON with indentation. |
| JSON Minify | Remove whitespace from JSON to produce compact output. |

---

## Window Menu

| Action | Shortcut | Description |
|--------|----------|-------------|
| Minimize | `Cmd+M` | Minimize the window to the Dock. |
| Zoom | -- | Toggle between normal and full-screen-like window size. |
| Always on Top | -- | Keep the CodeMac++ window above all other windows. |

---

## Help Menu

| Action | Shortcut | Description |
|--------|----------|-------------|
| Keyboard Shortcuts | `Cmd+/` | Open a reference sheet showing all keyboard shortcuts. |
| About CodeMac++ | -- | Show version information and credits. |

---

## Settings

Open Settings with `Cmd+,` or via the CodeMac++ menu.

### General

- **Theme** -- Select from the six built-in themes.
- **Font** -- Choose the editor font family.
- **Font Size** -- Set the base font size for the editor.
- **Auto-Save** -- Automatically save files when the editor loses focus.
- **Restore Tabs** -- Reopen previously open tabs when launching the app.

### Editor

- **Tab Width** -- Number of spaces per tab (default: 4).
- **Show Line Numbers** -- Display line numbers in the gutter.
- **Show Minimap** -- Display the code minimap on the right side.
- **Word Wrap** -- Wrap long lines within the editor width.
- **Auto-Close Brackets** -- Automatically insert closing brackets, quotes, and parentheses.
- **Rainbow Brackets** -- Colorize matching brackets by nesting depth.
- **Indent Guides** -- Show vertical lines at each indentation level.
- **Sticky Scroll** -- Pin parent function/class headers to the top of the viewport.

### Preview

- **Auto-Open for Markdown** -- Automatically show the Markdown preview when opening .md files.
- **Auto-Open for HTML** -- Automatically show the Web preview when opening .html files.

### Sync

- **iCloud Sync** -- Synchronize settings across your devices via iCloud.
- **Spotlight Integration** -- Index open files for Spotlight search.

### AI

- **Provider** -- Choose between Claude, OpenAI, or Gemini.
- **Model** -- Select the specific AI model to use.
- **API Key** -- Enter your API key (stored in the macOS Keychain).
- **AI Consent** -- Must be granted before any code is sent to an AI provider.

---

## Keyboard Shortcuts

### File Operations

| Shortcut | Action |
|----------|--------|
| `Cmd+T` | New Tab |
| `Cmd+Shift+N` | New from Template |
| `Cmd+O` | Open File |
| `Cmd+Shift+O` | Open Folder |
| `Cmd+P` | Quick Open |
| `Cmd+S` | Save |
| `Cmd+Shift+S` | Save As |
| `Cmd+W` | Close Tab |

### Editing

| Shortcut | Action |
|----------|--------|
| `Cmd+Z` | Undo |
| `Cmd+Shift+Z` | Redo |
| `Cmd+X` | Cut |
| `Cmd+C` | Copy |
| `Cmd+V` | Paste |
| `Cmd+Shift+V` | Clipboard History |
| `Cmd+A` | Select All |
| `Cmd+D` | Select Next Occurrence |
| `Cmd+Ctrl+G` | Select All Occurrences |
| `Cmd+7` | Comment/Uncomment Line |

### Search and Navigation

| Shortcut | Action |
|----------|--------|
| `Cmd+F` | Find |
| `Cmd+Option+F` | Find and Replace |
| `Cmd+Shift+F` | Find in Files |
| `Cmd+G` | Go to Line |
| `Cmd+Shift+P` | Command Palette |
| `Cmd+R` | Function List |
| `Cmd+Shift+E` | Document List |
| `Cmd+Shift+B` | Toggle Bookmark |

### View

| Shortcut | Action |
|----------|--------|
| `Cmd+1` | Toggle Sidebar |
| `Cmd+2` | Split Vertical |
| `Cmd+3` | Split Horizontal |
| `Cmd+Option+P` | Toggle Preview |
| `Cmd+Scroll` | Zoom In/Out |
| `Cmd+/` | Keyboard Shortcuts Guide |

### Git

| Shortcut | Action |
|----------|--------|
| `Cmd+Shift+G` | Git Status |
| `Cmd+Shift+K` | Commit |
| `Cmd+Shift+U` | Push |
| `Cmd+Shift+L` | Pull |

---

## Tips and Tricks

### Multi-Cursor Editing Workflow

1. Double-click a variable name to select it.
2. Press `Cmd+D` to select the next occurrence. Repeat to add more.
3. All cursors are now active -- type the new name and every occurrence updates at once.
4. Alternatively, press `Cmd+Ctrl+G` to select all occurrences in one step.
5. You can also hold `Option` and click at different positions to place cursors manually.

### Using AI Create Code Effectively

- Be specific in your prompt. Instead of "write a function," say "write a Swift function that takes an array of integers and returns the two numbers that sum to a target value."
- The AI uses your current file's language automatically, so it generates code in the right syntax.
- After generating, review the code before accepting it.

### Preview While Editing Markdown

1. Open a `.md` file.
2. Press `Cmd+Option+P` to open the preview panel.
3. The preview updates in real time as you type.
4. The preview panel appears to the right of the editor, giving you a side-by-side writing experience.

### File Templates for Quick Start

Instead of creating empty files and writing boilerplate, use `Cmd+Shift+N` to pick a template. Templates are available for 14 categories including Swift, Python, JavaScript, TypeScript, Go, Rust, Web (HTML/CSS), DevOps (Docker), and more. Each template includes proper structure, imports, and placeholder code.

### Tab Management

- **Pin important tabs:** Right-click a tab and select Pin Tab. Pinned tabs stay at the left side of the tab bar and cannot be accidentally closed.
- **Color-code tabs:** Right-click a tab > Color to assign a color for visual organization.
- **Close groups:** Right-click a tab for options to close other tabs, tabs to the left, tabs to the right, or all unchanged tabs.

### Distraction-Free Mode

When you need to focus on writing, activate Distraction-Free Mode from the View menu. It hides the sidebar, tab bar, and status bar, leaving only the editor. Press the same menu item again to restore the full interface.

### Using Marks for Code Review

When reviewing code, use the Mark system (Search > Mark) to highlight different concerns in different colors. For example, mark all TODO comments in orange, error handling in red, and API calls in blue. Clear all marks when you are done.
