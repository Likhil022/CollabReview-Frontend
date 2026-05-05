# CollabReview — Frontend

Frontend application for **CollabReview**, a real-time collaborative code review tool.
Built with React and Monaco Editor, it provides an interactive interface for reviewing pull requests, collaborating live, and leveraging AI assistance.

---

## Overview

CollabReview enables developers to:

* Log in with GitHub
* View and open pull requests
* Review code diffs with Monaco Editor
* Collaborate in real time (presence, cursors, comments)
* Use AI to explain and analyze code

This repository contains the complete frontend UI and client-side integrations.

---

## Tech Stack

* React 18
* TypeScript
* Vite
* Tailwind CSS
* Monaco Editor (VS Code engine)
* WebSocket (STOMP client)
* Server-Sent Events (SSE)

---

## Project Structure

```
src/
 ├── api/          # REST + SSE clients
 ├── components/   # Reusable UI components
 ├── pages/        # Route-based pages
 ├── hooks/        # Custom hooks
 ├── context/      # Auth + WebSocket context
 ├── editor/       # Monaco editor integration
 ├── utils/        # Helpers and utilities
 └── App.tsx
```

---

## Features

* GitHub authentication flow (via backend)
* Pull request listing dashboard
* Monaco-based diff viewer with syntax highlighting
* Real-time collaboration:

  * Active user presence
  * Live cursors
  * Instant comment sync
* Inline comment threads
* AI features:

  * Explain selected code
  * Bug detection
  * Improvement suggestions (planned)

---

## Getting Started

### Prerequisites

* Node.js 18+
* npm or yarn

---

### 1. Clone repository

```bash
git clone https://github.com/<your-username>/CollabReview-frontend.git
cd CollabReview-frontend
```

---

### 2. Install dependencies

```bash
npm install
```

---

### 3. Configure environment

Create a `.env` file in the root:

```env
VITE_API_URL=http://localhost:8080
```

---

### 4. Run the application

```bash
npm run dev
```

Application runs at:

```
http://localhost:5173
```

---

## Application Flow

1. User logs in via GitHub
2. Dashboard displays pull requests
3. User selects a pull request
4. Review session loads with Monaco diff view
5. Multiple users collaborate in real time
6. User selects code → AI response streams in

---

## API Integration

### REST Endpoints

* Fetch pull requests
* Create and fetch sessions
* Manage comments

### WebSocket (STOMP)

* Session-based communication:

  ```
  /topic/session/{sessionId}
  ```
* Used for:

  * Presence updates
  * Cursor movement
  * Live comments

### SSE (AI Streaming)

```ts
const eventSource = new EventSource(
  `${import.meta.env.VITE_API_URL}/api/ai/analyze`
);
```

---

## Key Components

* **PR List Page** — Displays pull requests from GitHub
* **Review Session Page** — Main collaboration interface
* **Monaco Diff Editor** — Code viewing and selection
* **Comment Thread UI** — Inline discussions
* **AI Panel** — Displays streamed AI responses

---

## Development Notes

* Keep API types in sync with backend DTOs
* Avoid hardcoding endpoints; use environment variables
* Debounce cursor updates to reduce network load
* Manage WebSocket lifecycle carefully (connect/disconnect)

---

## Future Improvements

* UI/UX refinement
* Notifications system
* Optimistic UI updates
* Performance improvements for large diffs
* Better state management (Zustand/Redux)

---

## License

MIT
