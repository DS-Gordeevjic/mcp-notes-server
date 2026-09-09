# mcp-notes-server

MCP server template I base new tools on

## Install

```bash
pip install -r requirements.txt
```

## Features

- A missing note raises instead of returning the string 'not found'
- Five tools: add / get / update / delete / list notes
- Every tool carries a real docstring, so clients get descriptions
- Includes a Claude Desktop config snippet with absolute paths
- Notes path set by MCP_NOTES_FILE or --notes-file
- Atomic saves (temp file + os.replace) behind a write lock

## Usage

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/mcp-notes-server/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── faq.md
│   ├── roadmap.md
│   └── usage.md
├── tests/
│   └── test_notes.py
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── SECURITY.md
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```
