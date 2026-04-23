# 🍃 Naruto Quiz — Context File

**Project:** Naruto Quiz Website  
**Developer:** Alakshit Pradhan  
**Type:** Single-file HTML Web App  
**File:** `index.html`

---

## 🎯 What This Project Is

A fast, interactive **Naruto character quiz** where a ninja's portrait appears and you have to pick the correct name from 4 options — within 8 seconds. Built as a single self-contained HTML file, no framework or build step needed.

Inspired by the classic *"Who's That Pokémon?"* format, adapted for the Naruto universe.

---

## 🕹️ How It Works

1. Open `index.html` in any browser
2. Home screen loads **instantly** — no waiting
3. Click **Genin / Chunin / Jonin** to choose difficulty
4. The app fetches **50 characters** for that mode from AniList API (~1–2 sec)
5. Quiz starts — 50 questions, 8 seconds each, 4 answer choices
6. Score and ninja rank shown at the end

---

## ⚙️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Pure HTML + CSS + JavaScript |
| Framework | None — single `.html` file |
| Images | AniList GraphQL API (`graphql.anilist.co`) |
| Fonts | Google Fonts — Cinzel + Nunito |
| Build | No build step — open directly in browser |

---

## 🌐 Image Source — AniList API

Characters and their portrait images are fetched from the **AniList GraphQL API** at quiz start (per mode). AniList is free, public, and CORS-enabled — no API key required.

**Endpoint:** `https://graphql.anilist.co`

**Query used:**
```graphql
{
  Media(id: <anime_id>, type: ANIME) {
    characters(page: <page>, perPage: 25, sort: FAVOURITES_DESC) {
      nodes {
        id
        name { full }
        image { medium }
      }
    }
  }
}
```

**Anime IDs used:**
| Mode | Anime IDs | Pages |
|---|---|---|
| Genin (Easy) | 20 (Naruto), 1735 (Shippuden) | 1, 2 |
| Chunin (Medium) | 1735 (Shippuden), 20 (Naruto) | 2, 3, 4 |
| Jonin (Hard) | 34566 (Boruto), 1735 (Shippuden) | 1, 3, 4 |

Characters with missing/default images are automatically excluded.

---

## 🎮 Game Features

- **3 Difficulty Modes:**
  - 🌿 **Genin** — Most famous characters (Naruto, Sasuke, Itachi, etc.)
  - 🔥 **Chunin** — Supporting cast & Shippuden characters
  - ⚡ **Jonin** — Boruto era & deep-cut characters

- **8-second timer** per question — bar turns amber then red as time runs out
- **50 questions** per round
- **4 answer choices** — shuffled each time
- **Keyboard shortcuts** — Press `1`, `2`, `3`, `4` to answer
- **Grading system** — S / A / B / C / D / F based on score
- **Smart caching** — replaying same mode uses cached data (instant restart)
- **Preloading** — next question's image loads in background for smooth transitions

---

## 🎨 Design — Light Naruto Theme

- **Background:** Warm cream `#FFF8F0` with subtle konoha symbol tile pattern
- **Primary colour:** Orange `#E8520A` — matching Naruto's outfit
- **Accent:** Forest green for correct answers, red for wrong
- **Hidden Leaf marks 🍃** scattered throughout the UI
- **Sticky header:** `🍃 NARUTO QUIZ 🍃` + `Made by Alakshit Pradhan`
- **Sticky footer:** `🍃 Made by Alakshit Pradhan 🍃`
- **Portrait frame:** Animated rotating fire-gradient ring around character image
- **Fonts:** Cinzel (headings/titles) + Nunito (body text)
- **Japanese rank labels:** 下忍 / 中忍 / 上忍 watermarked on mode cards

---

## 📁 File Structure

```
naruto-quiz/
├── index.html      ← Entire app (HTML + CSS + JS in one file)
├── context.md      ← This file
└── README.md       ← Project description
```

---

## 🚀 Running Locally

No setup required:

```bash
git clone https://github.com/Alakshit-Pradhan/naruto-quiz.git
cd naruto-quiz

# Option 1 — just open the file
open index.html

# Option 2 — serve locally
python3 -m http.server 8000
# then visit http://localhost:8000
```

**Requirements:** A modern browser + internet connection (for AniList API and Google Fonts on first load).

---

## 🔄 How Loading Works

```
Open file
    ↓
Home screen visible INSTANTLY (no fetch on startup)
    ↓
User clicks Genin / Chunin / Jonin
    ↓
Card shows "⏳ Loading..." (~1-2 seconds)
    ↓
50 characters fetched from AniList for that mode
    ↓
Quiz starts immediately
    ↓
Play Again → loads from cache (instant)
```

---

## 📊 Scoring / Grades

| Score | Grade | Title |
|---|---|---|
| 95–100% | S | 🔥 Hokage Level! |
| 85–94% | A | ⚡ Elite Jōnin! |
| 70–84% | B | ✊ Solid Chūnin! |
| 55–69% | C | 🌿 Decent Genin |
| 40–54% | D | 😅 Keep Training... |
| 0–39% | F | 💀 Back to Academy! |

---

## 🔗 Related Projects

- **Pokemon Quiz** — [github.com/Alakshit-Pradhan/pokemon_quiz](https://github.com/Alakshit-Pradhan/pokemon_quiz) — Same format, Pokémon theme, uses PokeAPI

---

*Made with 🍃 by **Alakshit Pradhan***
