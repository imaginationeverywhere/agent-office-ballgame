# Ballgame MVP — the five steps

A reference implementation of the Ballgame loop, broken into five steps from plan to
production.

1. **Plan** — a Product Owner agent plans the work with a project-board tool embedded
   right in its workspace.
2. **Assign** — the plan's tasks are assigned out to frontend and backend build agents.
3. **Build** — each build agent works in an isolated sandbox environment and publishes
   a live preview of its change.
4. **Review** — independent reviewer agents check the code before it can merge.
5. **Ship** — approved work is promoted from development to staging to production; a
   human gives the final approval before production.
