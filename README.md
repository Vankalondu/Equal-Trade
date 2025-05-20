---
## Monorepo Setup for Equal-Trade Project

This repository contains a Next.js main project (`equal-trade`) with two React apps inside the `app/` folder:

- `equal-buyer` (React app running on port 3001)
- `equal-seller` (React app running on port 3002)

### Folder Structure

```
equal-trade/
├── app/
│   ├── equal-buyer/
│   └── equal-seller/
├── package.json (root)
└── ...
```

### Dependency Management

- Root `package.json` uses **npm workspaces** to manage dependencies of all three projects.
- Run `npm install` at the root once to install dependencies for Next.js and both React apps.

### Running the Projects

- Run all three projects simultaneously with:

  ```bash
  npm run dev
  ```

- This uses `concurrently` to start:

  - Next.js app on `http://localhost:3000`
  - Buyer React app on `http://localhost:3001`
  - Seller React app on `http://localhost:3002`

### Scripts Summary (root `package.json`)

```json
"scripts": {
  "dev": "concurrently \"npm run dev:next\" \"npm run dev:buyer\" \"npm run dev:seller\"",
  "dev:next": "next dev --turbopack",
  "dev:buyer": "npm --workspace=app/equal-buyer start",
  "dev:seller": "npm --workspace=app/equal-seller start",
  "build": "next build",
  "start": "next start",
  "lint": "next lint"
}
```

---

This setup simplifies development by centralizing commands and dependency installation for all three projects in one place.

---
