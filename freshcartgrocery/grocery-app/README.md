# FreshCart - Vegetables & Fruits Store (Static React App)
#this is sample data
#Shop farm-fresh fruits, organic vegetables, essentials online with fast, same-day delivery slots.

A ready-to-host static web app for a fresh vegetables & fruits store, built
with React — **no npm install and no build step required**. React, ReactDOM
and Babel are loaded from a CDN directly in `index.html`, and JSX is
compiled in the browser at runtime.
this is sample data

## What's included

```
grocery-app/
├── index.html        # Main app (React SPA) - entry point
├── error.html         # Static 404 page for server-level "error document" config
├── css/style.css       # All styling
├── js/app.js           # All React components (Home, Login, Admin, Cart, 404...)
└── README.md
```

## Features

- **Home page** — browse fresh vegetables & fruits, search, filter by category, add to cart
- **Login page** — toggle between **Customer** login and **Admin** login
- **Admin Dashboard** (protected route) — add / edit / delete products, view
  inventory stats; only reachable after logging in as admin
- **Cart page** — update quantities, remove items, see subtotal/delivery/total, checkout (demo)
- **404 / Not Found page** — shown for any unknown in-app route, plus a
  standalone `error.html` you can set as your static host's error document
- **Access Denied page** — shown if a non-admin tries to open `#/admin`
- **Compliance basics** — Privacy Policy, Terms & Conditions, Refund Policy,
  and Accessibility Statement (modal pop-ups from the footer), plus a cookie
  consent banner
- Fully responsive, semantic HTML, labelled form fields for accessibility

## Demo admin login

```
Username: admin
Password: Admin@123
```

⚠️ **This is a client-side demo only.** The admin check happens in the
browser's JavaScript, so it is **not secure for real production use**.
Before going live with real admin access, replace the login logic in
`js/app.js` (`ADMIN_CREDENTIALS`) with calls to a real backend that:
- stores only hashed passwords (e.g. bcrypt/argon2)
- issues a signed session/JWT over HTTPS
- rate-limits login attempts and supports MFA
- never exposes credentials in client-side code

Data (products, cart, logged-in user) is currently stored in the browser's
`localStorage` for demo purposes — it resets per-browser and isn't shared
between users. For a real store, connect this front end to an actual API
and database.

## How to run it

Because everything is static HTML/CSS/JS, you don't need Node, npm, or any
build tooling. Options:

**Option A — just open it**
Double click `index.html` (works in most browsers; some browsers restrict
local file loading of scripts — if so, use Option B).

**Option B — any simple local server**
```bash
# Python 3 (built into most systems)
cd grocery-app
python3 -m http.server 8080
# then open http://localhost:8080
```

## Deploying to static hosting

Upload the contents of this folder as-is to any static host:

- **AWS S3 + CloudFront**: enable static website hosting, set `index.html`
  as the index document and `error.html` as the error document.
- **Netlify / Vercel**: drag-and-drop the folder (or connect a repo) — no
  build command needed, output directory is the project root.
- **GitHub Pages**: push this folder to a repo and enable Pages on the
  `main` branch / root.
- **Azure Static Web Apps**: set the app location to this folder with no
  build step.

## Notes on the CDN approach

Loading React/Babel from CDN keeps this dependency-free to develop and
host, but Babel-in-browser JSX compilation adds a small runtime cost and
isn't recommended for very high-traffic production apps. If you later
want a compiled/optimized bundle, you (or a developer) can migrate this
same code into a Vite or Create React App project and run a normal
`npm install && npm run build` — but that is optional and not required to
use this app as-is.
