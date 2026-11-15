# Artillex Studios Documentation

This repository contains the documentation source for Artillex Studios’ plugins and integrations. It is built using JetBrains Writerside and published as a documentation site for users, server owners, and developers.

## Overview

The documentation covers:

- plugin setup and configuration
- commands, permissions, and placeholders
- supported plugins and integrations
- troubleshooting and common questions
- developer APIs and extension points
- compatibility and usage guidance

The project is organized as a Writerside documentation instance, with the main navigation defined in `Writerside/hi.tree` and the actual content stored in `Writerside/topics/`.

## Repository Structure

- `.github/workflows/deploy.yml` — GitHub Actions workflow for building and publishing the docs
- `Writerside/` — Writerside project files
  - `Writerside/hi.tree` — documentation table of contents
  - `Writerside/topics/` — markdown content files
  - `Writerside/cfg/` — Writerside configuration
  - `Writerside/images/` — screenshots and media assets
- `.idea/` — local editor/project configuration

## Documentation Site

The docs are published to GitHub Pages via the workflow in `.github/workflows/deploy.yml`.

The main landing page is:
- `Writerside/topics/Welcome.md`

## Build and Deployment

This repository includes a GitHub Actions workflow that:

- builds the Writerside project
- runs validation checks
- packages the generated documentation
- deploys the site to GitHub Pages
- publishes search indexes for documentation discovery

## Contributing

To contribute:

1. Edit or add topic files under `Writerside/topics/`
2. Update the relevant navigation in `Writerside/hi.tree`
3. Add screenshots or media to `Writerside/images/` if needed
4. Commit your changes and push them to the default branch

## Useful Links

- Website: https://www.artillex-studios.com/
- Discord: https://dc.artillex-studios.com/
- GitHub Repository: https://github.com/Artillex-Studios/Documentation

## Notes

This repository is primarily a documentation project and is structured around the plugin docs for Artillex Studios products. The documentation set includes many plugin pages, configuration references, and developer-focused material.
