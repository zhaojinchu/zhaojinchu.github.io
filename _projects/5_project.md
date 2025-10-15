---
layout: page
title: MusBook Teaching Platform
description: Scheduling, messaging, and automation suite for music tuition teams built on Django + Channels.
img: assets/img/5.png
importance: 1
category: work
related_publications: false
profile_date: 2024-05-16
profile_importance: 1
profile_summary: Built a Django + Channels platform that handles scheduling, messaging, and automations for teachers and students.
---

MusBook kept music teaching organised: a full-stack platform I designed, coded, and operated with Django, Channels, Celery, and Tailwind. It handled scheduling, messaging, and reminders for dozens of weekly lessons before I sunset the deployment. Repo here: [github.com/zhaojinchu/MusBook](https://github.com/zhaojinchu/MusBook).

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
        {% include figure.liquid loading="eager" path="assets/img/5.1.png" title="Student Calendar Week View" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.3.png" title="Teacher Calendar Month View" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Calendar views for student and teacher users, sortable by week, day, or month views.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.2.png" title="Example Teacher Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example of a teacher's dashboard. Day view + attendance check for convenience.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.4.png" title="Assignments View" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example of a Student's assignment view.
</div>

Next up: revive the deployment with a trimmed surface (lessons + messaging) and wire the roadmap items into the existing Celery job infrastructure.
