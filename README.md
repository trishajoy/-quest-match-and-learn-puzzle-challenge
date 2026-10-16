# Tile Quest: Match and Learn Puzzle Challenge API

Backend API for Tile Quest: Match and Learn Puzzle Challenge — an educational tile-matching game. Software Engineering 1, A.Y. 2026-2027.

## Team Information
Developers: Trisha Joy Gutierrez, Gian Carlo Erivera, Donnalyn Mae Nares, Eron Hona
Course/Section: BSCS 3-1
Game Concept: Tile Quest is a learning game where players match tiles, complete puzzles, and answer quizzes to pass each level. Players earn points and advance to higher levels while improving their memory and knowledge.

## Tech Stack
Runtime           Node.js 22 LTS or newer
Web Framework    Express 5
Database         PostgreSQL 16 or newer
ORM              Sequelize 6 with sequelize-cli

## Setup
git clone https://github.com/trishajoy/quest-match-and-learn-puzzle-challenge.git
cd quest-match-and-learn-puzzle-challenge
npm install

Copy .env.example to .env and enter your database password.

npm run db:create
npm run db:migrate
npm run db:seed
npm run db:check
npm run dev

## Environment Variables
DB_HOST     127.0.0.1
DB_PORT     5432
DB_NAME     tile_quest
DB_USER     postgres
DB_PASSWORD your_password
PORT        3001
NODE_ENV    development

## API Endpoints
GET    /api/v1/health              Check API status
GET    /api/v1/game-info           Get game information
GET    /api/v1/player/:id          Get player profile
POST   /api/v1/player              Register new player
PUT    /api/v1/player/:id          Update player score and progress
GET    /api/v1/level/:id           Get level details
GET    /api/v1/level/:id/questions Get quiz questions
POST   /api/v1/question/:id/validate Check answer
GET    /api/v1/leaderboard         View top player scores

## What "Completed" Means
A player completes the game when they finish all levels — matching all tile pairs and answering quizzes. You can still progress even if some answers are wrong, but you must complete the puzzle to unlock the next level.

## Database Tables
players          Player accounts and profile data
admins           Administrator login and access
levels            Level information and settings
questions         Quiz questions and correct answers
game_progress     Saved progress, scores, and lives
