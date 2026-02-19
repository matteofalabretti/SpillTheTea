# Project Plan for SpillTheTea

## Introduction

SpillTheTea is envisioned as a startup project developed by a team of university students. The platform allows users to "spill the tea" on dating experiences, highlighting red flags and sharing stories in a safe, engaging way. The development will span 2 months (8 weeks), focusing on building an MVP (Minimum Viable Product) that can be tested with users and iterated upon.

### Objectives

- Deliver a functional MVP with core features.
- Demonstrate scalable architecture for future growth (e.g., mobile app integration).
- Use Agile methods for flexibility in a student team environment.
- Incorporate startup principles: fast iterations, user feedback, cost-effective tech stack.

### Scope

- Core: Authentication, posting stories, interactions (like/comment/repost), feeds, profiles.
- Stretch: Private chat, moderation tools, analytics.

## Team and Roles

- **Team Size**: 3-5 university students.
- **Roles** (flexible, with rotation):
  - Lead Developer: Oversees architecture and backend (1 person).
  - Frontend Specialist: UI/UX with JSP (1 person).
  - Database/Testing Engineer: Schema, DAO, tests (1 person).
  - Project Manager: Planning, meetings, docs (1 person, rotating).
  - All: Contribute to code reviews and features.

## Methodology

Adopt a **lightweight Agile approach** with 2-week sprints (4 sprints total). 

- **Daily Stand-ups**: 10-15 min via Discord/Zoom (what did I do? what will I do? blockers?).
- **Sprint Planning/Review**: Every 2 weeks, 1-hour meeting to prioritize backlog and demo.
- **Tools**: GitHub Projects for task board, Discord for comms, Google Docs for docs.

## Timeline (8 Weeks)

- **Week 1-2 (Sprint 1: Foundations)**
  - Setup repo, Maven, base architecture (layers: model, dao, service, web).
  - Database schema + initializer.
  - Authentication (register/login/logout).
  - Basic tests.
  - Deliverable: Running skeleton app with login.

- **Week 3-4 (Sprint 2: Core Features)**
  - Posting stories + feeds.
  - Profiles + follows.
  - Interactions (like, comment, repost).
  - Basic UI with JSP.
  - Deliverable: MVP with post creation and viewing.

- **Week 5-6 (Sprint 3: Enhancements)**
  - Chat functionality (1:1 messaging).
  - Search and trending.
  - Error handling + security basics (input validation).
  - More tests (integration/end-to-end).
  - Deliverable: Polished MVP with social interactions.

- **Week 7-8 (Sprint 4: Polish and Deployment)**
  - User feedback integration (simple form or survey).
  - Optimization (queries, performance).
  - Deployment to free hosting (Heroku).
  - Final docs, presentation prep.
  - Deliverable: Deployed app + demo video/report.

## Risks and Mitigation

- **Risk**: Time constraints from university classes.
  - Mitigation: Weekly check-ins, prioritize core over stretch features.

- **Risk**: Team coordination issues.
  - Mitigation: Use GitHub Issues/PRs, assign clear owners.

- **Risk**: Technical blocks (e.g., SQLite limits).
  - Mitigation: Start with simple schema, research alternatives early.

## Budget (Startup-like, Low-Cost)

- **Hardware/Software**: Free (university laptops, open-source tools).
- **Hosting**: Free tier Heroku ($0/month initially).
- **Total Estimated**: $0 (student project), future: $10-20/month for domain/hosting.

## Quality Assurance

- Code reviews on every PR.
- JUnit tests for DAO/service (aim 70% coverage).
- Manual testing for UI flows.
- Static analysis with SonarLint if time allows.

This plan is flexible—adjust based on sprint reviews. Let's spill the tea on bad dates! 🚀
