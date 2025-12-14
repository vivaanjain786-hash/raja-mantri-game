# 👑 Raja Mantri Chor Sipahi (RMCS) Game Backend

A server-side application built to manage the logic, state, and real-time communication for the classic Indian social game: **Raja Mantri Chor Sipahi** (King, Minister, Thief, Police).

## 🌟 Core Features

* **Real-Time Gameplay:** Utilizes WebSockets for instant, low-latency communication between the server and four players.
* **Game State Machine:** Implements robust state transitions (Lobby -> Role Reveal -> Guessing -> Scoring) for controlled gameplay.
* **Secure Role Distribution:** Ensures fair, random, and secret distribution of the four roles to the four players.
* **Scoring Engine:** Calculates scores accurately based on game rules (e.g., King 1000, Minister correct guess 800, etc.).
* **Room Management:** Handles creation, joining, and disconnection logic for dedicated game rooms.
* **Authentication:** Uses JWT for secure player session identification across REST and WebSocket connections.

## 🛠️ Technology Stack

The following technologies were used to build this backend service:

| Component | Technology | Version | Description |
| :--- | :--- | :--- | :--- |
| **Language** | `[e.g., Node.js]` | `[e.g., 18.x]` | Primary scripting language. |
| **Framework** | `[e.g., Express.js]` | `[e.g., 4.x]` | Web application framework for REST API. |
| **Real-Time** | `[e.g., Socket.IO]` | `[e.g., 4.x]` | Library for WebSockets communication. |
| **Database** | `[e.g., PostgreSQL]` | `[e.g., 14.x]` | Database for persistent data (scores, user profiles). |

## 🚀 Getting Started

Follow these steps to set up and run the backend server locally.

### Prerequisites

* `[Node.js / Python / etc.] (Version X.X or higher)`
* `[npm / pip / yarn]`
* A running instance of `[Database Name, e.g., PostgreSQL]`

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [Your Repository URL]
    cd [repository-name]
    ```

2.  **Install dependencies:**
    ```bash
    [npm install / yarn / pip install -r requirements.txt]
    ```

3.  **Environment Configuration:**
    Create a file named `.env` in the root directory and configure the following variables:

    ```env
    PORT=[Your Server Port, e.g., 3000]
    DATABASE_URI=[Your Database Connection String]
    JWT_SECRET=[A strong, random secret key for authentication]
    ```

4.  **Run Migrations (if applicable):**
    ```bash
    [npm run migrate / python manage.py migrate]
    ```

5.  **Start the server:**
    ```bash
    [npm start / node index.js / etc.]
    ```
    The server should now be running at `http://localhost:[PORT]`.

## 📖 API Documentation

The full API specification, including REST endpoints and WebSocket protocols, is available in the **OpenAPI (Swagger)** format for easy import into testing tools (Thunder Client, Postman).

* **View API Specification:** [Link to your `openapi.yaml` file on Drive or GitHub Gist]
* **Base URL:** `[http://localhost:3000/api/v1]`

### Key Endpoints Overview

| Type | Endpoint | Description | Authentication |
| :--- | :--- | :--- | :--- |
| **POST** | `/api/v1/players` | Creates a player session and returns the **JWT token**. | None |
| **POST** | `/api/v1/games` | Creates a new game room (Host required). | Bearer Token |
| **POST** | `/api/v1/games/{gameId}/join` | Player joins an existing game room. | Bearer Token |
| **POST** | `/api/v1/games/{gameId}/start` | Starts the round and distributes roles (Host only). | Bearer Token |
| **WS** | `/ws/game/{gameId}` | Real-time channel for gameplay and updates. | Query Param Token |

## 🧪 Testing

The API was tested using **Thunder Client** in VS Code to confirm successful player session creation, token handling, and game room state management.

To fully test the real-time game flow:

1.  Create 4 separate player sessions via `POST /players`.
2.  Use the 4 resulting JWT tokens to connect 4 separate WebSocket sessions to the same game room (`ws://...`).
3.  Execute the `start` and `guess` actions to confirm correct server-side logic.

## 🤝 Contribution

Feel free to open issues or submit pull requests. All contributions are welcome!

## 📜 License

This project is licensed under the **[MIT]# raja-mantri-game
