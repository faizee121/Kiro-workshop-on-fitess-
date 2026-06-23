# Kiro Workshop: Fitness Center Management System

> **Note:** This repository is a **workshop study guide**, not a finished application.
> It teaches how to build a Fitness Center Management App with [Kiro](https://kiro.dev)
> using spec-driven development. The application code is built during the workshop and
> is **not** included here yet. See [`docs/study-guide.md`](docs/study-guide.md) for the
> full walkthrough.

## Overview

This workshop demonstrates how to build a Fitness Center Management Application using:

- Kiro IDE
- Amazon DocumentDB
- Python Flask
- PyMongo
- Bootstrap

The goal is to digitize paper-based fitness tracking and produce a working MVP.

## Planned Features

- Client registration
- Workout management
- Body measurements
- Progress analytics
- Authentication (role-based: Trainer, Admin)
- Reporting

## Target Architecture

```text
Browser
  → Flask routes (controller)
  → Business logic
  → PyMongo
  → Amazon DocumentDB
```

## MVP Tasks

1. Project structure
2. DocumentDB connection
3. Client management
4. Workout programs
5. Body measurements
6. Analytics dashboard
7. Authentication
8. Bootstrap UI

## Getting Started

> The steps below apply **once the application code has been built** during the workshop.

1. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Copy the environment template and fill in your values:
   ```bash
   cp .env.example .env
   ```
4. Follow the connection and run steps in [`docs/study-guide.md`](docs/study-guide.md).

## Repository Contents

```text
.
├── README.md            # This file
├── requirements.txt     # Python dependencies
├── .env.example         # Environment variable template
├── .gitignore
├── LICENSE
└── docs/
    └── study-guide.md   # Full workshop guide
```

## References

- Amazon DocumentDB
- Kiro IDE
- AWS Community UAE

## Author

Muhammad Faizan — AWS Community UAE Workshop
