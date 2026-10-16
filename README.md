# Tile Quest: Match and Learn Puzzle Challenge API

Backend API for Tile Quest: Match and Learn Puzzle Challenge — an educational tile-matching game focused on the Respiratory System. Software Engineering 1, A.Y. 2026-2027.

## Team Information
- Developers: Trisha Joy Gutierrez, Gian Carlo Erivera, Donnalyn Mae Nares, Eron Hona
- Course/Section: BSCS 3-1
- Game Concept: Tile Quest is a learning game where players match tiles showing parts of the respiratory system, complete puzzles, and answer quiz questions. Players earn points, unlock new levels, and reinforce their knowledge of how the respiratory system works.

## Tech Stack
Runtime        : Node.js 22 LTS or newer
Web Framework : Express 5
Database      : PostgreSQL 16 or newer
ORM           : Sequelize 6 + sequelize-cli

## How to Run
git clone https://github.com/trishajoy/quest-match-and-learn-puzzle-challenge.git
cd quest-match-and-learn-puzzle-challenge
npm install

Create a .env file using .env.example as your template, then update your database password.

npm run db:create
npm run db:migrate
npm run db:seed
npm run db:check
npm run dev

## Environment Variables
DB_HOST     = 127.0.0.1
DB_PORT     = 5432
DB_NAME     = tile_quest
DB_USER     = postgres
DB_PASSWORD = your_password_here
PORT        = 3001
NODE_ENV    = development

## API Endpoints
GET    /api/v1/health              Check if API is running
GET    /api/v1/game-info           Get game details
GET    /api/v1/player/:id          View player profile and progress
POST   /api/v1/player              Create new player account
PUT    /api/v1/player/:id          Update player score and progress
GET    /api/v1/level/:id           Get level details and tile layout
GET    /api/v1/level/:id/questions Get quiz questions for a level
POST   /api/v1/question/:id/validate Submit and check answer
GET    /api/v1/leaderboard         View top scores

## Game Completion
A player completes a level by correctly matching all tile pairs and answering the quiz questions. The game is fully completed when all levels are finished. You can still move forward even if you get some questions wrong — just try again!

## Database Tables
players          Player accounts and game progress
levels           Level details, tile layouts, and difficulty
tiles            Tile images, names, and matching pairs
questions        Quiz questions and correct answers per level
scores            Player scores, points earned, and level completion status
