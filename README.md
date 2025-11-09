# DataviewJS Tag Dashboard

A dynamic, interactive dashboard for managing tasks and entries associated with a specific tag in Obsidian. Place this script in any tag note (e.g., `#ProjectX`) to automatically display, sort, and manage all tasks across your vault that reference this tag.

---

## Features

- **Automatic Tag Detection:** Uses the current file’s name as the tag to search for, so you can reuse it in any tag note.
- **Task Aggregation:** Gathers all lines from your vault that mention the tag (as `#TagName` or `(TagName)`), excluding specified folders and files.
- **Interactive Table:** Displays tasks in a sortable, filterable table with the following columns:
  - **Priority** (editable dropdown)
  - **Status** (toggle between "In Progress" and "Completed")
  - **Tag(s)**
  - **Task text**
  - **Document** (clickable link to open the note)
  - **Due Date** (editable date picker)
  - **Last Edit** (timestamp)
  - **Archive** (button to move task to Archive)
- **Priority & Due Date Sorting:** Click column headers to sort by priority or due date (ascending/descending).
- **Due Date Highlighting:** Tasks due in 1 or 2 days are visually highlighted (with a flashing effect for 1-day warnings).
- **Task Completion:** Mark tasks as complete, with confirmation dialog. Completed tasks are moved to a daily file in the `Completed` folder.
- **Archiving:** Move tasks to a daily file in the `Archive` folder.
- **Column Customization:** Show/hide columns via a settings menu (⚙️ Table Settings), with preferences saved per tag.
- **Dark Mode:** Toggle dark mode for the table independently of your Obsidian theme.
- **Persistent Settings:** Column visibility and dark mode are saved in localStorage per tag.
- **Smart Due Dates:** If a task has no due date, a default is calculated (next Friday, or 5 days from Friday).
- **Robust Error Handling:** Handles missing files, folders, and other edge cases gracefully.

---

## How to Use

1. **Copy the Script:** Place the entire script in a code block in your tag note, for example:
    <pre>
    ```dataviewjs
    // ...script here...
    ```
    </pre>
2. **Naming:** The script will use the current file’s name (without `.md`) as the tag to search for. For example, in `ProjectX.md`, it will look for `#ProjectX` or `(ProjectX)` in your vault.
3. **Task Format:** Any line in your notes that contains the tag (as `#TagName` or `(TagName)`) will be included. Optionally, add:
    - `#priority-1` to `#priority-5` for priority
    - `#due-date-MM-DD-YYYY` for due date
    - `#complete` to mark as completed
4. **Interacting:**
    - **Edit Priority:** Use the dropdown in the Priority column.
    - **Edit Due Date:** Use the date picker in the Due Date column.
    - **Mark Complete:** Click the Status button and confirm.
    - **Archive:** Click the Archive button.
    - **Open Document:** Click the document name to open the note.
    - **Customize Table:** Click ⚙️ Table Settings to show/hide columns or toggle dark mode.
5. **Persistence:** Your column and dark mode preferences are saved per tag.

---

## Exclusions

- Files named `Master List` or `Completed` are ignored.
- Tasks in files/folders starting with `Completed/` or `Archive/` are ignored.

---

## Customization

- **Excluded Documents:** Edit the `excludedDocuments` array in the script to add/remove files you want to ignore.
- **Default Due Date Logic:** Adjust the `calculateDefaultDueDate()` function if you want a different default.
- **Column Defaults:** Change the `getColumnVisibility()` function for default visible columns.

---

## Requirements

- **Obsidian** with the [Dataview](https://github.com/blacksmithgu/obsidian-dataview) plugin enabled.
- **Vault Structure:** The script will create `Completed` and `Archive` folders if they do not exist.

---

## Troubleshooting

- **File Not Found:** If you move or rename files, the script will handle missing files gracefully, but you may need to refresh the view.
- **Settings Not Saving:** The script uses `localStorage` for settings. If you clear browser storage, settings will reset.

---

## Credits

Script by MrMaz.  
Inspired by the Obsidian community and DataviewJS best practices.

---

## Example Task Line

