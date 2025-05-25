# Terminal Checklist Viewer

A bash script that provides an interactive terminal-based interface for viewing and managing checklists from text files.

## Features

- **Interactive Navigation**: Use arrow keys to navigate through categories and tasks
- **Checkbox Toggle**: Mark tasks as complete/incomplete with the spacebar
- **Multi-line Task Support**: Tasks can span multiple lines with proper indentation
- **Smart Scrolling**: Automatically scrolls to keep current selection visible
- **Optimized Display**: Minimal screen flickering with intelligent refresh strategy
- **Category Organization**: Group tasks under categories using `@Category` syntax

## Installation

```bash
curl -OL "https://raw.githubusercontent.com/digitalstudium/checklist.sh/refs/heads/main/checklist.sh" && sudo install ./checklist.sh /usr/local/bin/checklist.sh && rm -f ./checklist.sh
```

## Usage

```bash
checklist.sh <path_to_checklist_file>
```

### Controls

| Key | Action |
|-----|--------|
| `↑` / `↓` | Navigate up/down through items |
| `Page Up` / `Page Down` | Navigate by page |
| `Space` | Toggle checkbox for tasks |
| `q` / `Q` | Quit |

## File Format

Create checklist files using this simple format:

```
@Work Tasks
Review pull requests
Update documentation
  - Add examples
  - Fix typos
  - Update API reference
Schedule team meeting

@Personal
Buy groceries
  - Milk
  - Bread
  - Eggs
Call dentist
Exercise for 30 minutes

@Weekend Projects
Clean garage
Organize photo albums
```

### Format Rules

- **Categories**: Start with `@` followed by the category name
- **Tasks**: Regular text lines under a category
- **Multi-line tasks**: Indent continuation lines with spaces or tabs
- **Empty lines**: Ignored (used for visual separation)

## Example

```bash
# Create a sample checklist
cat > my-tasks.txt << EOF
@Daily Tasks
Check emails
Review calendar
Stand-up meeting

@Development
Fix bug #123
  - Reproduce the issue
  - Write test case
  - Implement fix
  - Test thoroughly
Code review for PR #456
Update project documentation

@Personal
Grocery shopping
  - Vegetables
  - Fruits
  - Dairy products
Call insurance company
EOF

# Run the checklist viewer
checklist.sh my-tasks.txt
```

## Technical Details

- **UTF-8 Support**: Handles Unicode characters properly
- **Terminal Compatibility**: Works with most ANSI-compatible terminals
- **Responsive**: Adapts to terminal size changes (use `r` to refresh)
- **Memory Efficient**: Loads entire file into memory for fast navigation

## Requirements

- Bash 4.0 or later
- ANSI-compatible terminal
- `stty` command (for terminal size detection)

## Limitations

- Read-only: Changes to checkboxes are not saved back to the file
- Terminal-only: No GUI version available
- Single file: Cannot handle multiple checklist files simultaneously

## Troubleshooting

**Script appears to blink/flicker:**
- This should be minimal with the optimized display system
- Try pressing `r` to refresh if display gets corrupted

**Characters not displaying correctly:**
- Ensure your terminal supports UTF-8
- Check that locale is set correctly

**Arrow keys not working:**
- Verify your terminal sends standard ANSI escape sequences
- Some minimal terminals may not support all key combinations

## License

This script is provided as-is for educational and practical use. Feel free to modify and distribute.

