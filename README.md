# Application Workshop App

Private web application for the Application Workshop.

## Current layer

The repository currently contains the local DeepSeek Control Room:

- prompt and model selection
- Product Brain context display
- response, raw JSON, and next-step views
- token telemetry
- Skill Planning Workflow
- Research Mode

## Local setup

From this repository root:

```bat
copy server\.env.example server\.env.local
notepad server\.env.local
npm install
npm run check
npm run start
```

Open `http://localhost:3000`.

Set `WORKSHOP_BRAIN_PATH` to the local sibling Brain repository. The server reads only the allowlisted Product Brain files and never sends the whole repository to the browser.

## Repository boundary

- `application-workshop-brain` owns specifications, skills, templates, agents, and research.
- `application-workshop-app` owns the UI, server, provider router, tools, tests, and deployment configuration.

The app may read approved Brain context during development. It must not modify the Brain repository automatically.
