> **Celaya Solutions Research Course Edition.** Read [COURSE_EDITION.md](COURSE_EDITION.md) before you start. Use fake data only.

# Kanban Board

Project 01 on the [Zero to Agent project shelf](https://zerotoagent.org/course/landing.html#projects). Core track. You fork this at Level 6 and it stays yours through Level 9.

A board with columns and cards. You make a column, you add cards to it, you drag a card to the next column. That is the whole app, and that is the point.

## Why this one is first

It is the smallest honest full stack in the catalog. Two tables, a short list of API routes, and a screen that is obvious the second you open it. When you drag a card, you can watch the request leave the page, hit the server, and change a row in the database. Nothing else on the shelf shows you that trip so clearly.

Pick this one if you have never shipped anything before. Nobody loses points for starting here.

## What you have to change to pass

The same five things are asked of every project on the shelf:

1. A change you can see on the screen.
2. A change to the server or to what gets stored.
3. The frontend live on Vercel.
4. The backend running on Railway, still running tomorrow.
5. A three minute demo: the problem, the before, the after.

## Run it on your machine

```bash
pnpm install
cp .env.example .env
pnpm dev
```

Open the address the terminal prints. Set `APP_PASSWORD` and `SESSION_SECRET` in `.env` first; the server refuses to serve without them. The database file is created on the first run.

Checks before you hand anything in:

```bash
pnpm build
pnpm typecheck
pnpm smoke          # with the app already running
pnpm db:export -- exports/my-backup.db
```

## Where to look when you want to change something

| What you want to change | Where it lives |
| --- | --- |
| What the page looks like | `src/client/components/` |
| How the board loads and saves | `src/client/hooks/use-board.ts` |
| Drag and drop behavior | `src/client/hooks/use-drag.ts` |
| What the API does | `src/server/index.ts` |
| What gets stored | `src/server/schema.sql` |
| The class password gate | `src/server/course-app.ts` |
| How the server starts | `src/server/node.ts` |

## What it stores

Two tables. `lists` is a column, with a title and a position. `cards` belongs to a list and carries a title, a description, and a position. Deleting a list deletes its cards.

## Putting it online

The screen goes on Vercel. The server and the database go on Railway, on a volume, so your cards are still there the next morning. Step by step in [COURSE_EDITION.md](COURSE_EDITION.md). Copy `vercel.example.json` to `vercel.json` and replace `YOUR-RAILWAY-DOMAIN` with your Railway address, or the live page will have no server to talk to.

## Built with

Preact and TypeScript on Vite for the screen. Hono on Node 22 for the API. SQLite for storage.

## Source and license

Imported from an open source kanban project. The source project, the exact commit, and what was changed for the course are recorded in [UPSTREAM.md](UPSTREAM.md). The original MIT license and copyright notice are kept in [LICENSE](LICENSE) and stay with any copy you make. Package names still carry the source project's identifiers so the build keeps working.

This is a course edition, not a product. It is free and noncommercial, and the Celaya Solutions Research Course Edition notice stays on it.
