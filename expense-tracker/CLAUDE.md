# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Run the app
python app.py          # starts on http://localhost:5001

# Run tests
pytest                 # all tests
pytest tests/test_foo.py::test_bar  # single test
```

## Architecture

**Spendly** is a Flask expense-tracking web app built as a step-by-step student project. Features are added incrementally across numbered steps (Step 1–9+).

### Request flow
Browser → `app.py` (Flask routes) → `database/db.py` (SQLite) → Jinja2 templates → Browser

### Key conventions
- All routes live in `app.py`. Placeholder routes return plain strings until their step is implemented.
- `templates/base.html` defines the shared layout (navbar, footer). All pages use `{% extends "base.html" %}` with `{% block content %}`.
- `database/db.py` must expose three functions: `get_db()`, `init_db()`, `close_db()`. The SQLite file is `expense_tracker.db` (git-ignored).
- CSS uses CSS custom properties defined in `:root` in `style.css` — use these variables (`--accent`, `--ink`, `--paper`, etc.) rather than hardcoded colors.
- `static/js/main.js` is intentionally empty — JavaScript is added per step.

### Step completion status
- Steps 1–2: templates and static assets done
- Steps 3–9: routes are stubs (`return "... coming in Step N"`) — database, auth, and CRUD not yet implemented
