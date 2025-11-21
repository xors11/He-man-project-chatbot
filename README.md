# My Movie Watch

Curated, language-first movie recommendations powered by TMDB with a secure backend proxy.

## Requirements

- Node.js 18+
- TMDB API key

## Setup

1. Install dependencies:
   ```bash
   npm install express axios
   ```
   (Add `cors` if you run the frontend from a different origin.)

2. Create a `.env` file in the project root and set your API key:
   ```bash
   TMDB_API_KEY=your_tmdb_key_here
   ```

3. Start the server:
   ```bash
   node server/index.js
   ```

4. Visit `http://localhost:3000` to use the app.

## Project Structure

- `server/index.js`: Express server with `/api/recommend` proxy endpoint.
- `public/index.html`: UI shell.
- `public/styles.css`: Styling and responsive layout.
- `public/app.js`: Frontend logic, TMDB calls via proxy, modal interactions.

## Repo layout and Git guidance

- Keep the runtime code in the repository: `server/` (backend) and `public/` (frontend assets).
- Do NOT commit secrets or `node_modules`. A `.gitignore` is included that excludes `.env` and `node_modules`.
- Use the provided `.env.example` as a template for local environment variables.

To run locally:

```powershell
npm install
# copy .env.example to .env and set TMDB_API_KEY
node server/index.js
# or use npm start
npm start
```

To prepare for deployment (Heroku/Render): the repository includes a `Procfile` and `start` script in `package.json`.

## Notes

- The TMDB key never touches the frontend; all calls go through `/api/recommend`.
- If TMDB fails or no key is provided, the server responds with curated fallback data (`verified: false`).
- The frontend also contains a lightweight fallback list for complete resilience.

