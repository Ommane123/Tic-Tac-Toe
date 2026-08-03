# Tic-Tac-Toe — Play vs AI

A sleek, responsive, single-file Tic-Tac-Toe game featuring an intelligent AI opponent powered by the **Minimax Algorithm with Alpha-Beta Pruning**. Built as an AI Course Project, it runs entirely in the browser with no external dependencies.

## 🚀 Live Demo & Getting Started

Play the live game here: **[Tic-Tac-Toe Live Demo](https://ommane123.github.io/Tic-Tac-Toe-AI-Game/)**

Alternatively, since the entire application is contained within [index.html](file:///d:/Tic-Tac-Toe-AI-Game/index.html), you can:
1. Open [index.html](file:///d:/Tic-Tac-Toe-AI-Game/index.html) directly in any web browser.
2. Host it on your own platform (e.g., GitHub Pages, Vercel, or Netlify).

---

## 🎮 Features

- **Optimal AI Opponent**: Play against a Minimax-based AI that makes perfect decisions on Hard difficulty.
- **Adjustable Difficulty**:
  - **Hard (Optimal)**: The AI is unbeatable. It evaluates every possible state to win or secure a draw.
  - **Easy (Randomized)**: The AI introduces a 35% chance of making a random move, allowing players to win.
- **Interactive Controls**:
  - **New Game**: Reset the current board state.
  - **Toggle First Player**: Swap the starting player between You (X) and the AI (O).
  - **Scoreboard**: Real-time tracking of player wins, AI wins, and draws.
- **Immersive UI**:
  - Premium dark-themed, glassmorphic layout styled with custom CSS.
  - Interactive grid cells with micro-animations.
  - Dynamic confetti animation using `requestAnimationFrame` for game-over celebrations.
  - Custom modal dialogs to quickly restart or close game state.

---

## 🤖 How the AI Works

The AI relies on search algorithms to evaluate game states and make decisions:

### 1. Minimax Algorithm
The core decision-making function is [minimax](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L200-L230). It builds a complete decision tree of all possible future game states. It assigns scores to terminal states:
- **AI Win**: `+10 - depth` (incentivizes winning faster)
- **Human Win**: `depth - 10` (incentivizes dragging the game out to find potential blocks)
- **Draw**: `0`

### 2. Alpha-Beta Pruning
To optimize performance, the algorithm employs **Alpha-Beta Pruning** within the minimax evaluation.
- **Alpha ($\alpha$)**: The best value that the maximizing player (AI) can guarantee.
- **Beta ($\beta$)**: The best value that the minimizing player (Human) can guarantee.
- If at any point $\beta \leq \alpha$, the branch is pruned (discarded) because the opponent would never allow that path to be taken. This significantly reduces the number of evaluated states.

### 3. Difficulty Modes
- **Hard**: Invokes [bestMove](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L186-L198) directly, guaranteeing optimal play.
- **Easy**: At every turn, there is a $35\%$ chance that the AI picks a move at random from [availableMoves](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L176) to allow for human error and wins.

---

## 🛠️ Code Structure

The project is structured within a single file [index.html](file:///d:/Tic-Tac-Toe-AI-Game/index.html) to keep it lightweight and portable:

- **HTML Structure**: Elements for difficulty selection, the $3\times3$ grid, action buttons, and placeholders for overlays.
- **CSS Styling**: Responsive styling using CSS variables, flexbox, and grid layouts.
- **JavaScript Core**:
  - State tracking variables (board state, active player, scores).
  - Game logic routines ([cellClick](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L122-L127), [winner](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L178-L183), [finish](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L157-L172)).
  - AI logic routines ([bestMove](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L186-L198), [minimax](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L200-L230)).
  - UI effect helper functions ([showConfetti](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L263-L291), [showResultModal](file:///d:/Tic-Tac-Toe-AI-Game/index.html#L233-L261)).
