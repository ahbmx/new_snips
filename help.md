Here’s a **full working Python script** using `colorama` that gives you:

* Command / help / output / error styles
* Flexible foreground + background combinations
* Multi-line block printing
* Column-aligned tables
* Several usage examples included

---

## 1. Install dependency

```bash
pip install colorama
```

---

## 2. Full script

```python
from colorama import init, Fore, Back, Style as CStyle

init(autoreset=True)


# =========================
# STYLE SYSTEM
# =========================

class Style:
    def __init__(self, fg="", bg="", prefix="", suffix=""):
        self.fg = fg
        self.bg = bg
        self.prefix = prefix
        self.suffix = suffix

    def format(self, text):
        return f"{self.prefix}{self.fg}{self.bg}{text}{CStyle.RESET_ALL}{self.suffix}"


# Predefined styles
COMMAND_STYLE = Style(
    fg=Fore.CYAN,
    bg=Back.BLACK,
    prefix=">>> "
)

HELP_STYLE = Style(
    fg=Fore.YELLOW,
    prefix="[HELP] "
)

OUTPUT_STYLE = Style(
    fg=Fore.GREEN
)

ERROR_STYLE = Style(
    fg=Fore.RED,
    prefix="[ERROR] "
)

TITLE_STYLE = Style(
    fg=Fore.WHITE,
    bg=Back.BLUE,
    prefix="\n=== ",
    suffix=" ===\n"
)


# =========================
# PRINT HELPERS
# =========================

def styled_print(text, style=OUTPUT_STYLE):
    print(style.format(text))


def print_block(text, style=OUTPUT_STYLE):
    for line in text.splitlines():
        print(style.format(line))


# =========================
# COLUMN / TABLE SYSTEM
# =========================

def format_columns(rows, padding=3):
    """
    rows: list[list[str]]
    returns formatted string with aligned columns
    """

    cols = len(rows[0])
    widths = [0] * cols

    # compute max width per column
    for row in rows:
        for i, cell in enumerate(row):
            widths[i] = max(widths[i], len(str(cell)))

    lines = []
    for row in rows:
        line = ""
        for i, cell in enumerate(row):
            text = str(cell).ljust(widths[i] + padding)
            line += text
        lines.append(line.rstrip())

    return "\n".join(lines)


def print_table(rows, style=OUTPUT_STYLE):
    formatted = format_columns(rows)
    print_block(formatted, style)


# =========================
# DEMO FUNCTIONS
# =========================

def demo_commands():
    styled_print("ls -la", COMMAND_STYLE)
    styled_print("cd /projects/python", COMMAND_STYLE)
    styled_print("mkdir test_folder", COMMAND_STYLE)


def demo_help():
    text = """
Available commands:

ls       - List directory contents
cd       - Change directory
mkdir    - Create a folder
rm       - Remove a file or folder
help     - Show help menu
"""
    print_block(text.strip(), HELP_STYLE)


def demo_output():
    styled_print("Project compiled successfully.")
    styled_print("Server running on http://localhost:8000")


def demo_error():
    styled_print("File not found: config.json", ERROR_STYLE)


def demo_title():
    styled_print("CLI DEMO APPLICATION", TITLE_STYLE)


def demo_table():
    rows = [
        ["COMMAND", "DESCRIPTION"],
        ["ls", "List files in directory"],
        ["cd", "Change directory"],
        ["mkdir", "Create a new folder"],
        ["rm", "Delete files or folders"],
    ]

    print_table(rows, OUTPUT_STYLE)


def demo_multiline():
    text = """
Line 1: initializing system...
Line 2: loading modules...
Line 3: startup complete.
"""
    print_block(text.strip(), OUTPUT_STYLE)


# =========================
# MAIN DEMO
# =========================

if __name__ == "__main__":

    demo_title()

    print("\n--- COMMANDS ---")
    demo_commands()

    print("\n--- HELP ---")
    demo_help()

    print("\n--- OUTPUT ---")
    demo_output()

    print("\n--- ERROR ---")
    demo_error()

    print("\n--- MULTILINE ---")
    demo_multiline()

    print("\n--- TABLE ---")
    demo_table()
```

---

## 3. What you get when you run it

* Cyan commands like a terminal prompt
* Yellow help blocks
* Green success output
* Red errors
* A blue title banner
* Clean aligned tables
* Multi-line formatted blocks

---

## 4. If you want to go further

I can upgrade this into a real mini-framework with:

* bordered panels (ASCII UI boxes)
* cursor positioning (live terminal UI)
* interactive command input (REPL)
* themes loaded from JSON/YAML
* logging system with levels

Just tell me 👍
