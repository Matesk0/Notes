# Spec: Notes Mobile App (`mobile-notes`)

This repository contains the standalone **Obsidian-Style Wiki Notes** React Native app, enabling double-bracket wiki link navigation and developer logs.

---

## 🛠️ Tech Stack & Dependencies
* **Framework**: Expo SDK 57 + React Native 0.86
* **Language**: TypeScript
* **Icons**: `lucide-react-native`
* **Network Client**: Axios or native `fetch` (fetching markdown logs from database)

---

## 📂 Folder Structure
```text
notes-app/
├── src/
│   ├── components/         
│   │   └── NoteLink.tsx       # Clickable wikilink renderer
│   ├── screens/
│   │   ├── NotesListScreen.tsx # Screen showing all note files
│   │   └── NoteViewScreen.tsx # Markdown reader displaying notes
│   ├── services/
│   │   └── api.ts             # Backend note synchronization endpoints
│   └── App.tsx                # App entrypoint and navigation
├── app.json
├── package.json
└── tsconfig.json
```

---

## ⚙️ App Requirements

### 1. Wiki Note Viewer
* Parses note bodies for the double-bracket format: `[[target-note-slug]]`.
* Converts text inside double brackets into a pressable, colored link. Clicking it updates the active note state to load and display the target note.

### 2. Note search / list
* Lists all notes stored in the wiki.

---

## 🔌 Backend API Connections
This app integrates with the backend using the following endpoints:

* `GET /notes` -> Fetches all available notes (slugs and titles).
* `GET /notes/{slug}` -> Fetches the markdown text body for a specific note.
* `POST /notes` -> Syncs or adds a new markdown note (optional/editor mode).
