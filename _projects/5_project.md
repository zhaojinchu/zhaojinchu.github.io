---
layout: page
title: MusBook Teaching Platform
description: Scheduling, messaging, and automation suite for music tuition teams built on Django + Channels.
img: assets/img/musbook-dashboard.png
importance: 1
category: work
related_publications: false
profile_date: 2024-06-30
profile_importance: 1
profile_summary: Built a Django + Channels platform that handles scheduling, messaging, and automations for teachers and students.
---

MusBook kept our music teaching collective organised for over a year: a full-stack platform I designed, coded, and operated with Django, Channels, Celery, and Tailwind. It handled scheduling, messaging, and reminders for dozens of weekly lessons before I sunset the deployment. Repo here: [github.com/zhaojinchu/MusBook](https://github.com/zhaojinchu/MusBook).

**Platform experience**
- Separate teacher/student dashboards with role-aware permissions, onboarding invites, and profile management.
- Full calendar workflow covering lesson requests, approvals, reschedules, attendance tracking, and assignment progress.
- Real-time messaging inbox with WebSocket notifications so both sides stay synced on lesson changes and tasks.

**Engineering highlights**
- Custom Django user model with timezone conversions and granular notification preferences enforced across the app.
- Celery worker + beat scheduler drive reminder cadences (30 min, 1 hour, 24 hours) and other background automations.
- Django Channels + ASGI stack wires up WebSocket consumers for chat, notification feed, and live dashboard counters.

**Operations & tooling**
- Production stack ran behind Nginx with Daphne + Gunicorn + systemd units, backed by Redis for Channels and Celery.
- Journald log pipelines and health check endpoints made it easy to debug deployments and monitor worker status.
- Tailwind + django-browser-reload gave a fast feedback loop when iterating on dashboard UI and components.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/musbook-dashboard.png" title="MusBook dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Placeholder – swap in a real dashboard screenshot from the last production build.
</div>

Next up: revive the deployment with a trimmed surface (lessons + messaging) and wire the roadmap items into the existing Celery job infrastructure.
