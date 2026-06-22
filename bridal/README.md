# Shringar AI — Delhi Bridal Beauty

A single-file AI-powered bridal beauty platform for Delhi brides, built in pure HTML/CSS/JS with the Anthropic Claude API.

---

## Overview

Shringar AI is a luxury bridal beauty marketplace concept that connects brides with curated makeup artists, mehendi specialists, and bridal stylists across Delhi. The app includes a live AI stylist powered by Claude that gives personalised bridal look recommendations.

---

## Features

### Pages
The app is a single HTML file with a client-side page router (no frameworks). It has four main sections:

| Page | Description |
|------|-------------|
| **Home** | Hero section with an AI look generator demo |
| **AI Stylist** | Full conversational chat with the bridal AI |
| **Packages** | Filterable/sortable bridal package listings |
| **Booking** | Multi-step booking form with slot selection |

### AI Features (Claude-powered)
- **Hero Demo** — One-shot bridal look recommendation. The user describes their wedding (outfit, theme, skin tone) and gets a personalised 4–5 sentence styling brief covering makeup style, lip colour, mehendi, and hair.
- **AI Stylist Chat** — Multi-turn conversation with Shringar AI, a persona trained on Indian bridal traditions (Punjabi, Bengali, South Indian, Rajasthani, Marathi, and more). Maintains conversation history within the session.

### UI/UX
- Dark luxury aesthetic with a deep violet/rose/gold palette
- Glassmorphism cards, ambient orb animations, typewriter text effect
- Filterable package grid (by audience type and price range), sortable by price or popularity
- Artist filter chips
- Toast notification system
- Fully responsive layout

---

## Tech Stack

- **Pure HTML/CSS/JS** — no build tools, no frameworks, no dependencies
- **Fonts** — Cormorant Garamond (serif) + Outfit (sans) via Google Fonts
- **AI** — Anthropic Claude API (`claude-sonnet-4-6`) called directly from the browser

---

## Setup & Usage

1. Open `shringar_ai.html` in any modern browser.
2. The AI features require an Anthropic API key. The file currently calls the API without an explicit key (relies on the environment/proxy providing auth headers). To use it standalone, add your key to the fetch headers:

```js
headers: {
  'Content-Type': 'application/json',
  'x-api-key': 'YOUR_ANTHROPIC_API_KEY',
  'anthropic-version': '2023-06-01',
  'anthropic-dangerous-direct-browser-ipc': 'true'
}
```

> **Note:** Calling the Anthropic API directly from the browser exposes your API key in the client. For production, route calls through a backend proxy.

---

## Project Structure

Everything lives in a single file:

```
shringar_ai.html
├── <head>          Google Fonts, CSS custom properties, all styles
├── <nav>           Fixed top navigation with page links
├── #page-home      Hero + AI demo widget
├── #page-stylist   Full AI chat interface
├── #page-packages  Package grid with filters and sort controls
├── #page-booking   Multi-step booking flow
├── #toast          Global notification component
└── <script>        Page router, API calls, filter/sort logic, chat history
```

---

## Customisation

| What | Where |
|------|-------|
| Brand colours | `:root` CSS variables at the top of `<style>` |
| AI persona/tone | System prompt string in `sendChat()` and hero prompt in `runDemo()` |
| Package listings | `.pkg-card` elements in `#page-packages` |
| Artists | Artist cards in `#page-stylist` |
| Booking slots | `<select>` options inside the booking step HTML |

---

## Intended Use

This is a **frontend prototype / demo**. It has no backend, no authentication, and no real payment integration. It is suited for:

- Design presentations and client demos
- Rapid prototyping of AI-powered booking experiences
- A starting point to wire up a real backend (booking API, artist database, payment gateway)
