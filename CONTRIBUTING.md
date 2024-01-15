# Project Info

## Directories

- config (dev config files)
- data (App data)
- db (Base database and migration scripts)
- dist (Frontend build)
- docker (Dockerfiles)
- extra (Extra useful scripts)
- public (Frontend resources for dev only)
- server (Server source code)
- src (Frontend source code)
- test (unit test)


## Coding Styles

- 4 spaces indentation
- Follow `.editorconfig`
- Follow ESLint
- Methods and functions should be documented with JSDoc

## Name Conventions

- Javascript/Typescript: camelCaseType
- SQLite: snake_case (Underscore)
- CSS/SCSS: kebab-case (Dash)

## Tools

- [`Node.js`](https://nodejs.org/) >= 14
- [`npm`](https://www.npmjs.com/) >= 8.5
- [`git`](https://git-scm.com/)
- IDE that supports [`ESLint`](https://eslint.org/) and EditorConfig ([`IntelliJ IDEA`](https://www.jetbrains.com/idea/))
- A SQLite GUI tool (f.ex. [`SQLite Expert Personal`](https://www.sqliteexpert.com/download.html) or [`DBeaver Community`](https://dbeaver.io/download/))

## Install Dependencies for Development

```bash
npm ci
```

## Dev Server

(2022-04-26 Update)

We can start the frontend dev server and the backend dev server in one command.

Port `3000` and port `3001` will be used.

```bash
npm run dev
```

But sometimes, you would like to restart the server, but not the frontend, you can run these commands in two terminals:

```bash
npm run start-frontend-dev
npm run start-server-dev
```

## Backend Server

It binds to `0.0.0.0:3001` by default.

It is mainly a socket.io app + express.js.

express.js is used for:

- entry point such as redirecting to a status page or the dashboard
- serving the frontend built files (index.html, .js and .css etc.)
- serving internal APIs of the status page

### Structure in /server/

- jobs/ (Jobs that are running in another process)
- model/ (Object model, auto-mapping to the database table name)
- modules/ (Modified 3rd-party modules)
- monitor_types (Monitor Types)
- notification-providers/ (individual notification logic)
- routers/ (Express Routers)
- socket-handler (Socket.io Handlers)
- server.js (Server entry point)
- uptime-kuma-server.js (UptimeKumaServer class, main logic should be here, but some still in `server.js`)

## Frontend Dev Server

It binds to `0.0.0.0:3000` by default. The frontend dev server is used for development only.

For production, it is not used. It will be compiled to `dist` directory instead.

You can use Vue.js devtools Chrome extension for debugging.

### Build the frontend

```bash
npm run build
```

### Frontend Details

Uptime Kuma Frontend is a single page application (SPA). Most paths are handled by Vue Router.

The router is in `src/router.js`

As you can see, most data in the frontend is stored at the root level, even though you changed the current router to any other pages.

The data and socket logic are in `src/mixins/socket.js`.

## Database Migration

See: https://github.com/louislam/uptime-kuma/tree/master/db/knex_migrations

## Unit Test

```bash
npm run build
npm test
```

## Dependencies

Both frontend and backend share the same package.json. However, the frontend dependencies are eventually not used in the production environment, because it is usually also baked into dist files. So:

- Frontend dependencies = "devDependencies"
  - Examples: vue, chart.js
- Backend dependencies = "dependencies"
  - Examples: socket.io, sqlite3
- Development dependencies = "devDependencies"
  - Examples: eslint, sass
