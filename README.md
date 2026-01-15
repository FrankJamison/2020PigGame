# The Pig Game (Dice Game)

A simple 2‑player browser game built with vanilla HTML/CSS/JavaScript. Players take turns rolling dice to build up a **round score**, then choose to **Hold** to bank it into their **global score**—but rolling a **1** ends your turn and costs your round points.

This project is part of my portfolio and focuses on DOM manipulation, game-state management, and clean UI updates.

---

## Live / Demo

- Portfolio demo: *[(https://2020-thepiggame.fcjamison.com/)]*

---

## Gameplay Rules

### Base Rules (1 Die)
- 2 players take turns.
- On your turn, click **Roll dice** as many times as you want.
- Each roll adds to your **Current (round) score**.
- If you roll a **1**, you lose your **Current** points and your turn ends.
- Click **Hold** to add your **Current** score to your **Global** score and pass the turn.
- First player to reach the **winning score** wins.

### Variation (2 Dice)
When the **2 Dice** mode is selected:
- Rolling a **1** on either die ends your turn (you lose current points).
- Rolling **double 1s** (snake eyes) resets your **entire global score to 0** and your turn ends.

---

## Controls / UI

- **New game**: resets scores and starts a new match.
- **Roll dice**: rolls the die/dice and updates the current score.
- **Hold**: banks the current score into the player’s global score.
- **Mode selector**: choose **1 Die** or **2 Dice**.
- **Final score input**: sets the winning score.
  - If blank/invalid, the game defaults to **100**.

---

## Tech Stack

- **HTML**: structure and layout
- **CSS**: styling and layout
- **JavaScript (Vanilla)**: game logic and DOM updates

---

## Project Structure

```
2020-ThePigGame/
  index.html
  css/
    style.css
  js/
    app.js
  images/
    back.jpg
    dice-1.png ... dice-6.png
```

---

## Run Locally

### Option A: Open directly
1. Open `index.html` in your browser.

### Option B: Use a local server (recommended)
Some browsers restrict certain local behaviors; running a server is a good habit.

- **VS Code Live Server** (easy):
  1. Install the “Live Server” extension.
  2. Right-click `index.html` → **Open with Live Server**.

- **XAMPP** (works great with this repo):
  1. Start Apache in XAMPP.
  2. Put the folder in your web root (commonly `C:\xampp\htdocs`).
  3. Visit `http://localhost/2020-ThePigGame/`.

---

## Customization

- **Change default winning score**: update the fallback value in `js/app.js` (currently defaults to `100` when the input is invalid).
- **Visual styling**: edit `css/style.css`.
- **Assets**: dice images and background are in `images/`.

---

## What I Practiced / Learned

- Managing game state with clear variables (active player, round score, global scores)
- DOM updates driven by state changes
- Event-driven UI (roll/hold/new game)
- Handling user input safely (fallback winning score)

---

## Notes / Known Behaviors

- The UI supports both 1‑die and 2‑dice play via the mode selector.
- In 2‑dice mode, rolling double 1s resets the active player’s global score.

---

## Credits

- Dice game concept: classic “Pig” dice game rules
- Icons: Ionicons (loaded via CDN)
- Font: Lato (loaded via Google Fonts)

---

## License

Add a license if you plan to distribute this publicly (MIT is common for portfolio projects).
