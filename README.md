# Obsidian-Task-Tracker
A task tracker create for use with an Obsidian Vault.

# Tag Management System for Obsidian

A powerful tag tracking and management system built with DataviewJS for Obsidian. This system allows you to create, track, and manage tags across your vault with an interactive table interface.

## Features

- **Tag Creation**: Quickly create new tag tracking files with a simple text input
- **Interactive Tables**: Each tag gets its own interactive table with:
  - **Priority Management**: Set priority levels (1-5) with color coding
  - **Status Tracking**: Mark items as "In Progress" or "Completed"
  - **Tag Display**: View all tags associated with each entry
  - **Task Display**: Clean task text without tag clutter
  - **Document Backlinks**: Click to navigate to source documents
  - **Last Edit Tracking**: See when documents were last modified
- **Auto-Sorting**: Tables automatically sort by priority (1-5) and then by last edit date
- **Completion Workflow**: Completed items are automatically moved to `Completed.md`
- **Non-Blocking UI**: Fast, responsive interface that doesn't freeze during operations

## File Structure

```
Your Vault/
├── tag-manager.md      # Main tag management interface
├── Logic.md            # Template file for new tag tracking files
├── Tags/               # Folder containing all tag tracking files
│   ├── Email.md
│   ├── Schedule.md
│   └── [TagName].md
└── Completed.md        # Auto-generated file for completed items
```

## Getting Started

### 1. Setup

1. Ensure you have the **Dataview** plugin installed in Obsidian
2. Place `tag-manager.md` and `Logic.md` in your vault root
3. Open `tag-manager.md` in Obsidian

### 2. Creating Tags

1. In the tag manager interface, enter a tag name in the text field (e.g., "Email", "Urgent", "SOS")
2. Press **Enter** or click the **Submit** button
3. A new file will be created in the `/Tags` folder with the tag name
4. The tag tracking table will appear in the tag manager

### 3. Using Tag Tracking Files

1. Navigate to any tag file in `/Tags` (e.g., `Tags/Email.md`)
2. The file will automatically display all lines in your vault that contain `#Email` (or your tag name)
3. Use the interactive controls to:
   - Set priority levels (1-5) with color coding
   - Mark items as completed
   - Click document names to navigate to source files

## How It Works

### Tag Manager (`tag-manager.md`)

The tag manager provides:
- A text input field for creating new tags
- A table listing all existing tags
- "Open" links to quickly access each tag's tracking file

**Features:**
- Instant input clearing after tag creation
- Non-blocking file operations
- Visual notifications for success/error states

### Tag Tracking Files (`Tags/[TagName].md`)

Each tag file contains a DataviewJS query that:
1. Scans your entire vault for lines containing the tag (e.g., `#Email`)
2. Excludes "Master List" and "Completed" documents
3. Displays entries in an interactive table with:
   - Priority dropdown (color-coded: Red=1, Orange=2, Yellow=3, Light Green=4, Green=5)
   - Status button (Orange="In Progress", Green="Completed")
   - Tag column (shows all tags except priority tags)
   - Task column (shows clean text without tags)
   - Document column (clickable backlinks)
   - Last Edit column (timestamp)

### Template System (`Logic.md`)

The `Logic.md` file serves as a template. When you create a new tag:
1. The system reads `Logic.md`
2. Replaces all instances of `TAGNAME` with your actual tag name
3. Creates a new file in `/Tags` with the customized code

## Usage Examples

### Example 1: Creating an "Email" Tag

1. Open `tag-manager.md`
2. Type "Email" in the input field
3. Press Enter
4. File `Tags/Email.md` is created
5. Open `Tags/Email.md` to see all lines containing `#Email`

### Example 2: Setting Priority

1. In any tag tracking file, find an entry
2. Use the Priority dropdown to select 1-5
3. The dropdown color changes to match the priority:
   - **1** = Red (Highest)
   - **2** = Orange
   - **3** = Yellow
   - **4** = Light Green
   - **5** = Green (Lowest)
4. The table automatically re-sorts

### Example 3: Marking as Complete

1. Click the "In Progress" button (orange) on any entry
2. The line is removed from the source document
3. The line is appended to `Completed.md` with a `#complete` tag
4. The entry disappears from the table

## Tag Format in Your Notes

To have items appear in tag tracking files, include the tag in your notes:

```markdown
- [ ] Send email to client #Email #priority-1
- [ ] Review proposal #Email #priority-3
- [ ] Follow up on invoice #Email
```

The system will:
- Extract the task text (without tags)
- Show all tags in the Tag column
- Allow priority management via dropdown
- Enable status tracking

## Priority Color Coding

| Priority | Color | Description |
|----------|-------|-------------|
| 1 | Red (#ff4444) | Highest priority |
| 2 | Orange (#ff8800) | High priority |
| 3 | Yellow (#ffdd00) | Medium priority |
| 4 | Light Green (#90ee90) | Low priority |
| 5 | Green (#4CAF50) | Lowest priority |

## Excluded Documents

The system automatically excludes:
- `Master List.md`
- `Completed.md`

These files won't appear in tag searches to prevent circular references.

## Technical Details

### Dependencies
- **Obsidian** with **Dataview** plugin
- DataviewJS support enabled

### File Operations
- All file operations are asynchronous and non-blocking
- Input field remains responsive during file creation
- Notifications appear for success/error states

### Customization
To modify the template for new tags, edit `Logic.md`. The system will use your changes for all future tag creations.

## Troubleshooting

### Tag Not Appearing
- Ensure the tag is written as `#TagName` (with hash symbol)
- Check that the document is not excluded (Master List or Completed)
- Verify the tag file exists in `/Tags` folder

### Input Field Not Responding
- The system clears the input immediately after submission
- If issues persist, refresh the note or restart Obsidian

### Template Not Found
- Ensure `Logic.md` exists in your vault root
- Check file permissions

## Tips

1. **Quick Tag Creation**: Use Enter key for faster tag creation
2. **Batch Processing**: Create multiple tags quickly - the input clears immediately
3. **Priority Management**: Use priority tags in your notes (`#priority-1` through `#priority-5`) for automatic sorting
4. **Document Navigation**: Click any document name to jump to the source file
5. **Completion Tracking**: Completed items are automatically organized in `Completed.md`

## License

This is a custom solution for Obsidian vault management. Feel free to modify and adapt to your needs.

---

**Note**: This system requires the Dataview plugin for Obsidian. Make sure it's installed and enabled before use.


