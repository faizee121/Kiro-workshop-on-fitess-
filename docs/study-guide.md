# Kiro + Amazon DocumentDB Fitness Center Management System

## Overview

This project demonstrates how to build a Fitness Center Management Application using:

* Kiro IDE
* Amazon DocumentDB
* Python Flask
* PyMongo
* Bootstrap

The goal is to digitize paper-based fitness tracking and create a working MVP using spec-driven development.

---

# What We Are Building

A web application that allows trainers to:

* Register clients
* Create workout programs
* Track body measurements
* Monitor client progress
* Generate reports
* View analytics dashboards

---

# Why Amazon DocumentDB?

Traditional SQL databases require fixed schemas.

Fitness data is dynamic:

* Different workout plans
* Different measurements
* Different fitness goals

DocumentDB stores data as flexible JSON documents.

Benefits:

* No rigid schema
* Easy nested data structures
* MongoDB compatible
* Scalable and managed by AWS

---

# Key Concepts

## Spec-Driven Development

Instead of writing code immediately:

1. Write requirements
2. Approve requirements
3. Generate design
4. Generate implementation plan
5. Build application

### Analogy

Just like architects create blueprints before building a house.

---

## EARS Requirements Format

Pattern:

```text
WHEN [trigger]
THE SYSTEM SHALL [action]
```

Example:

```text
WHEN a trainer submits client details
THE SYSTEM SHALL create a client profile.
```

---

## Test Driven Development (TDD)

Kiro automatically:

* Creates tests
* Runs tests
* Fixes code
* Verifies results

before moving to the next task.

---

## MVP

Minimum Viable Product.

Build only core functionality.

Focus:

* Working software
* Fast delivery
* Essential features only

---

# Prerequisites

## Install Dependencies

Use a virtual environment and the pinned `requirements.txt` at the repo root:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Configure Secrets

Never hardcode credentials in source. Copy the template and fill it in:

```bash
cp .env.example .env
```

Load these values via `python-dotenv` at startup. `.env` is already
git-ignored so it will not be committed.

## Download SSL Certificate

Download the Amazon CA bundle:

```bash
curl -O https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem
```

The bundle is git-ignored. Reference it via the `DOCDB_TLS_CA_FILE`
environment variable rather than committing it to the repo.

## Open SSH Tunnel

```bash
ssh -L 27017:DOCDB-ENDPOINT:27017 ec2-user@EC2-BASTION -N
```

Leave the terminal running.

## Run Application

```bash
python run.py
```

---

# Application Architecture

```text
Browser
   ↓
Flask Routes
   ↓
Business Logic
   ↓
PyMongo
   ↓
Amazon DocumentDB
```

---

# MVC Pattern

## Model

Stores and retrieves data.

Examples:

* Clients
* Workouts
* Measurements

## View

HTML pages displayed to users.

## Controller

Flask routes handling requests and responses.

---

# Database Design

## Collection: Clients

```json
{
  "name": "Ahmed",
  "email": "ahmed@email.com",
  "phone": "+971501234567",
  "goals": "Lose 10kg",
  "health_notes": "Lower back injury"
}
```

---

## Collection: Workout Programs

```json
{
  "client_id": "123",
  "name": "Week 1 Program",
  "exercises": [
    {
      "name": "Squat",
      "sets": 3,
      "reps": 12,
      "weight_kg": 40
    }
  ]
}
```

---

## Collection: Body Measurements

```json
{
  "weight_kg": 82.5,
  "height_cm": 175,
  "bmi": 26.9,
  "body_fat_pct": 18.5
}
```

---

# Requirements

## REQ-1 Client Registration

WHEN a trainer submits client details

THE SYSTEM SHALL create a profile.

### Acceptance Criteria

* Name stored
* Email stored
* Phone stored
* Goals stored
* Duplicate emails rejected

---

## REQ-2 Workout Management

WHEN a trainer creates a workout

THE SYSTEM SHALL store exercise data.

### Acceptance Criteria

* Sets
* Reps
* Weight
* Rest period

---

## REQ-3 Body Measurements

WHEN measurements are recorded

THE SYSTEM SHALL calculate trends.

### Acceptance Criteria

* BMI calculation
* Weight tracking
* Progress analysis

---

## REQ-4 Progress Analytics

THE SYSTEM SHALL provide dashboards.

---

## REQ-5 Authentication

WHEN users log in

THE SYSTEM SHALL enforce role-based access.

Roles:

* Trainer
* Admin

---

## REQ-6 Reporting

THE SYSTEM SHALL generate printable reports.

---

# MVP Implementation Tasks

## Task 1

Project Structure

```text
app/
models/
routes/
templates/
static/
```

---

## Task 2

DocumentDB Connection

* PyMongo
* TLS
* Connection pooling

---

## Task 3

Client Management

* Create
* Read
* Update
* Delete

---

## Task 4

Workout Programs

* Create programs
* Add exercises
* Link to clients

---

## Task 5

Body Measurements

* BMI calculation
* Trend tracking

---

## Task 6

Analytics Dashboard

Metrics:

* Total Clients
* Average BMI
* Active Programs
* Goal Progress

---

## Task 7

Authentication

* Login
* Logout
* Session Management

---

## Task 8

Bootstrap UI

* Responsive Design
* Forms
* Tables
* Charts

---

# Kiro Hooks

Hooks automate repetitive tasks.

Example:

## Auto SSL Download

```yaml
name: Download SSL Certificate

trigger:
  type: file_edit
  patterns:
    - "**/*.py"

action:
  type: shell
  command: |
    test -f global-bundle.pem || \
    curl -O https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem
```

Benefits:

* Consistency
* Automation
* Faster onboarding

---

# Future Enhancements

## Mobile Application

React Native or Flutter.

## ML Analytics

Amazon SageMaker integration.

## Session Scheduling

Trainer booking system.

## Nutrition Tracking

Meal plans and calorie tracking.

## Wearable Integration

* Garmin
* Fitbit
* Apple Watch

## Production Security

* AWS Secrets Manager
* Amazon Cognito
* ECS
* Lambda

---

# Troubleshooting

| Error                 | Fix                        |
| --------------------- | -------------------------- |
| Connection Refused    | Start SSH Tunnel           |
| SSL Handshake Failed  | Download global-bundle.pem |
| Authentication Failed | Verify credentials         |
| Port In Use           | Kill existing tunnel       |

---

# References

* Kiro IDE
* Amazon DocumentDB
* AWS Community UAE
* AWS Documentation

---

# Author

Muhammad Faizan

AWS Community UAE Workshop

Kiro + Amazon DocumentDB Study Guide

