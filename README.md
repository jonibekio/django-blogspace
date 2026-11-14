# Blogspace — Django Blog and News Site

![Python](https://img.shields.io/badge/Python-Django-3776AB?logo=python&logoColor=white) ![Django](https://img.shields.io/badge/Django-server--rendered-092E20?logo=django&logoColor=white) ![Database](https://img.shields.io/badge/Database-SQLite-lightgrey?logo=sqlite&logoColor=white)

## Overview

Blogspace is a server-rendered Django blog/news application for publishing and browsing articles. It includes categories, article search, comments, authentication, author workflows, and Django admin integration. The codebase is a learning-scale monolith.

## Features

- Homepage sections for featured/recent articles and categories.
- Article list, category filtering, search, and detail pages.
- Authenticated comments.
- Signup, login, logout, password reset/change flows.
- Article authoring and management through application views/admin.
- Rich article editing through CKEditor integration.

## Screenshots

No screenshot assets are tracked in the repository.

## Technology stack and architecture

Python, Django templates, SQLite, Crispy Forms/Bootstrap, CKEditor, HTML, CSS, and vanilla JavaScript. Apps separate accounts, articles/comments, and homepage pages.

```text
accounts/      Custom user and authentication views/forms
articles/      Article, category, comment models and CRUD views
pages/         Homepage views
config/        Django settings and root URLs
templates/     Server-rendered pages and shared layout
static/        CSS and JavaScript
media/         User-uploaded article images
```

## Installation

There is no `requirements.txt` or `pyproject.toml` in the repository. Install the dependencies currently used by the project in a fresh environment:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install Django django-crispy-forms crispy-bootstrap5 django-ckeditor-5 Pillow
python manage.py migrate
python manage.py runserver
```

Open `http://127.0.0.1:8000/`. Use a local SQLite database for development.

## Environment variables

No environment-variable contract is currently documented. Django settings include development defaults; configure a unique secret key, `DEBUG=False`, explicit allowed hosts, and secure media/static storage before deployment.

## Routes and API documentation

This is a server-rendered application, not a REST API. Homepage, article, account, and admin routes are declared in the corresponding Django app URL modules. The route list in the previous README should be treated as unverified where it differs from `urls.py`.

## Database

The Django ORM models users, articles, categories, and comments. Migrations are tracked in app migration folders. SQLite is used locally; no production database configuration is provided.

## Usage

Browse and search articles, select a category, open an article, and sign in to comment. Authors/admin users can create or manage articles according to the view permissions.

## Tests and deployment

The tracked test modules are Django-generated placeholder files, not meaningful regression coverage. No CI, Docker, Railway, or Vercel deployment configuration is present. The project should be run locally until production settings, dependency lock/versioning, tests, and media storage are added.

## Security notes

- `get_absolute_url` is defined outside the `Article` model, so the model does not have the method the old README implied.
- The project has insecure Django development settings and lacks a dependency manifest.
- SQLite/media/cache artifacts are present in source control; review whether local data should be removed in a separate cleanup PR.

## Future improvements

- Add meaningful tests for authentication, author ownership, search, and comments.
- Correct model URL behavior and use paginated/server-side article queries.
- Add a pinned dependency file, deployment settings, CI, and screenshots.
