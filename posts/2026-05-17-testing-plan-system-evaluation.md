---
title: Week 9/10 - Testing Plan, System Evaluation, and Improvement Priorities
date: 2026-05-17
summary: This entry defines a testing and evaluation plan for the MojoJS, SQLite, and HTMX prototype, while identifying technical and UX improvements required before the system can be considered robust.
tags: [testing, system evaluation, accessibility, performance, security, interaction design]
---

## Testing Strategy Overview

This stage moves the project from implementation toward evaluation. The MojoJS, SQLite, and HTMX prototype must be tested as both an interface and an information system while preserving the BlaBla Corp template. All tests assume users are logged in, so the session cookie provides identity. The purpose is to verify routes, templates, SQLite persistence, and HTMX partial rendering.

## Accessibility Testing

The accessibility target is WCAG 2.1 AA or better. Key pages should be tested using keyboard navigation, Lighthouse, axe, and screen reader review. Checks include focus order, labels, validation errors, contrast, headings/link text, and HTMX feedback.

Compliance is validated when automated tools report no critical or serious WCAG issues, keyboard-only users can complete core tasks, and screen reader output communicates structure clearly.

## Performance Evaluation

Performance testing will use browser developer tools, Lighthouse, and repeated local runs with representative SQLite data. The metrics are TTFB for route/database response speed, FCP for visible content, and LCP for key listing or detail content.

The ideal load time is under one second. Between one and three seconds is acceptable, while any route or HTMX interaction above three seconds is a failure. HTMX partial requests should be faster than full-page reloads. SQLite queries should be checked for repeated queries, missing joins, and inefficient search/filter operations.

## Privacy / EU Cookie Compliance

The session cookie is necessary for authentication and does not require optional consent if strictly functional. A cookie audit should record name, purpose, duration, security flags, and essential status. Session cookies should use `HttpOnly`, `Secure` in deployment, and `SameSite=Lax` or stricter. Analytics, pixels, heatmaps, identifiers, or other tracking would require consent and a reject option.

## Security and Input Validation

Protected routes must read identity from the session and not trust submitted `user_id` values. SQLite testing should attempt SQL injection in search fields, listing IDs, forms, and messages, then confirm parameterised queries. Titles, descriptions, and messages should be tested with HTML-like input. Message privacy is validated when users cannot view unrelated threads by changing URL parameters.

## Responsive Design Testing

Responsive testing will validate mobile (320-480px), tablet (768-1024px), and desktop (1280px+) layouts. Test cases include navigation wrapping, listing grid collapse, readable cards, form width, message layout, tap targets, and image scaling. HTMX components need mobile review because partial updates can shift content or scroll position.

## Functional Testing Strategy

Functional testing focuses on route behaviour, persistence, and interaction correctness. Login tests should confirm protected routes read session identity and logout clears access. Listing tests should submit valid/invalid data, confirm SQLite persistence, and check validation. Messaging tests should verify sending, display, persistence, and access control. Filtering/search tests should cover empty queries, invalid characters, no-result states, combined filters, and database consistency. HTMX tests should confirm fragments update the correct target without duplicating layout.

## Git-Based Development Workflow Validation

Git will evidence controlled development. Each feature or fix should use a task branch, with commits reflecting route, template, database, or HTMX changes. Before merge, branches should pass checks and avoid unrelated template or stack changes.

## Performance Threshold Definition

Acceptable thresholds are: TTFB under 300ms locally where possible, FCP under one second, LCP under 1.5 seconds, HTMX partial responses under one second, and common SQLite queries below 100ms. Failure criteria include routes above three seconds, full-layout HTMX responses, sharply growing queries, or visible instability during partial updates.

## Identified System Improvements

Several improvements are clear. The main issue is inconsistency between SQLite persistence and fixture data, which can make the interface appear complete while real data flow remains fragile. The architecture needs cleaner boundaries between full-page templates and HTMX partials. Search/filtering need stronger empty-result, combined-filter, invalid-input, and database-backed handling. Product/listing flows remain incomplete around editing, validation, uploads, and confirmation states.

