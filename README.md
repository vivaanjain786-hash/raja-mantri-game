This repository contains the backend API for *Raja Mantr, a multiplayer role-based strategy game inspired by the traditional *Raja–Mantri–Chor–Sipahi game.

The backend is built using *Flask* and *SQLite*, handling room management, player actions, role assignment, scoring logic, and leaderboards.

---

## 🎮 Game Overview

- Each room has *4 players*
- Roles are randomly assigned:
  - Raja
  - Mantri
  - Sipahi
  - Chor
- The *Mantri* guesses the *Chor*
- Points are awarded based on roles and guess correctness
- Scores persist across rounds

---

## 🛠 Tech Stack

- Python 3
- Flask
- Flask-SQLAlchemy
- SQLite

---

## ⚙ How to Run

bash
pip install flask flask-sqlalchemy
python app.py

Server runs at:
http://localhost:5000

Core API Endpoints

GET	/	Health check
POST	/room/create	Create a room
POST	/room/join	Join a room
GET	/room/players/<roomId>	List players
POST	/room/assign/<roomId>	Assign roles
GET	/role/me/<roomId>/<playerId>	Get player role
POST	/guess/<roomId>	Mantri guess
GET	/result/<roomId>	Round result
GET	/leaderboard/<roomId>	Leaderboard

🧮 Scoring
Role	Points
Raja	1000
Mantri	800
Sipahi	500
Chor	0

If Mantri guesses incorrectly, Chor steals Mantri’s points.

## API Example (Nice Bonus for GitHub)

bash
POST /room/create
{
  "playerName": "Alice"
}
bash
Copy code
POST /room/join
{
  "roomId": "ROOM_ID",
  "playerName": "Bob"
}
bash
Copy code
