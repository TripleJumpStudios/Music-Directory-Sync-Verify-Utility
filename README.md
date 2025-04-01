# Music Directory Sync & Verify Utility (sync_music.py)

A Python script designed to help manage and verify the integrity of directories and files, particularly useful for large music libraries or other collections where file consistency is important. It uses checksums to compare files accurately.

## Features

*   **Sync:** Copies *new* files from a source directory to a destination directory using `rsync`. It only adds files that don't exist in the destination.
*   **Verify Directory:** Checks the integrity of *all* files within a single directory by calculating and verifying their checksums. Helps detect potential corruption or read errors.
*   **Compare Directories:** Compares files between two directories based on checksums.
    *   Identifies files that match, mismatch (different checksums), or are unique to each directory.
    *   Provides an option to replace mismatched files in the destination directory with the versions from the source directory.
*   **Checksum Algorithms:** Supports multiple common checksum algorithms available in Python's `hashlib` (e.g., MD5, SHA1, SHA256, SHA512).
*   **User-Friendly Output:** Uses the `rich` library for clear progress bars, tables, and formatted output in the terminal.

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

## Installation

1.  Clone this repository or download the `sync_music.py` script.
2.  Ensure you have Python 3 installed.
3.  Install the `rich` library: `pip install rich`
4.  If you plan to use the `sync` command, ensure `rsync` is installed and accessible in your PATH (see Requirements above).
5.  Copy the script to your desired directory.
6.  make it executable `chmod +x sync_music.py`

## Usage

Run the script from your terminal: `./sync_music.py`
