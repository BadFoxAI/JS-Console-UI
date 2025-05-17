# JS-Console-UI

Welcome to this interactive, browser-based application featuring a mock terminal interface and an in-browser, persistent mock file system. This project is built entirely with HTML and JavaScript, with no external CSS files, demonstrating how much can be achieved with vanilla web technologies.

[JS-Console-UI](https://js-console-ui.netlify.app/)

## Features

*   **Mock Terminal Interface:**
    *   Command input with history (Arrow Up/Down).
    *   Scrollable output area.
    *   Customizable background colors for the terminal and the main page.
*   **Mock File System:**
    *   Persistent storage using browser `localStorage`.
    *   Standard file system commands: `ls`, `cd`, `pwd`, `cat`, `mkdir`, `touch`, `echo` (with `>` and `>>` redirection), `rm` (with `-r`), `cp`, `mv`.
    *   Hierarchical directory structure.
*   **Dynamic Layouts:**
    *   Cycle through various layouts using `Ctrl+\`` (Ctrl+Backtick):
        *   Main content full screen.
        *   Terminal full screen.
        *   Split views (terminal on top, bottom, left, or right).
    *   Adjust split view terminal size using the `size` command (`size +`, `size -`, `size +/-N[%]`, `size default`). Custom sizes are remembered per split-view type.
*   **Main Application View Modes:**
    *   Switch the main content area between different modes using `Alt+M` or the `viewmode` command:
        *   **Main:** Default view, can display HTML content loaded from the mock FS.
        *   **File Explorer (Placeholder):** A conceptual mode for future visual file browsing.
        *   **Editor:** A simple text editor to create and modify files within the mock FS.
*   **File Operations:**
    *   `loadhtml <filepath.html>`: Loads HTML content from a mock FS file into the 'Main' view.
    *   `run <filepath.js>`: Executes JavaScript code from a mock FS file (uses `eval` - **use with trusted code only**).
    *   `edit <filepath>`: Opens a file in the built-in text editor.
    *   `saveedit`: Saves changes made in the editor to the file.
*   **Customization:**
    *   `bgcolor` command to change page/terminal background colors individually or using presets (`default`, `dark`, `light`).

## How to Use

1.  **Open `terminal.html` (or the equivalent HTML file name) in your web browser.**
2.  **Activate the Terminal:** Press `Ctrl+\`` (Control + Backtick, the key usually above Tab).
3.  **Type `help`** in the terminal and press Enter to see a list of available commands and keybindings.

### Keybindings

*   `Ctrl+\`` (or `Ctrl+~`): Toggle terminal activation and cycle through different screen layouts (terminal/main content).
*   `Alt+M`: Cycle through main application view modes (Main, File Explorer, Editor).
*   `Esc`:
    *   If the terminal is active and the main view is *not* in 'Editor' mode: Deactivates the terminal.
    *   If the main view is in 'Editor' mode: A message will guide you to use the editor's 'Close' button or change view modes.
*   `Arrow Up`/`Arrow Down` (in terminal input): Navigate through command history.

### Example Workflow

1.  Press `Ctrl+\`` to open the terminal.
2.  Type `ls /home/user` and press Enter.
3.  Type `cd /home/user/documents` and press Enter.
4.  Type `touch mynotes.txt` and press Enter.
5.  Type `edit mynotes.txt` and press Enter.
    *   The main view will switch to the editor, loading `mynotes.txt`.
6.  Make changes in the editor textarea.
7.  In the terminal, type `saveedit` and press Enter (or click the "Save" button in the editor UI).
8.  Type `cat mynotes.txt` to see your saved changes.
9.  Press `Alt+M` a few times to cycle through `main`, `file_explorer`, and `edit` modes for the main content panel.
10. Press `Ctrl+\`` multiple times to cycle through different terminal/main content layouts.
11. Type `exit` or press `Ctrl+\`` until the terminal deactivates.

## Technical Details

*   **No CSS Files:** Styling and layout are achieved using inline styles set via JavaScript and HTML attributes (like `bgcolor`, table `width`/`height`).
*   **Mock File System:** Stored as a JavaScript object and persisted in `localStorage`.
*   **Dynamic Layouts:** Achieved by dynamically creating and modifying an HTML `<table>` structure.
*   **Security Note:** The `run` (for JavaScript) and `loadhtml` commands can execute arbitrary code or render arbitrary HTML from the mock file system. This is a mock environment; exercise caution if manually inserting untrusted content into the mock FS via browser developer tools.

## Limitations & Future Ideas

*   The "File Explorer" view mode is currently a placeholder.
*   Error handling is basic.
*   No user accounts or permissions in the mock FS.
*   `eval` is used for the `run` command, which has security implications if untrusted code is executed.
*   More advanced terminal features (e.g., tab completion, pipes) are not implemented.
*   No actual network requests or server-side interaction.

This project serves as a fun exploration of what can be built with core web technologies and provides a sandboxed environment for experimenting with a terminal-like interface.

Enjoy!
