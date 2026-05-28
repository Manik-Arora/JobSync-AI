# JobSync-AI

JobSync-AI is a resume review frontend built with TypeScript, Tailwind CSS, and Vite. The app enables users to upload a resume PDF, add a target job title and description, and receive an AI-powered resume review with ATS scoring, feedback, and improvement suggestions.

## Key Features

- Resume PDF upload with file preview
- PDF-to-image conversion for in-app resume display
- Job-specific resume analysis using AI feedback
- Detailed score breakdown: ATS, content, structure, tone & style, skills
- Secure resume storage using Puter file and key-value APIs
- Resume review page at `/resume/:id`

## Getting Started

### Install dependencies

```bash
npm install
```

### Run in development

```bash
npm run dev
```

Open the app at:

```text
http://localhost:5173
```

### Build for production

```bash
npm run build
```

### Start the built app

```bash
npm start
```

## Usage

1. Open the app and go to the resume upload screen.
2. Enter the company name, job title, and job description.
3. Upload a resume PDF file.
4. Click `Analyze Resume` to run the analysis.
5. After processing, the app redirects to `/resume/:id` for the review details.

## Project Structure

- `app/` – application entrypoint and route logic
- `app/routes/` – page components for upload, resume review, auth, home, and wipe
- `app/components/` – UI components like upload form, score cards, ATS review, and summary
- `app/lib/` – utilities for PDF conversion, Puter integration, and helper functions
- `app/constants/` – sample resume data and app constants
- `types/` – global TypeScript interfaces
- `public/` – static assets, images, icons, and example resumes

## Runtime Requirements

This app relies on a Puter-like runtime exposing `window.puter` with:

- `puter.auth` for authentication
- `puter.fs` for file upload/read operations
- `puter.ai` for AI feedback
- `puter.kv` for storing resume metadata

If `window.puter` is unavailable, upload and analysis behavior may not work correctly.

## Scripts

- `npm run dev` – start development server
- `npm run build` – build production output
- `npm start` – serve built app
- `npm run typecheck` – run React Router type generation and TypeScript checks

## Docker

A `Dockerfile` is included in the repo. To build and run with Docker:

```bash
docker build -t jobsync-ai .
docker run -p 3000:3000 jobsync-ai
```

## Vercel

A `vercel.json` file is included so Vercel can deploy the app as a static frontend.

If you already imported the repo on Vercel, use these project settings:

- Build Command: `npm run build`
- Output Directory: `build/client`
- Install Command: `npm install`
- Framework Preset: `Other`

Vercel will run the build and serve the generated client bundle. The `vercel.json` file also rewrites all routes to `index.html`, which is required for React Router.

> You do not need to commit the `build/` folder. It is intentionally ignored by `.gitignore`.

## Notes

- Uploaded resumes are stored using the app's Puter-backed file system.
- Resume review content is stored in key-value storage and presented on the review page.
- The app currently uses local constants and runtime APIs for feedback and demonstration purposes.

---

Built for job seekers who want AI-assisted resume optimization.
