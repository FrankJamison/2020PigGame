# 2020 Pig Game (Vanilla JS)

A two-player browser game implementing the classic “Pig” dice rules with a 1-die mode and a 2-dice variation.

This project is intentionally “no framework” to highlight fundamentals: DOM-driven UI, predictable state updates, input validation, and clean UX feedback.

## Quick Pitch (Recruiter / Hiring Manager)

If you’re scanning for evidence of practical front-end skill, this project demonstrates:

- **Product thinking**: clear rules, discoverable controls, immediate feedback, and minimal friction to start playing.
- **UI/UX implementation**: a centered game board, strong hierarchy for scores, and state-based styling for “active” and “winner”.
- **Engineering fundamentals**: event-driven code, state management, defensive input handling, and reliable UI synchronization.
- **Professional polish**: consistent typography, iconography, and asset usage (background + dice sprites).

## Demo

- Public demo: https://2020-thepiggame.fcjamison.com/

## Gameplay

### 1 Die (Base Rules)

- Players alternate turns.
- **Roll dice** accumulates points into the **Current** (round) score.
- Rolling a **1** loses the round score and ends the turn.
- **Hold** banks the Current score into the player’s **Global** score and passes the turn.
- First to reach the **winning score** wins.

### 2 Dice (Variation)

When **2 Dice** is selected:

- Rolling a **1** on either die ends the turn and loses round points.
- Rolling **double 1s** (snake eyes) resets the active player’s **Global** score to 0 and ends the turn.

## Controls & UX Details

- **New game** resets state and UI (scores, names, active highlight, dice visibility).
- **Roll dice** shows dice images only when needed (reduces visual noise).
- **Hold** uses a **validated winning score**:
  - If the “Final score” input is blank/invalid, the game defaults to **100**.
- **Mode selector (1 Die / 2 Dice)** restarts the game to avoid mixed-rule ambiguity.

## Design & Front-End Implementation Highlights

### Layout & Visual Hierarchy

- **Single-screen experience**: everything fits within a centered `.wrapper` with consistent spacing.
- **Two-column player panels** communicate turn-taking and competition at a glance.
- **Strong score hierarchy**: large global scores, smaller current score modules.

### State-Based Styling

- **Active player indicator** is purely a CSS class toggle (`.active`), including an accent dot via a `::after` pseudo-element.
- **Winner state** uses a `.winner` class for immediate, high-salience feedback.

### Assets & Branding Consistency

- Background image with an overlay gradient improves text readability.
- Dice images are swapped via `src` changes (sprite-style asset set), keeping the DOM stable.
- Ionicons + Google Fonts are loaded via CDN for a clean, modern UI without build tooling.

## Engineering / Code Highlights (Developer Notes)

### State Model

Core game state is kept in a small set of variables:

- `scores`: global totals for both players
- `roundScore`: current turn accumulator
- `activePlayer`: index (0 or 1)
- `gamePlaying`: guard flag to disable input after win
- `gameVersion`: `"1"` or `"2"` based on the selector

This separation keeps UI rendering straightforward: UI text always reflects these state variables.

### Event-Driven Flow

- UI is driven by click events for **Roll**, **Hold**, and **New game**, plus a change event for **mode selection**.
- “Stop-the-world” logic is handled by `gamePlaying` so the UI can remain interactive-looking without allowing invalid state transitions.

### DOM Update Strategy

- Uses stable element IDs (`#score-0`, `#current-1`, etc.) for deterministic updates.
- Switches turns by toggling classes and resetting only the turn-scoped values.
- Dice visibility is controlled via `style.display`, keeping the layout consistent.

### Input Validation

Winning score is parsed using `parseInt` and validated with `isNaN` / range checks.
If invalid, the game falls back to a safe default (100), preventing `NaN` propagation.

## Tech Stack

- **HTML**: structure and semantics
- **CSS**: layout, typography, state styling
- **Vanilla JavaScript**: rules engine + DOM updates
- **Assets**: background + dice images

## Project Structure

```
2020PigGame/
  index.html
  css/
    style.css
  js/
    app.js
  images/
    back.jpg
    dice-1.png ... dice-6.png
```

## Run Locally

### Option A: Open directly

Open `index.html` in your browser.

### Option B: Serve from a local web server

If you prefer a local server (recommended for consistency), run one of these from the project folder:

- Python: `python -m http.server 5500`
- Node (if installed): `npx http-server -p 5500`

Then visit: http://localhost:5500/

## Customization Ideas

- Add a “**Reset winning score**” button and/or persist the setting in `localStorage`.
- Add keyboard controls (R = roll, H = hold, N = new).
- Add a small “rules” modal for first-time users.
- Add animations (dice shake, score transitions) while keeping state updates deterministic.

## Credits

- Game concept: classic “Pig” dice game
- Icons: Ionicons (CDN)
- Font: Lato (Google Fonts)

## License

No license specified. Add an MIT license if you plan to distribute this publicly.
