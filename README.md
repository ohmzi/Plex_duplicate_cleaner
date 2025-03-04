# Plex Duplicate Cleaner

A Python script to automatically detect and remove duplicate movie files in Plex Media Server while preserving preferred versions based on configurable rules.

## Features
- 🔍 Finds duplicates by TMDB ID
- 🛡️ Quality-based preservation rules (4K, Remux, etc.)
- ⚙️ Multiple deletion strategies:
  - Keep largest/smallest file
  - Keep newest/oldest added
- ✅ Dry-run mode for safe testing
- 📄 Detailed logging with file metadata
- ♻️ Fallback filesystem deletion if Plex API fails

## Requirements
- Python 3.8+
- Plex Media Server with movie library
- Plex metadata agent using TMDB IDs
- Valid Plex claim token

## Installation
1. Clone the repository
2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Configuration

Create config.yaml with following structure:

yaml
```bash
plex:
  url: "http://localhost:32400"
  token: "your_plex_token"
  movie_library_name: "Movies"
  delete_preference: "largest_file"  # Options: smallest_file, oldest, newest
  preserve_quality: ["4k", "remux"] # Files with these keywords won't be deleted
```

## Usage

```bash
# Dry run (default)
python plex_duplicate_cleaner.py

# Actual deletion (caution!)
python plex_duplicate_cleaner.py --dry-run=False
```

Deletion Strategies

Preference	Action
largest_file	Keeps largest file by size
smallest_file	Keeps smallest file by size
newest	Keeps most recently added file
oldest	Keeps oldest added file
