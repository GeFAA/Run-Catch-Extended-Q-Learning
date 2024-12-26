# Run & Catch – Extended Q-Learning (Made by GeFA)

This repository contains a single **HTML file** (`index.html`) that demonstrates a **Q-Learning**-based “Run & Catch” scenario on a 6×6 grid:

- **Two Runners** (blue) try to survive for 30 seconds.
- **Two Chasers** (red) attempt to catch both Runners before time runs out.
- A **Q-Learning** system updates the policy for both teams (Runners and Chasers) each episode.
- **LocalStorage** is used to save/load the learned Q-tables, allowing the AI to persist across browser sessions.
- A custom **HUD** shows the game state (time, caught runners, etc.), and a **Chart.js** line graph tracks the **Runners’ Win-Rate** over multiple episodes.

---

## Main Features

1. **Q-Learning for Both Teams**  
   - Each team has its own Q-table.  
   - \(\epsilon\)-greedy actions; rewards for distance changes, attacking, catching, or avoiding capture.

2. **Auto-Restart Episodes**  
   - Game runs for up to 30 seconds.  
   - If both Runners are caught beforehand, the Chasers win immediately.  
   - Otherwise, if time expires with at least one Runner free, the Runners win.  
   - The code automatically starts a new episode (unless stopped), incrementing an episode counter.

3. **Model Persistence via LocalStorage**  
   - Q-tables are saved after each episode.  
   - On reload, the game continues from previously saved Q-tables.

4. **HUD & Live Chart**  
   - Time left, actions taken, episodes, and game status displayed in a panel-based HUD.  
   - **Chart.js** line chart for Runners’ overall win-rate across multiple episodes.

---

## Usage

1. **Clone or Download** this repository (you only need `index.html`).
2. **Open** `index.html` in a modern web browser:
   - Either directly (some browsers might restrict localStorage if loaded via `file://`).
   - Or, use a basic local server, for example:
     ```bash
     python -m http.server
     ```
     then go to [http://localhost:8000/index.html](http://localhost:8000/index.html) in your browser.
3. **Click “Start”** to begin the first episode:
   - Two Runners and two Chasers will move on the 6×6 grid.
   - The Runners try to survive; the Chasers try to catch them.
4. **Observe** the Q-Learning in action:
   - At each episode’s end, the result (Runners win or Chasers win) updates the stats.
   - After a brief pause, the next episode starts automatically (unless you click “Stop”).
5. **Monitor** the **HUD**:
   - Time left in the current episode.  
   - How many Runners are caught.  
   - The chosen action (e.g., `UP, DOWN, STAY, ATTACK, SPECIAL`) for each team.  
   - The overall **episode count**, and in the **Chart**, the Runners’ win-rate.
6. **Stop** the process anytime with the “Stop” button. The next run can continue from the stored model.

---

## Customizing

- **Adjust Q-Learning**: Tweak parameters \(\alpha, \gamma, \epsilon\) in the Brython code.  
- **Rewards**: Edit the distance-based rewards, catching penalty/bonus, or attack/special logic to encourage different AI behaviors.  
- **Auto-Restart**: Switch off `AUTO_RESTART` or change `EPISODE_DELAY_MS` in the code to control the downtime between episodes.  
- **LocalStorage**: If you prefer ephemeral training, remove the calls to `load_all_q_tables()` / `save_all_q_tables()`.

---

## Contributing

Feel free to open issues or pull requests to improve the AI logic, add new features, or enhance the visuals. Feedback is welcome!

---


