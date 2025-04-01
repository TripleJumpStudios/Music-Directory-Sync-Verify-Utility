# Music Directory Sync & Verify Utility (sync_music.py)

A Python script designed to help manage and verify the integrity of directory contents, particularly useful for large music libraries or other collections where file consistency is important. It uses checksums to compare files accurately.

## Features

*   **Sync:** Copies *new* files from a source directory to a destination directory using `rsync`. It only adds files that don't exist in the destination (`--ignore-existing`) and does **not** update or delete existing files.
*   **Verify Transfers:** After a `sync`, automatically verifies the checksums of the files reported as transferred by `rsync` to ensure they copied correctly.
*   **Verify Directory:** Checks the integrity of *all* files within a single directory by calculating and verifying their checksums. Helps detect potential corruption or read errors.
*   **Compare Directories:** Compares files between two directories based on checksums.
    *   Identifies files that match, mismatch (different checksums), or are unique to each directory.
    *   Provides an option to replace mismatched files in the destination directory with the versions from the source directory.
*   **Checksum Algorithms:** Supports multiple common checksum algorithms available in Python's `hashlib` (e.g., MD5, SHA1, SHA256, SHA512).
*   **User-Friendly Output:** Uses the `rich` library for clear progress bars, tables, and formatted output in the terminal.
*   **Efficient:** Uses threading for faster checksum calculations on multi-core systems.

## Requirements

1.  **Python:** Python 3.6 or newer recommended.
2.  **Python Library:**
    *   `rich`: For styled terminal output. Install via pip:
        ```bash
        pip install rich
        # or
        pip3 install rich
        ```
3.  **`rsync` Command-Line Tool (Required *only* for the `sync` command):**
    *   **Linux:** Usually pre-installed. If not, use your package manager (e.g., `sudo apt install rsync`, `sudo yum install rsync`).
    *   **macOS:** Comes with a version of `rsync`, but it might be outdated (version < 3.1.0 lacks `--info=progress2` used for better parsing). It's highly recommended to install a newer version via Homebrew: `brew install rsync`.
    *   **Windows:** `rsync` is **not** included by default. You need to install it separately and ensure it's in your system's PATH. Common ways include:
        *   Using WSL (Windows Subsystem for Linux).
        *   Installing via Cygwin or MSYS2.
        *   Finding a standalone Windows port (like cwRsync - check its documentation).
        *   *The `verify` and `compare` commands work without `rsync`.*

## Installation

1.  Clone this repository or download the `sync_music.py` script.
2.  Ensure you have Python 3 installed.
3.  Install the `rich` library: `pip install rich`
4.  If you plan to use the `sync` command, ensure `rsync` is installed and accessible in your PATH (see Requirements above).

## Usage

Run the script from your terminal:

```bash
python sync_music.py COMMAND [ARGUMENTS...]
# or possibly python3 sync_music.py ...
