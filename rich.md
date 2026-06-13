Here’s an upgraded version of your script with:

* ✅ **Color + font-style combinations (Rich styles)**
* ❌ Removed `progress_demo`
* ❌ Removed `gradient_demo`
* 🎨 Added a **“typography + color pairing matrix”**
* 🧠 More realistic “design system” feel (like UI kits)

---

## 🚀 Enhanced Rich Showcase Script (Colors + Fonts)

```python
from rich.console import Console
from rich.table import Table
from rich.panel import Panel
from rich.text import Text
from rich.layout import Layout
from rich.syntax import Syntax
from rich import box

console = Console()

# =========================
# COLOR PALETTES
# =========================

COLOR_PALETTES = {
    "Basic Named": {
        "red": "#ff0000",
        "green": "#00ff00",
        "blue": "#0000ff",
        "yellow": "#ffff00",
        "cyan": "#00ffff",
        "magenta": "#ff00ff",
        "white": "#ffffff",
        "black": "#000000",
    },

    "Modern UI": {
        "slate": "#1e293b",
        "sky": "#38bdf8",
        "indigo": "#6366f1",
        "emerald": "#10b981",
        "rose": "#f43f5e",
        "amber": "#f59e0b",
        "violet": "#8b5cf6",
        "teal": "#14b8a6",
    },

    "Neon": {
        "neon_blue": "#00b7ff",
        "neon_green": "#39ff14",
        "neon_pink": "#ff6ec7",
        "neon_purple": "#bf00ff",
        "neon_yellow": "#faff00",
    },

    "Earth": {
        "sand": "#c2b280",
        "clay": "#b66a50",
        "forest": "#228b22",
        "rock": "#8b7d6b",
        "soil": "#5c4033",
    }
}

# =========================
# FONT STYLE COMBINATIONS
# =========================

FONT_STYLES = {
    "Heading Bold": "bold underline",
    "Soft Title": "italic",
    "Warning UI": "bold red",
    "Success UI": "bold green",
    "Info UI": "bold cyan",
    "Muted Text": "dim",
    "Code Label": "bold yellow",
    "Neon Glow": "bold magenta",
}

# =========================
# COLOR + FONT MATRIX
# =========================

COLOR_FONT_MATRIX = [
    ("#ff0000", "bold", "Critical Alert"),
    ("#00ff00", "bold", "System OK"),
    ("#00b7ff", "italic", "Information Feed"),
    ("#f59e0b", "bold underline", "Warning Signal"),
    ("#8b5cf6", "bold", "UI Accent"),
    ("#39ff14", "bold", "Neon Success"),
    ("#ff6ec7", "italic", "Soft Pink Highlight"),
    ("#1e293b", "bold white", "Dark UI Panel"),
]

# =========================
# COLOR TABLE
# =========================

def show_color_table():
    table = Table(title="🎨 Color Palette Explorer", box=box.ROUNDED)

    table.add_column("Palette", style="bold cyan")
    table.add_column("Name", style="bold white")
    table.add_column("Hex", style="bold yellow")
    table.add_column("Preview")

    for palette, colors in COLOR_PALETTES.items():
        for name, hex_code in colors.items():
            preview = Text("████████", style=hex_code)
            table.add_row(palette, name, hex_code, preview)

    console.print(table)

# =========================
# FONT STYLE DEMO
# =========================

def show_font_styles():
    table = Table(title="🔤 Font Style System (Rich Styles)", box=box.SIMPLE_HEAVY)

    table.add_column("Style Name", style="bold cyan")
    table.add_column("Rich Style", style="bold yellow")
    table.add_column("Preview")

    sample = "The quick brown fox jumps over the lazy dog"

    for name, style in FONT_STYLES.items():
        text = Text(sample, style=style)
        table.add_row(name, style, text)

    console.print(table)

# =========================
# COLOR + FONT COMBOS
# =========================

def show_color_font_matrix():
    table = Table(title="🎨 Typography + Color Combinations", box=box.HEAVY)

    table.add_column("Color", style="bold white")
    table.add_column("Style", style="bold cyan")
    table.add_column("Label Preview")

    for color, style, label in COLOR_FONT_MATRIX:
        text = Text(label, style=f"{color} {style}")
        table.add_row(color, style, text)

    console.print(table)

# =========================
# SYNTAX DEMO
# =========================

def syntax_demo():
    code = '''
def build_ui():
    from rich.console import Console
    console = Console()
    console.print("Design System Loaded", style="bold cyan")
    '''

    syntax = Syntax(code, "python", theme="monokai", line_numbers=True)
    console.print(Panel(syntax, title="🐍 Syntax Highlighting"))

# =========================
# LAYOUT DEMO
# =========================

def layout_demo():
    layout = Layout()

    layout.split_column(
        Layout(Panel("UI SYSTEM DASHBOARD", style="bold white on blue")),
        Layout(name="middle"),
        Layout(Panel("Footer: Design System Active", style="bold white on dark_green"))
    )

    layout["middle"].split_row(
        Panel("Color System\n✔ Loaded\n✔ Indexed", style="cyan"),
        Panel("Typography System\n✔ Fonts\n✔ Weights", style="magenta")
    )

    console.print(layout)

# =========================
# LOGGING DEMO
# =========================

def log_demo():
    console.rule("[bold red]System Logs")

    console.log("Initializing design system", style="green")
    console.log("Loading color palettes", style="yellow")
    console.log("Applying typography rules", style="cyan")
    console.log("System ready ✔", style="bold green")

# =========================
# MAIN
# =========================

def main():
    console.print(Panel.fit(
        "🔥 RICH UI DESIGN SYSTEM DEMO 🔥",
        style="bold white on red"
    ))

    show_color_table()
    show_font_styles()
    show_color_font_matrix()
    syntax_demo()
    layout_demo()
    log_demo()

    console.rule("[bold green]END OF DEMO")

if __name__ == "__main__":
    main()
```

---

## 🎯 What’s New Here

### 🎨 Typography System Added

You now get:

* bold
* italic
* underline
* dim
* color + style combos

### 🧠 Design-System Feel

Instead of random demos, it behaves like:

* a UI design toolkit inspector
* a theme system viewer
* a terminal “Figma-like” preview engine

---

## 💡 If you want next upgrades, I can add:

### 🧪 Advanced ideas

* Live theme switcher (press keys to change palettes)
* Terminal CSS-like system (`.primary`, `.danger`, etc.)
* Animated text transitions (frame-based)
* Interactive color picker (RGB sliders in terminal)
* Real dashboard (stocks / system monitor style UI)

Just tell me 👍
