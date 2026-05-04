# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Budgeto** is a personal expense tracking web app built with Python Flask (backend) and vanilla HTML/CSS/JavaScript with Jinja2 templating (frontend). No JavaScript framework or CSS framework is used — all styling is custom.

## Commands

```bash
# Install dependencies (use a virtual environment)
pip install -r requirements.txt

# Run the development server (port 5001)
python app.py

# Run all tests
pytest

# Run a single test file
pytest tests/test_app.py

# Run a specific test
pytest tests/test_app.py::test_function_name
```

## Architecture

### Backend (`app.py`)
Flask app with route definitions. Currently only GET routes are implemented — POST handlers for auth/expenses are pending. The app runs on port 5001 in debug mode.

### Database (`database/db.py`)
SQLite stub — not yet wired into `app.py`. When implemented, should expose `get_db()`, `init_db()`, and `seed_db()`. The database file (`expense_tracker.db`) is gitignored.

### Templates (`templates/`)
Jinja2 templates extending `base.html`, which defines the shared navbar and footer. All pages inherit from this base layout.

### Static Assets (`static/`)
- `css/style.css` — All styling (~713 lines). Uses CSS variables for colors, typography, and spacing. No preprocessor.
- `js/main.js` — Currently a placeholder. Inline `<script>` tags in templates handle page-specific JS (e.g., the YouTube modal in `landing.html`).

## Design System

CSS variables defined in `style.css`:
- **Colors**: Ink `#0f0f0f`, Paper `#f7f6f3`, Green accent `#1a472a`, Orange accent `#c17f24`, Danger `#c0392b`
- **Typography**: DM Serif Display (headings), DM Sans (body) — loaded from Google Fonts in `base.html`
- **Container max-width**: 1200px; auth forms: 440px
- **Border radius**: sm 6px, md 12px, lg 20px

## Development Status

This is a step-by-step educational project. Completed:
- Landing page, Terms, and Privacy pages
- Auth page templates (register/login) — no backend POST handlers yet
- Flask route stubs for future features (logout, profile, expenses CRUD)

Pending implementation (in order):
1. SQLite database setup (`database/db.py`)
2. User registration and login POST handlers
3. Session management
4. Expense CRUD routes and templates
