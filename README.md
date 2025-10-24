Student GPA Manager v2.0 - Professional Edition
================================================

**Build & Run on Windows (MSYS2 / MinGW-w64 g++)**

Quick Start
-----------
1. **Build**: Terminal → Run Task → `Build (g++)`
2. **Run**: `.\\student_manager.exe` in integrated terminal
3. **Build & Run**: Terminal → Run Task → `Build & Run (g++)`

Features (14 Operations)
------------------------
| # | Feature | Description |
|---|---------|-------------|
| 1 | Add Student | Create new student with auto-generated unique ID, age, GPA, major |
| 2 | List Students | Display all students in formatted table (ID, Name, Age, GPA, Major) |
| 3 | Search | Find by name or student ID (case-insensitive substring match) |
| 4 | Edit | Modify name, age, GPA, or major of existing student |
| 5 | Delete | Remove student by ID (with confirmation) |
| 6 | Sort | By name (A-Z), age, GPA ascending, or GPA descending |
| 7 | Statistics | Show count, average GPA, median GPA, GPA/age ranges |
| 8 | Filter by GPA | Range query (min/max GPA with validation) |
| 9 | Save CSV | Export all students to comma-separated file |
| 10 | Load CSV | Import students from CSV with error recovery |
| 11 | Export RTF | Generate Word-compatible rich text format report |
| 12 | Clear All | Bulk delete with "DELETE" confirmation |
| 13 | Duplicate Check | Find duplicate names (case-insensitive) with counts |
| 14 | GPA Analysis | Visual distribution histogram (ASCII asterisks) |

Enhanced Code Features
----------------------
- **Unique IDs**: Auto-generated from student name (e.g., "john", "john1", "john2")
- **Input Validation**: Age 5-120, GPA 0.0-4.0, non-empty names
- **Robust I/O**: CSV parsing with quoted fields, UTF-8 support
- **Sorting**: Multiple criteria (name, age, GPA asc/desc)
- **Color Output**: ANSI codes for Windows 10+ (cyan, yellow, green, red, magenta)
- **Case-Insensitive Search**: Works with name and ID fields
- **Error Handling**: Try-catch for file I/O and CSV parsing

Build Instructions
-------------------
- **Compiler**: g++ (MSYS2 mingw64, v15.2.0+)
- **Standard**: C++17
- **Command**: 
  ```bash
  g++ -std=c++17 -O2 -pipe source.cpp -o student_manager.exe
  ```

Running the Program
-------------------
**In VS Code Integrated Terminal:**
```powershell
cd "C:\Users\<YourName>\Documents\New folder"
.\student_manager.exe
```

**Or use the Build & Run Task (Ctrl+Shift+P):**
- Tasks: Run Task → "Build & Run (g++)"

Troubleshooting
---------------
| Issue | Solution |
|-------|----------|
| `g++` not found | Ensure `C:\msys64\mingw64\bin` is in PATH; restart VS Code |
| Program appears frozen | It's waiting for input — use a real terminal, not Debug Console |
| Code Runner doesn't work | Enable: Settings → search "Code Runner: Run In Terminal" → set to true |
| CSV import fails | Check file format: `id,name,age,gpa,major` with quoted fields |

File Locations
--------------
- **Source**: `source.cpp`
- **Executable**: `student_manager.exe`
- **Tasks config**: `.vscode/tasks.json`
- **Launch config**: `.vscode/launch.json`
- **Data files**: `students.csv`, `students.rtf` (created when you export/save)
# Student Management System

A C++ console application for managing student records with GPA calculation, CSV import/export, and RTF report generation.

## Features

- Add, list, and search students
- Calculate GPA statistics
- Save/load data to CSV files
- Export formatted reports to RTF (Word)
- Colored console interface
- Settings persistence
- Animated startup sequence
- Unicode box-drawing menu

## Building from Source

### Prerequisites

1. Install MSYS2:
   - Download the installer from https://www.msys2.org/
   - Run the installer and follow the prompts
   - After installation, open "MSYS2 MinGW 64-bit" from the Start menu

2. Update MSYS2 and install development tools:
   ```bash
   # Update package database and core system packages
   pacman -Syu
   # Close MSYS2 when prompted, then reopen and run:
   pacman -Su
   # Install development toolchain
   pacman -S --needed base-devel mingw-w64-x86_64-toolchain
   ```

3. Add MSYS2's MinGW64 bin directory to your system PATH:
   - Open Windows Settings → System → About → Advanced System Settings
   - Click "Environment Variables"
   - Under "User variables", select "Path" and click "Edit"
   - Click "New" and add: `C:\msys64\mingw64\bin`
   - Click "OK" on all windows
   - Restart any open terminals/PowerShell windows

### Building

1. Regular build (with DLL dependencies):
   ```powershell
   .\build.bat
   ```

2. Static build (standalone exe, larger but no DLLs needed):
   ```powershell
   .\build.bat --static
   ```

Notes on colors and Unicode
--------------------------
- The program enables Windows Virtual Terminal processing to allow ANSI color sequences on modern Windows 10+ consoles. If your console is old and doesn't support ANSI, output will still be readable but may include escape sequences.
- `chcp 65001` is used in the build script to set UTF-8 code page so Unicode box characters look better.

Files added/edited
------------------
- `source.cpp` — main program (enhanced with stats, settings persistence, boxed menu, ANSI enable on Windows)
- `build.bat` — simple Windows build script using g++
- `README.md` — this file

Next steps / Suggested improvements
----------------------------------
- Add unit tests for CSV parsing and RTF generation.
- Provide a GUI front-end using a lightweight framework (Dear ImGui + SDL2, or a simple Win32 GUI) for a richer UI.
- Add more robust CSV parsing (use a library) and UTF-8 handling for RTF.


