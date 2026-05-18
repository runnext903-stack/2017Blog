---
title: Week 10 - Implementation-Driven System Refinement
date: 2026-05-16
summary: This week focused on integrating authentication, messaging, database relationships, and HTMX interactions into a more complete system architecture while reflecting on MVP trade-offs and emerging technical debt.
tags: [scope refinement, system design, DBML, feasibility, trade-offs]
---

## From Prototype to Integrated System

This week marked a transition from page-level design into a more integrated full-stack prototype. Earlier work focused on interfaces, but the project now connects authentication, messaging, routing, SQLite models, and server-rendered HTMX interactions. The design question therefore shifted from whether screens looked complete to whether the system behaved consistently under authenticated use.

---

## Project Architecture Overview

The project follows an MVC-style architecture using MojoJS, SQLite, HTMX, and server-side rendering. Controllers manage routes, services handle marketplace logic, SQLite models manage persistence, and views are rendered through templates. This shifted my focus from isolated screens to how data, routing, and interaction structure shape the user experience.

This architecture also creates testing responsibilities. Routes should read `user_id` and `username` from the session rather than trusting submitted identity values. SQLite queries should be parameterised, and HTMX partials should stay separate from full-page templates to avoid duplicated layout or inconsistent UI states.

---

## Complete Authenticated Application Flow

One major achievement was building a more complete authenticated flow. Users can log in, browse listings, filter categories, access profiles, and communicate through messaging. HTMX partial rendering makes filtering and message sending feel responsive without requiring a fully client-side application.

This flow should be tested at route level. A valid session should allow access to profile, listing, and messaging views, while logout should remove protected access. Message routes require privacy validation: changing a URL parameter should not allow one user to view another user's conversation.

---

## Dual Data Sources and Technical Debt

Integration exposed a major architectural issue: two data sources. The homepage marketplace still relies on fixture data, while profiles, products, conversations, and messages use SQLite-backed models. This was useful for rapid interface prototyping, but it now creates technical debt because product information effectively exists in two systems.

This inconsistency is a testable risk. Filtering, search, messaging, and product detail routes should be validated against the same source of truth. If SQLite-backed pages and fixture-driven pages show different listing states, the prototype may pass visual inspection while failing data consistency evaluation.

---

## Challenges in Maintaining MVC Separation

Rapid development also weakened MVC boundaries. Some controllers accumulated direct SQL queries and business logic instead of relying on service-layer abstraction. This accelerated implementation, but reduced maintainability and blurred responsibilities. Architecture is therefore not fixed once at the beginning; it needs continuous discipline as complexity grows.

---

## HTMX Integration Challenges

HTMX integration improved responsiveness, but made partial rendering more complex. Filters and messaging require a clear separation between full-page responses and fragment responses. This became noticeable in unfinished features such as search and campus filtering, where frontend interaction and backend routing can drift apart.

HTMX tests should compare each partial update with its full-page equivalent. Responses should update only the intended target, preserve valid markup, maintain focus where possible, and return consistent data. Partial responses should remain faster than full-page reloads and stay below the three-second maximum.

## Compliance and Quality Criteria

The integrated system should now be evaluated against explicit standards: WCAG 2.1 AA using Lighthouse, axe, and keyboard testing; responsive checks across mobile, tablet, and desktop; and performance checks using TTFB, FCP, and LCP, with under one second ideal and three seconds maximum. Privacy remains limited to necessary session cookies unless tracking is added. Git branches should map to specific route, template, database, or HTMX changes.

---

## Reflection

Looking back, Week 9 was less about creating new screens and more about confronting system integration. The project shifted into a platform with authentication, relational data, messaging logic, and reusable rendering structures. Several systems remain unfinished, including real search routing, product detail pages, persistent product publishing, and campus filtering. This week clarified that interaction design is shaped by data structures, routing, persistence, and architectural trade-offs.

---

## Next Step

The next priority is to reduce architectural inconsistency before adding visible features. Search robustness, product/listing completion, message privacy, input validation, and SQLite-backed persistence should be treated as evaluation criteria rather than optional polish.


