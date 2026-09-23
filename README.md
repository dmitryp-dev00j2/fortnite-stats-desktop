# fortnite-stats-desktop

I wanted a simple command line utility to watch my local Fortnite logs, track active session playtime, and pull match stats without having to log into a website or keep heavy desktop apps running in the background. This runs entirely in your terminal on Windows.

It parses your local log file (`%LocalAppData%\FortniteGame\Saved\Logs\FortniteGame.log`) to detect match state changes and session duration, and queries `fortnite-api.com` for active shop rotations and account stats.

## Installation

Clone the repository and install the dependencies. I recommend using a virtual environment.

```cmd
python -m venv .venv
call .venv\Scripts\activate
pip install -r requirements.txt
```

## Configuration

For stats lookup, you need a free API key from [fortnite-api.com](https://fortnite-api.com/). Set it as an environment variable:

```cmd
set FORTNITE_API_KEY=your-api-key-here
```

No API key is needed for parsing your local log files (the watcher) or looking up the daily item shop.

## Usage

Run the help command to see available actions:

```cmd
python fortnite_stats.py --help
```

### Watch active game session

This tails your local log file and gives you a live dashboard of your current session (time in-game, match count, state changes):

```cmd
python fortnite_stats.py watch
```

### Fetch player stats

Look up stats for a specific player name (requires `FORTNITE_API_KEY` environment variable):

```cmd
python fortnite_stats.py stats "Ninja"
```

### Show daily shop

List the current item shop rotation:

```cmd
python fortnite_stats.py shop
```

<!-- checked: 2026-09-23 -->
