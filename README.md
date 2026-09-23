# Tic-Tac-Toe

A small, single-file browser game with a hand-drawn paper look. Play against a computer opponent or take turns with another person on the same device.

[Play the live game](https://tictactoe-morfius.vercel.app)

## Game modes

- **Vs. computer:** You play X; the computer plays O. X always starts.
- **Two players:** Two people take turns as X and O on the same board. X starts here too.

The scoreboard tracks X, O, and draws across rounds during the current page session. Reloading the page starts the scores over.

## How to play

1. Choose **vs. computer** or **two players**.
2. Select an empty square to place your mark.
3. Get three marks in a row, column, or diagonal to win. The winning line is highlighted; a full board with no winner is a draw.
4. Choose **new round** to clear the board while keeping the scoreboard, or **reset scores** to clear both.

The computer pauses briefly before responding, so its move feels like a turn rather than an instant update.

## How the computer chooses a move

The opponent uses the **minimax** algorithm. For each empty square, it simulates the computer’s move, then recursively explores the possible replies. It treats the computer’s result as something to maximize and the human’s response as something that minimizes that result. A computer win scores `10`, a human win `-10`, and a draw `0`.

That search makes the computer **unbeatable with optimal play**: it can win if a winning line is available, otherwise it can force at least a draw. A draw is still possible. The score does not include how quickly a win happens, so the computer does not specifically prefer the shortest winning path.

This is a small search over a nine-square board, not machine learning: the game checks the possible moves directly.

## Run it locally

1. Clone this repository:

   ```sh
   git clone https://github.com/jai25-byte/tic-tac-toe.git
   ```

2. Open the `tic-tac-toe` folder and double-click `index.html` to launch it in your browser.

There is no build step, package manager, or server requirement. The game works with the browser’s local file view. Google Fonts are used for the visual style when online; system fonts provide a fallback.

## Project structure

- `.gitignore` — keeps `.claude/` settings and macOS `.DS_Store` files out of the repository.
- `index.html` — page markup, styles, board creation, game rules, scoring, and the minimax opponent in one file.
- `README.md` — this project overview and run guide.

## What I learned building it

1. **Shape a page with HTML and CSS:** build a responsive board with CSS Grid, style controls, and give the project a consistent paper-and-ink visual identity.
2. **Connect interface actions to state:** create the nine square buttons, handle clicks, track turns, detect wins, and keep the scoreboard in sync.
3. **Think recursively with minimax:** evaluate the possible future moves for both players instead of choosing a computer move at random.

## Next improvements I can build myself

- Move the inline CSS and JavaScript into `style.css` and `game.js`, keeping the game working after each small change.
- Announce turn and win messages to screen readers, and label squares with their row and column.
- Add a short manual test checklist for mode switching, wins, draws, new rounds, and score resets.
