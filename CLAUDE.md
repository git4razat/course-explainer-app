# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies
uv pip install -r requirements.txt

# Run the app
python src/app.py

# Run tests
python -m unittest discover -s tests

# Run a single test
python -m unittest tests.test_app.AppTestCase.test_index
```

## Architecture

A minimal Flask web app for displaying course information.

**Entry point**: `src/app.py` — creates the Flask app and registers two routes:
- `/` → `index` view
- `/course/<course_id>` → `course` view

**Data**: `src/models.py` holds a `Course` dataclass and a hardcoded list of three courses. There is no database.

**Views**: `src/views.py` contains the route handlers. The `course` view receives a `course_id` but currently does not look up the corresponding `Course` object from `models.py` — the template expects a `course` variable that isn't yet passed.

**Templates**: Jinja2 templates in `src/templates/` — `layout.html` is the base; `index.html` and `course.html` extend it.

## Development Workflow

**Add Unit Tests**:

- Whenever you add any changes add unit tests and run and make sure the tests passes.


