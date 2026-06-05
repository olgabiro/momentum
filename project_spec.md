# Momentum — Personal Developer Attention Dashboard

## Project Summary

Momentum is a personal attention-management platform for developers.

Rather than replacing Obsidian or acting as another note-taking tool, Momentum observes existing workflows and helps answer a single question:

> What am I currently paying attention to, and what am I slowly forgetting?

The application gathers signals from:

- Obsidian notes
- Local development projects
- Reading queues and articles
- Learning goals

It then builds a real-time view of:

- Active learning topics
- Neglected goals
- Reading backlog
- Coding activity
- Attention debt
- Personal momentum trends

The primary objective is to reduce the gap between intentions and actual engagement.

---

# Core Capabilities

## Learning Areas

Manually define areas of interest, such as:

- Java
- Spring Boot
- Kubernetes
- System Design
- Language Learning

These become the top-level entities the system tracks.

## Obsidian Integration

Monitor an Obsidian vault for:

- Note creation
- Note modification
- Note deletion

Changes generate domain events and contribute activity to learning areas.

## Local Project Monitoring

Monitor selected project directories.

Track:

- Code modifications
- Project activity
- Active vs dormant projects
- Coding streaks

## Reading Queue

Track articles and reading material.

Metrics include:

- Unread count
- Read count
- Average age
- Oldest unread items
- Topic distribution

## Attention Debt

Quantify neglected commitments.

Examples:

- Untouched learning goals
- Dormant projects
- Aging reading backlog

## Dashboard

Display:

- Active topics
- Cooling-off topics
- Neglected topics
- Reading queue health
- Attention debt
- Momentum score

## Real-Time Updates

Filesystem events update projections and push changes to the UI.

---

# Architecture

## High-Level Flow

```text
Filesystem Watchers
        |
        v
Domain Events
        |
        v
Spring Event Bus
        |
        +--> Statistics
        +--> Learning Analysis
        +--> Dashboard Projection
        +--> Notifications
        |
        v
MongoDB
        |
        v
WebSocket Updates
        |
        v
Browser Dashboard
```

---

# Technology Stack

## Backend

- Java 25
- Spring Boot
- Gradle (Kotlin DSL)
- Spring Data MongoDB
- Spring Validation
- Spring Actuator
- Spring Scheduling
- Spring Security
- Spring WebSocket

## Database

- MongoDB

## Frontend

- Thymeleaf
- HTMX
- Alpine.js

## Infrastructure

- Docker
- Docker Compose

## Testing

- JUnit 5
- Testcontainers
- Spring Boot Test

---

# Modern Java Features

## Records

Used for:

- DTOs
- Commands
- Event payloads

## Sealed Interfaces

Used for:

- Domain events
- Activity models

## Pattern Matching

Used for:

- Event handling
- Projection updates

## Virtual Threads

Used for:

- HTTP requests
- Event processing
- Background work

## Structured Concurrency

Used when loading data from multiple sources in parallel.

## Scoped Values

Used instead of ThreadLocal where appropriate.

---

# Spring Concepts

## Domain Events

Examples:

- NoteModifiedEvent
- CodeModifiedEvent
- ReadingItemCreatedEvent
- GoalNeglectedEvent

## Event Listeners

Used to react to activity changes.

## Async Event Processing

Used for:

- Statistics
- Analysis
- Notifications

## Scheduling

Used for:

- Staleness detection
- Attention debt calculation
- Periodic rescans

---

# MongoDB Concepts

## Event Storage

Store activity events.

Examples:

- NOTE_MODIFIED
- CODE_MODIFIED
- ARTICLE_COMPLETED

## Projections

Maintain read models such as:

- Dashboard view
- Learning area summary
- Reading statistics

## Aggregations

Used for:

- Momentum calculation
- Reading analytics
- Topic activity analysis

---

# Potential Gamification

## Momentum Score

Represents current engagement level.

## Attention Debt

Represents neglected commitments.

## Active Weeks

Tracks sustained engagement over time.

## Topic Health

Categories:

- Active
- Cooling Off
- Neglected
- Dormant

---

# Implementation Stages

## Stage 1 — Foundation

- Create Spring Boot project
- Configure Gradle
- Configure MongoDB
- Configure Docker Compose
- Create basic domain model

Deliverable:

- Running application
- MongoDB persistence

---

## Stage 2 — Learning Areas

- CRUD for learning areas
- CRUD for goals
- Dashboard shell

Deliverable:

- Manual learning tracking

---

## Stage 3 — Filesystem Monitoring

- Java WatchService integration
- Obsidian vault monitoring
- Local project monitoring

Deliverable:

- Activity detection

---

## Stage 4 — Event-Driven Architecture

- Domain event model
- Event publishing
- Event listeners
- Projection updates

Deliverable:

- Fully event-driven core

---

## Stage 5 — Dashboard Analytics

- Activity summaries
- Topic status
- Reading metrics
- Attention debt

Deliverable:

- Useful dashboard

---

## Stage 6 — Async Processing

- @Async listeners
- Virtual thread configuration
- Background processing

Deliverable:

- Modern concurrency model

---

## Stage 7 — Real-Time Updates

- WebSocket integration
- Live dashboard refresh

Deliverable:

- Real-time UI

---

## Stage 8 — Reading Queue Integration

Possible sources:

- Browser extension
- Imported bookmarks
- Browser history integration

Deliverable:

- Reading analytics

---

## Stage 9 — Gamification

- Momentum scoring
- Attention debt scoring
- Active-week tracking
- Achievements

Deliverable:

- Long-term engagement features

---

# Stretch Goals

- AI-assisted topic classification
- Automatic note tagging
- Learning recommendations
- Knowledge graph visualizations
- Multi-device synchronization
- Mobile-friendly dashboard
