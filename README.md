# Tile Quest: Match and Learn Puzzle Challenge API

Backend API for Tile Quest: Match and Learn Puzzle Challenge, an educational game for the SorSU Bulan Campus Library. CS 313 Software Engineering 1, A.Y. 2026-2027.

- **Developer:** Trisha Joy Gutierrez (@trishajoy), Gian Carlo Erivera, Donnalyn Mae Nares (@donnalynnares-ux), Eron Hona
- **Course/Section:** BSCS 3-1
- **Group and game concept:** Group 4 — Tile Quest: Match and Learn is an educational game where players match the required tiles, complete puzzles, and answer quizzes to pass each level. Players earn points and advance to higher levels while improving their memory, focus, and knowledge.

This is my own build of my group's game concept. Every commit in this repository was made by me, with Git, on my own computer or in my own Codespace.

## Tech stack

| Layer | Tool |
|-------|------|
| Runtime | Node.js 22 LTS or newer |
| Web framework | Express 5 |
| Database | PostgreSQL 16 or newer |
| ORM and migrations | Sequelize 6 with sequelize-cli |

## Setup

git clone [repository-url]
cd [folder-name]
npm install

Copy .env.example to .env, then put your own PostgreSQL password in DB_PASSWORD.

npm run db:create    (first time only)
npm run db:migrate
npm run db:seed
npm run db:check
npm run dev

## Environment variables

| Key | Example | Purpose |
|-----|---------|---------|
| NODE_ENV | development | Which config block to use |
| PORT | 3001 | Port the API listens on |
| DB_HOST | 127.0.0.1 | PostgreSQL host |
| DB_PORT | 5432 | PostgreSQL port |
| DB_NAME | tile_quest | Database name |
| DB_USER | postgres | Database user |
| DB_PASSWORD | (your own) | Database password. Never commit this. |
| HUB_API_KEY | dev-hub-key | Key the Library Game Hub sends to read results. |

## Endpoints (Hub Contract v1.2)

Base URL: http://localhost:3001/api/v1

| Method | Path | Purpose | Success |
|--------|------|---------|---------|
| GET | /health | Is the API up and can it reach the database? | 200 (503 when the database is down) |
| GET | /game-info | Slug, name, group, developer, description, player limits, version | 200 |
| GET | /player/:id | Get player profile, progress, score, lives and current level | 200 |
| POST | /player | Register new player | 201 |
| PUT | /player/:id | Update player progress, score and lives | 200 |
| GET | /level/:id | Load level details: tiles, difficulty, time limit | 200 |
| GET | /level/:id/questions | Get quiz questions for a specific level | 200 |
| POST | /question/:id/validate | Submit answer and check correctness | 200 |
| GET | /leaderboard | Get ranked top player scores | 200 |
| GET | /results | Finished games, every player, and the top 3 | 200 (401 without the key) |

## What "completed" means in my game

A player completes the game when they have successfully finished all levels — matching every tile pair and answering the quiz for each level. Players can still progress even if some answers are wrong, but they must complete the puzzle to pass the level.

## Tables

players — Player accounts and profile data

admins — Administrator credentials and access levels

levels — Level configurations: tile layouts, difficulty, time limits

questions — Quiz questions, answer options, and correct answers per level

game_progress — Player's saved progress: completed levels, scores, lives remaining

## Database scripts

| Command | What it does |
|---------|-------------|
| npm run db:migrate | Runs migrations that have not run yet |
| npm run db:migrate:status | Lists every migration as up or down |
| npm run db:seed | Loads the seed data |
| npm run db:check | Counts the rows in every table |
| npm run db:reset | Empties the database, rebuilds every table and reloads the seed data |
| npm run dev | Starts the development server |
| npm run check | Runs the same automatic check that GitHub runs after every push |
