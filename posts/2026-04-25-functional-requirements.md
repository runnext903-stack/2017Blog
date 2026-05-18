---
title: Week 7 – Interpreting Functional Requirements for a Student Relocation Community Hub
date: 2026-04-25
summary: Early-stage interpretation of the project brief and identification of functional requirements for a relocation-focused community platform for international students in Sydney.
tags: [functional requirements, community hub, relocation, interaction design]
---

## Understanding the Problem Context

Based on our own experiences as international students living in Sydney, we initially explored design directions around scenarios of frequent relocation, where students often need to acquire or dispose of household items within short timeframes.

Through early discussion, we identified that the core challenge is not simply access to second-hand goods, but the coordination effort required when managing relocation-related exchanges. This shifted our framing from a generic item exchange system towards a relocation-focused community context, where interaction efficiency and time sensitivity become central concerns.

---

## Assessing Existing Solutions

Existing platforms such as Facebook Marketplace already support peer-to-peer buying and selling. However, their interaction model is designed for general-purpose marketplace activity rather than relocation-specific coordination.

In practice, users must navigate unstructured listings, repeatedly negotiate availability with different sellers, and manage uncertainty around timing and pickup arrangements. This creates several limitations in the context of international student relocation:

- Lack of structured support for time-sensitive availability
- High communication overhead across multiple separate transactions
- Limited mechanisms for coordinating bundled or multiple-item needs
- Reduced efficiency due to mixed listings from unrelated user groups

This analysis suggests that the limitation is not purely functional, but structural: general marketplace systems are not optimised for coordinated, time-constrained relocation scenarios.

---

## Reframing the Interaction Model

Through further group discussion, we refined the concept from an item-centric marketplace into a hybrid system that incorporates both item exchange and community-based coordination.

We observed that relocation scenarios often involve bundled needs rather than isolated item purchases. For example, students moving into new accommodation typically require multiple items (e.g. furniture and kitchen equipment) within a short timeframe. In a traditional marketplace model, this results in fragmented interactions across multiple sellers, increasing cognitive load and communication effort.

To address this, we propose introducing a community posting space where users can share broader needs or available bundles of items. This shifts the system from individual item matching to coordination-based matching, where users can more efficiently align overall relocation requirements.

This also introduces a temporal dimension to the interaction model, as users may begin planning their relocation before arriving in Sydney. Early browsing of community posts enables pre-arrival coordination and reduces last-minute transactional pressure.

---

## Identifying Core Functional Requirements

Based on this reframed understanding, we identified the following core functional requirements.

Users should be able to:
- Create individual item listings during relocation periods
- Post community messages describing bundled needs or available item sets
- Filter and browse both items and community posts based on category and relevance
- Communicate with other users to coordinate exchange and pickup arrangements

The system should also:
- Store structured item data as well as unstructured community posts
- Support lightweight user accounts with session-based identity
- Enable simple messaging or coordination between users

These requirements also informed early technical considerations. Since users are expected to access the system under time pressure and primarily via mobile devices, the interface should prioritise fast content creation and low-friction navigation. This supports a design decision to favour structured filtering and simplified communication flows over more complex systems such as real-time chat or algorithmic recommendations.

---

## Scope and Next Steps

Given the constraints of the project timeline, advanced features such as payment integration is considered out of scope for the initial prototype. This allows the focus to remain on usability, coordination efficiency, and feasibility within the required tech stack.

The next stage of development will involve wireflows and interaction diagrams to further evaluate how users navigate between individual item exchange and community-level coordination within time-sensitive relocation contexts.