# Fae's Grimoire (recipes, formerly aoof.ca)

The 2024–25 version of aoof.ca. On the surface it was my portfolio; behind a login it held **Fae's Grimoire**, a shared recipe book for me and my friends. A SvelteKit front end is served by an Express and MongoDB back end on one Node server.

My current portfolio lives in [svelte-aoof-ca](https://github.com/Aoof/svelte-aoof-ca).

## Features
- Sign up, log in and log out, with bcrypt-hashed passwords, JWTs and sessions stored in MongoDB
- Create, view, edit and delete recipes: title, ingredients with amounts, instructions, cook time, food type, tags and a vegetarian flag
- Search and tag filtering, with paginated recipe cards
- Toast notifications and custom Svelte components
- A backup script that exports the recipes collection to dated JSON files and removes old logs
- In production, Express serves HTTPS with its own certificate and answers ACME challenges for renewal

## Tech
SvelteKit 2, Svelte 4, TypeScript, Tailwind CSS, SCSS · Node.js, Express, MongoDB, express-session, connect-mongo, JWT, bcrypt

## Project structure
```
frontend/   SvelteKit app (routes: home, add-recipe, recipe/[id], recipe/[id]/edit)
backend/    Express API (/api/auth, /api/recipes), MongoDB models, auth middleware, backup.js
buildrun.sh builds the front end, then starts the back end
```

## Run it locally
Requires Node.js 18+ and a MongoDB database (local or Atlas).

1. Create `backend/.env`:
   ```
   MONGO_URI=mongodb://localhost:27017
   DBNAME=recipes
   SESSION_SECRET=change-me
   JWT_SECRET=change-me
   PORT=3000
   ```
2. Install and start both parts:
   ```bash
   git clone https://github.com/Aoof/recipes-aoof-ca.git
   cd recipes-aoof-ca
   (cd backend && npm install && npm run dev)
   (cd frontend && npm install && npm run dev)
   ```
3. For a production-style run, use `./buildrun.sh`.

## Author
Abdulrahman (Aoof) Mousa · [aoof.ca](https://aoof.ca)
