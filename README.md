# SkazStrength
Skazius Strength Tracker is a lightweight, static SPA that runs entirely in the browser. Built with a small React + vanilla CSS stack, it provides an exercise library, a workout-logging form, lightweight analytics (SVG charts), and templates to speed data entry. Data is stored locally in the browser (localStorage) with no backend required, making it ideal for JAMstack deployments and GitHub Pages. The project is organized into a clean multi-file structure so you can iteratively evolve the app (e.g., add IndexedDB migration, cloud sync, richer analytics) without breaking the public single-page experience.

Skazius Strength Tracker — Static SPA (React + Vanilla CSS)
A compact, client-side SPA for logging strength workouts, viewing lightweight analytics, and planning with templates. Everything runs in the browser with localStorage, and the static site is designed for GitHub Pages deployment (npm run build → docs/ → upload to GH Pages).

Features
Single-page React app with client-side routing (Log / Analytics / Templates)
Exercise library with a searchable/selectable UI
Workout logging form: date, exercise, sets, reps, weight, RPE, rest, notes
Local persistence using localStorage (no backend)
Lightweight analytics: SVG charts for volume over time and PR tracking
Pre-built templates (Push Day, Pull Day, Legs Day) to speed up logging
Import/export JSON for data portability
Light theming (dark/light) with persistence (via CSS variables)
Static deployment friendly (GitHub Pages) with a small multi-file codebase
Tech Stack
Frontend: React (CSR, no server required)
Styling: Vanilla CSS (no frameworks)
Persistence: localStorage (client-side)
Build tooling: Vite (static build) → outputs to docs/ for GitHub Pages
Charts: Lightweight inline SVG (no external charting libs)
Getting Started
Prerequisites:

Node.js LTS installed
Basic familiarity with Git and GitHub Pages (docs/ folder or gh-pages branch)
Initial setup:

Install dependencies
npm install
Build for production (static assets)
npm run build
The build output will be in the docs/ directory
Deploy to GitHub Pages by uploading the contents of docs/ to your GitHub Pages host (either serve from docs/ on main or push to a gh-pages branch)
Development quickstart (optional, for local debugging):

npm run dev (if you want a dev server) and open the provided localhost URL
Project structure (high level)

index.html
Public entrypoint for the static site
src/
main.jsx
React entry that mounts the App
components/
App.jsx
Root app with internal views: Log, Analytics, Templates
LogForm.jsx
Workout logging form (date, exercise, sets, reps, weight, RPE, rest, notes)
WorkoutList.jsx
Recent workouts with delete/edit actions
Analytics.jsx
Lightweight SVG charts (volume over time, PRs)
Templates.jsx
Quick templates (Push Day, Pull Day, Legs Day)
store.js
LocalStorage wrapper for persisting workouts
lib/exercises.js
Pre-populated exercise library (SQ, BP, DL, OHP, ROW, PL)
styles.css
Plain CSS for theming and responsive layout
vite.config.js
Vite config to output to docs/ for GitHub Pages
package.json
Build scripts (dev, build, preview) and dependencies
README.md
This document (describes the app, setup, and usage)
Usage tips and guidance

Logging workouts
Go to the Log view
Enter date (defaults to today), choose an exercise (with helpful autocomplete), and fill sets, reps, weight
Optional: RPE, rest, and notes
Click “Log Workout” to persist locally
Templates
Open Templates to apply a preset (Push Day, Pull Day, Legs Day)
The first exercise from the template is loaded into the log draft for quick posting
Analytics
Switch to Analytics to see a simple volume-over-time sparkline and a PR table
The PR table derives simple personal records per exercise based on weight × reps
Import/Export
Use Export JSON to download your workouts
Use Import JSON to paste in a JSON array and merge with existing data
Persistence
All data lives in localStorage; it remains on the same device and browser
For cross-device sync later, you can evolve the data layer to IndexedDB and/or a cloud backend
Data model (Phase 1 MVP)

Exercise
name: string
muscleGroup: string
Workout
id: number (generated)
date: string (YYYY-MM-DD)
exercise: string (name)
sets: number
reps: number
weight: number (lbs)
volume: computed (weight × sets × reps)
rpe: number (optional)
rest: number (seconds, optional)
notes: string (optional)
Migration and future-proofing (phase ideas)

IndexedDB migration plan
Move storage from localStorage to IndexedDB with a small DataStore wrapper
Add migration path from older localStorage format to new DB schema
Cloud sync (optional)
Add an opt-in cloud sync (Firebase, Supabase, or a simple serverless endpoint)
Enhanced analytics
Calendar heatmap, rolling averages, and per-muscle-group insights
Training planning
More templates, periodization planning, and auto-generated macros
Collaboration and sharing
PR-style notes, progress sharing, or exporting PDFs
Licensing and contribution

This scaffold is intended for private or commercial projects. If you plan to publish or share publicly, consider adding a LICENSE file (e.g., MIT) and a CONTRIBUTING guide.
Notes

The README focuses on the static SPA approach with a multi-file React structure and vanilla CSS, built via Vite, and deployed to GitHub Pages.
If you want, I can provide a ready-to-paste README file block you can drop into your repo as README.md, or tailor the content to emphasize any particular feature or workflow you plan to highlight.
