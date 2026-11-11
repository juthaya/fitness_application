# FitChallenge — Group Fitness & Habit Tracker

> **Status:** Planning / pre-development

FitChallenge is a web application that helps people build sustainable fitness habits through friendly group challenges. Users can create or join groups, complete daily goals, earn points, and follow their progress on a shared leaderboard.

## Project goals

- Make healthy habits easy to track every day.
- Encourage consistency rather than extreme workouts.
- Create accountability through small private groups.
- Support fair, customizable challenges for different fitness levels.
- Build a portfolio-ready full-stack application with clear documentation and tests.

## Example: 30-day challenge

A group of 10 friends competes over 30 days. Each day, participants can log the following goals:

| Daily goal | Example completion rule | Points |
| --- | --- | ---: |
| Steps | Walk at least 10,000 steps | 10 |
| Workout | Complete a workout session | 15 |
| Nutrition | Eat at least two balanced meals | 10 |
| Sleep | Sleep at least seven hours | 10 |
| Hydration | Drink at least two litres of water | 5 |
| **Maximum per day** | | **50** |

These are **sample defaults**, not universal health recommendations. Challenge organizers should be able to adjust goals and thresholds for their members. A goal awards points at most once per participant per challenge day. Each participant's score is the sum of their earned points; ties can share a rank in the MVP.

## Minimum viable product (MVP)

A first release should allow users to:

1. Register, sign in, and manage a basic profile.
2. Create a private group and invite others with a join code or link.
3. Create a challenge with start/end dates and customizable daily goals.
4. Join a challenge within a group.
5. Manually check off completed goals once per day.
6. See today's progress, total points, and a group leaderboard.
7. Review previous daily check-ins and streaks.

**Not in the MVP:** wearable integrations, photo verification, AI coaching, payments, public social feeds, and push notifications.

## Proposed technology stack

| Layer | Proposed choice | Purpose |
| --- | --- | --- |
| Frontend | React + Vite | Interactive web interface |
| Styling | CSS (initially) | Responsive, accessible design |
| Backend | Python + FastAPI | API, scoring rules, and permissions |
| Database | PostgreSQL | Persist users, groups, challenges, and logs |
| Authentication | To be decided during implementation | Secure user sessions |
| Testing | Pytest + frontend testing tools | Validate core behavior |
| Hosting | To be decided | Deploy frontend, API, and database |

The stack is a proposal and can change before implementation.

## Step-by-step development roadmap

### Phase 1 — Plan and set up the repository

- [ ] Finalize the MVP feature list and scoring rules.
- [ ] Choose the tech stack and write down key architectural decisions.
- [ ] Create `frontend/`, `backend/`, and `docs/` directories.
- [ ] Add `.gitignore`, `.env.example`, and contribution/setup instructions.
- [ ] Initialize the frontend and backend projects.
- [ ] Confirm both projects run locally and commit the baseline.

**Done when:** a new developer can clone the repo and start both apps using documented commands.

### Phase 2 — Design the user experience

- [ ] Sketch login, dashboard, group, challenge, daily check-in, and leaderboard screens.
- [ ] Define navigation and mobile layouts.
- [ ] Create reusable UI components (buttons, cards, progress bars).
- [ ] Implement static screens with mock data.

**Done when:** users can navigate a realistic prototype without a backend.

### Phase 3 — Build the backend and database

- [ ] Design tables for users, groups, memberships, challenges, goals, and check-ins.
- [ ] Set up PostgreSQL and database migrations.
- [ ] Implement authenticated endpoints and authorization checks.
- [ ] Add group creation and membership endpoints.
- [ ] Add challenge creation, enrollment, and daily logging endpoints.
- [ ] Implement points calculation and leaderboard queries.
- [ ] Add automated tests for scoring and permissions.

**Done when:** the API supports an entire challenge workflow using test users.

### Phase 4 — Connect the frontend

- [ ] Implement registration and sign-in screens.
- [ ] Connect group creation and invitations.
- [ ] Connect challenge creation and participation.
- [ ] Build daily goal check-in controls and progress indicators.
- [ ] Display real leaderboard and check-in history data.
- [ ] Handle loading, errors, and empty states.

**Done when:** a user can complete the MVP workflow in a browser.

### Phase 5 — Test and deploy

- [ ] Test with a sample group of 10 users and a 30-day challenge.
- [ ] Verify scoring, duplicate submissions, date boundaries, and time zones.
- [ ] Verify users cannot edit another member's check-ins or private groups.
- [ ] Test mobile accessibility and keyboard navigation.
- [ ] Deploy the app with secure environment variables and HTTPS.
- [ ] Add deployment instructions, screenshots, and a demo link to this README.

**Done when:** invited testers can use the deployed application reliably.

### Phase 6 — Future enhancements

- [ ] Apple Health / Google Health Connect integrations, where technically supported.
- [ ] Optional evidence submission and group moderation.
- [ ] Badges, streak milestones, and personalized goals.
- [ ] Team-versus-team challenges and normalized scoring.
- [ ] Reminders and notifications with user consent.
- [ ] Analytics for habit consistency over time.

## Initial data model

- **User:** account and profile.
- **Group:** name, creator, privacy settings, invite mechanism.
- **Membership:** user, group, and role.
- **Challenge:** group, title, start/end dates, timezone, status.
- **Goal:** challenge, description, threshold, unit, and points.
- **Enrollment:** participant registered in a challenge.
- **CheckIn:** participant, goal, challenge date, completion status, and timestamp.

Database constraints should prevent duplicate completion awards for the same user, goal, and challenge date. The server, not the browser, should calculate authoritative scores.

## Fair play and privacy principles

- Manual activity logging is based on trust in the MVP; display that clearly.
- Allow goals to be adapted to different abilities and schedules.
- Store only data needed to operate challenges; avoid collecting sensitive medical information.
- Private groups should be visible only to authorized members.
- Users should be able to correct their entries and request account/data deletion.
- Clearly define the challenge's timezone and daily reset rules.

## Suggested project structure

```text
fitness_application/
├── README.md
├── .gitignore
├── .env.example
├── frontend/
│   └── (React app — Phase 1)
├── backend/
│   └── (FastAPI app — Phase 1)
└── docs/
    └── (design notes and API documentation)
```

*This is the planned structure, not the current repository layout.*

## Getting started

The project is currently in planning. Installation commands will be added when the frontend and backend are initialized in Phase 1.

To clone the repository:

```bash
git clone https://github.com/juthaya/fitness_application.git
cd fitness_application
```

## Current milestone

**Next task:** Phase 1 — agree on the stack, scaffold the frontend/backend, and run a basic page and health-check API locally.

## License

MIT — see [LICENSE](LICENSE).
