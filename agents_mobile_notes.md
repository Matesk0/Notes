# Project Configuration (AGENTS.md) - Mobile Notes

This file guides development inside the **`mobile-notes`** repository.

---

## 🏗️ Repository Overview
* **Name**: `mobile-notes`
* **Role**: Mobile Obsidian Devlog Wiki
* **Tech Stack**: Expo SDK 57 + React Native 0.86 + TypeScript + `lucide-react-native`
* **Backend Connection**: Shared Supabase DB (`notes` table).

---

## 📜 Development Rules
1. **Wiki Link Parsing**: Implement an inline regex parser that matches double brackets `[[note-slug]]` in the note text body and renders them as pressable text navigation hooks.
2. **Offline Caching**: Support local storage caching for notes to enable read operations when network connectivity is lost.
3. **Notes List**: Enable searching and filtering of notes by title or content tags.

---

## 📂 Backend Integration Details
- **Notes Table (`notes`)**: Columns `id`, `slug` (UNIQUE), `title`, `content` (Markdown text), `created_at`.
- **Endpoints**:
  - `GET /notes` - Fetch all notes metadata (slug, title).
  - `GET /notes/{slug}` - Fetch specific note markdown body.
  - `POST /notes` - Save or edit markdown notes (requires authenticated developer profile).
