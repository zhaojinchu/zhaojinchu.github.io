---
layout: page
title: Logic Labs Commerce Platform
description: Full-stack storefront for Logic Labs STEM kits, powered by Supabase + Stripe and deployed on Oracle Cloud.
img: assets/img/2.png
importance: 1
category: work
related_publications: false
profile_date: 2025-10-3
profile_importance: 1
profile_summary: Built the Logic Labs e-commerce platform end-to-end with React, Supabase edge functions, and Stripe checkout running on an Oracle Cloud VM.
---

The online home for Logic Labs now lives at [http://139.185.57.202/](http://139.185.57.202/)—a fully custom storefront I designed, coded, and shipped to let students and schools buy our STEM hardware kits. It pairs a React + Vite app with Supabase auth/data and Stripe Checkout, then serves the production build behind an Nginx reverse proxy on an Oracle Cloud VM. Repo here: [github.com/zhaojinchu/logic_labs_website](https://github.com/zhaojinchu/logic_labs_website).

**Product experience**
- Responsive storefront with Tailwind + shadcn/ui components and a cart flow tuned for quick lap times on mobile.
- Session-aware navigation, magic-link auth, and protected routes that keep casual browsers out of the admin areas.
- Dedicated success journey that surfaces Stripe receipts, order summaries, and shipping notes without leaving the site.

**System design**
- Supabase service-role edge functions (`create-payment`, `retrieve-session`, `stripe-webhook`) validate carts, orchestrate Stripe sessions, and persist orders atomically.
- Postgres migrations capture product catalog, multi-quantity order items, and Stripe metadata for rich reporting.
- Stripe webhook hardening uses async signature verification and granular error codes so failures surface instantly in logs.

**Operations & deployment**
- Automated Supabase CLI deploys and Stripe sync scripts keep environments reproducible.
- Oracle Cloud Ubuntu VM runs Nginx as a static file server + reverse proxy with HTTPS-ready config for the upcoming domain.
- Hardened with firewall rules, process supervision, and rotating Supabase/Stripe secrets stored via `supabase secrets set`.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/4.1.png" title="Logic Labs Storefront" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Home page of the logic labs e-commerce website. 
</div>

Next up: connect the vanity domain, add inventory dashboards, and ship a lightweight CMS so the team can update kits without touching code.
