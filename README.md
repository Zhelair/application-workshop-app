# Application Workshop App

Private web application for the Application Workshop.

## Current layer

The repository currently contains the Vercel DeepSeek Control Room:

- prompt and model selection
- Product Brain context display
- response, raw JSON, and next-step views
- token telemetry
- Skill Planning Workflow
- Research Mode

## Runtime

Vercel is the primary runtime. The repository does not require a local server or local API-key file.

Run only the syntax check before pushing:

```bat
npm run check
```

## Vercel setup

Import this private repository into Vercel. Add these server-side environment variables in **Project → Settings → Environment Variables**:

```text
DEEPSEEK_API_KEY
DEEPSEEK_BASE_URL=https://api.deepseek.com
DEEPSEEK_MODEL=deepseek-v4-flash
APP_ACCESS_PASSWORD=<long private password>
BRAIN_GITHUB_TOKEN=<fine-grained read-only GitHub token>
BRAIN_GITHUB_OWNER=Zhelair
BRAIN_GITHUB_REPO=application-workshop-brain
BRAIN_GITHUB_REF=main
```

Do not add these values to the browser, repository, or public build files. `APP_ACCESS_PASSWORD` protects the app session. `BRAIN_GITHUB_TOKEN` is used only by the server to read the allowlisted Brain files.

Enable Vercel Deployment Protection for previews. The application gate remains enabled so an exposed deployment cannot use the DeepSeek key without the private password.

## Repository boundary

- `application-workshop-brain` owns specifications, skills, templates, agents, and research.
- `application-workshop-app` owns the UI, server, provider router, tools, tests, and deployment configuration.

The app reads approved Brain context server-side through the private GitHub token. It must not modify the Brain repository automatically.
