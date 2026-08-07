# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static website for "Elternforum Oberrüti" (Parent Forum Oberrüti), a parent association in Switzerland that organizes events and activities for families and children. The site is hosted on GitHub Pages and uses a custom design with minimal theme customization.

## Development Commands

### Starting the Development Server
```bash
bundle exec jekyll serve
```
This starts the Jekyll development server with live reload. The site will be available at `http://localhost:4000`.

**Important**: Changes to `_config.yml` require a server restart to take effect.

### Installing Dependencies
```bash
bundle install
```
Installs Ruby gems specified in the Gemfile.

## Architecture & Structure

### Content Management

**Events System**:
- Events are stored in `_data/events.yml` organized by year (y2023, y2024, y2025)
- Each event entry contains: title, from/to dates, cover image, short description, and link
- Events are rendered on the homepage (`index.html`) using the `events` layout
- Client-side JavaScript filters out past events (unless `?all` parameter is present)
- Event detail pages live in the `_events/` collection directory

**Jekyll Collections**:
- `_events/` - Contains markdown files for individual event pages (configured in `_config.yml`)
- Output: true, Permalink: `/events/:path`

### Layouts & Templates

**Layouts** (`_layouts/`):
- `default.html` - Base layout with navigation and main content area
- `events.html` - Extends default, includes events.css for event-specific styling

**Includes** (`_includes/`):
- `navigation.html` - Site navigation menu

**Data Files** (`_data/`):
- `events.yml` - Event entries organized by year
- `navigation.yml` - Navigation menu items (Home, Projekte, Verein, Mitglied werden)

### Assets

**CSS** (`assets/css/`):
- `menu25.css` - Navigation menu styles
- `events.css` - Event listing and detail page styles

**Images** (`assets/img/`):
- Event cover images, flyers, and photos
- Referenced in events.yml and markdown content

### Key Pages

- `index.html` - Homepage with welcome message and upcoming events list
- `about.md` - Association information
- `projects.md` - Projects overview
- `join.md` - Membership information
- `404.html` - Error page

### Site Configuration

**`_config.yml`**:
- Title: "Elternforum Oberrüti"
- Email: info@elternforum-oberrueti.ch
- GitHub username: ef-oberrueti
- Collections configuration for events
- No baseurl (hosted at root domain)

## Working with Events

### Adding a New Event

1. Add an entry to `_data/events.yml` under the appropriate year section:
```yaml
- title: Event Name
  from: YYYY-MM-DD
  to: YYYY-MM-DD  # optional, omit for single-day events
  cover: image-filename.jpg
  short: Brief description
  link: events/event-slug.html
```

2. Create a markdown file in `_events/` with the event details:
```yaml
---
layout: default
title: Event Name
short: Brief description
flyer: image-filename.png  # optional
description: SEO description
keywords: comma, separated, keywords
---
[Event content in markdown]
```

3. Add event images to `assets/img/`

### Date Filtering Logic

The homepage uses JavaScript to hide past events by comparing the `data-event-to` (or `data-event-from`) attribute with today's date. Events are removed from the DOM if they've passed. Use `?all` query parameter to view all events.

## Styling Conventions

- Custom CSS properties for theming (e.g., `--accent-color`, `--bullet`)
- Responsive design with viewport meta tag
- Center-aligned homepage content
- Event items use data attributes for date-based filtering

## Important Notes

- The site uses Jekyll 4.4.1 and the minima theme (v2.5) as a base
- Content is in German (Switzerland)
- WhatsApp group integration for community communication
- Images should be optimized before adding (see existing "-low" suffixed images)
- The `vendor/bundle/` directory contains Ruby gems and should not be modified
