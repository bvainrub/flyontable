# Remember the Fly — 

A browser-based working memory trainer built around a simple but surprisingly demanding concept: a fly lands on a grid, you memorize its position, close your eyes, and follow its movement through audio commands alone. When you believe it has crossed the edge of the grid, you press Stop.

That's it. And it's harder than it sounds.

This project was vibe coded with [Claude.ai](https://claude.ai).

---

## What It Is

The game is a single HTML file with no dependencies, no build step, and no server required. Open it in a browser and it runs. It uses the Web Speech Synthesis API to deliver movement commands in either Russian or English, and the entire game state is managed in plain JavaScript.

The exercise itself is not new. Variants of spatial tracking under sensory restriction have been used in the training of intelligence personnel, fighter pilots, air traffic controllers, and competitive chess players. The underlying goal is always the same: force the brain to maintain and update a mental model without visual confirmation, under time pressure, with consequences for errors.

---

## How to Play

**Setup**

Choose a grid size between 5x5 and 20x20 using the plus and minus buttons. Select a speed from 1 to 3. Pick your language — Russian or English — using the toggle in the top right corner. Optionally enable Spectator Mode if a second person is watching (see below). The game adapts fully to both languages.

**Starting a Round**

Press Start. A fly appears on the grid. You have three seconds to memorize its position. The fly is placed with a bias toward the center of the grid — it will rarely start near an edge.

After three seconds the fly disappears and the commands begin.

**During Play**

A voice announces movements: "fly up", "fly down", "fly left", "fly right" — or the Russian equivalents. After each command, press the corresponding arrow key on your keyboard. This confirms you received the command and triggers the next one immediately rather than waiting for the timeout.

Keep the fly's position updated in your head with each command. You are tracking a point moving across an invisible grid.

**Ending a Round**

When you believe a command has moved the fly off the edge of the grid — press the spacebar. That is the Stop action.

The game ends when you press spacebar. Not before.

---

## Scoring

The scoring is intentional and unforgiving in a specific way.

If you press spacebar immediately after the command that caused the fly to exit the grid, and you have not pressed any arrow key since it exited, you receive **+10 points**.

If you press an arrow key after the fly has already exited — meaning you thought it was still on the grid — you receive **-1 point** for each such press. Those penalty presses do not end the game. Commands keep coming. Only spacebar ends the round.

If you press spacebar while the fly is still on the grid, you receive **-5 points**.

There is no partial credit. The only clean outcome is: fly exits, you notice immediately, you press spacebar, no arrows pressed in between.

**Level Progression**

Your level is determined by your total score. Every 100 points equals one level. If your score drops below a threshold — through penalties — your level decreases accordingly.

- Level 1: 0 to 99 points
- Level 2: 100 to 199 points
- Level N: (N-1) x 100 points

---

## Grid Size and Command Ranges

The number of commands issued before the fly is guaranteed to exit the grid depends on the grid size. Smaller grids use shorter sequences; larger grids require you to track more moves.

For grids 5x5 and 6x6, the fly exits somewhere between the 4th and 15th command.

For grids 7x7 and larger, the fly exits somewhere between the 7th and 20th command.

The exit is guaranteed within that range. The fly will not still be on the grid after the maximum number of commands. The exact exit point is randomized within the range each round.

---

## Speed Settings

After each command, a timer bar counts down. If you do not press an arrow key within the window, the next command fires automatically.

- Speed 1: 10 seconds per command
- Speed 2: 7 seconds per command
- Speed 3: 3 seconds per command

Speed can only be changed between rounds. Speed 3 is genuinely difficult — three seconds is not much time to process a command, update your mental model, and press a key.

---

## Spectator Mode

The Spectator toggle is designed for use with a training partner. When a coach or second player is watching the screen while you play with your eyes closed, this mode gives them a clear visual signal.

When Spectator Mode is on, the screen flashes red at the exact moment the fly exits the grid. The person watching sees the signal and knows you should now press Stop — but you don't see it, because your eyes are closed. This lets a trainer observe your reaction time and accuracy in real time without giving you any advantage.

When Spectator Mode is off, there is no visual indication on screen when the fly exits. You play completely blind, and nothing on the screen gives away the exit to anyone watching. This is the default for solo play.

The toggle is in the grid control row and can be switched at any time between rounds.

---

## Starting Position Bias

The fly does not appear with equal probability across all grid cells. Cells closer to the center are weighted more heavily. The weight formula is 1 divided by (1 plus distance from center), meaning a cell at the exact center is several times more likely to be chosen than a cell near an edge. Corners are excluded entirely.

This is intentional. Starting near an edge with a small grid makes the game trivial. Starting near the center forces more genuine tracking.

---

## Controls

| Key | Action |
|---|---|
| Arrow keys | Confirm command / track fly direction |
| Spacebar | Stop — declare that the fly has exited the grid |

Buttons on screen duplicate the Start, Stop, and Reset functions for mouse users.

---

## Languages

The game supports Russian and English. Switch using the RU / EN toggle in the top right corner. Language can only be changed when no round is in progress.

In English mode, the voice says "fly up", "fly down", "fly left", "fly right".
In Russian mode, the voice says "muha vverkh", "muha vniz", "muha vlevo", "muha vpravo".

All interface text, help content, scoring messages, and spoken commands switch with the language setting.

---

## The Help Panel

Click the Rules button in the top left corner to open a sliding panel with the full rules, scoring breakdown, timer reference, grid size table, spectator mode explanation, and background on the training history of the exercise. The panel is scrollable and available in both languages.

---

## Technical Notes

The game is a single self-contained HTML file. It requires no installation, no internet connection after the initial font load, and no backend of any kind.

Browser compatibility depends on Web Speech Synthesis support. This works in Chrome, Edge, and Safari. Firefox support for speech synthesis varies by platform.

The grid scales automatically to fit the viewport. On large grids, cells shrink so that the control buttons remain visible at all times. The layout does not scroll — everything stays on one screen.

---

## Running It

Download the file. Open it in a browser. That is the entire setup.

If you want to host it, drop it on any static file server or GitHub Pages. No configuration needed.

---
![](https://komarev.com/ghpvc/?username=bvainrub&color=blue&style=flat)
## About

Built as a focused single-purpose training tool. No accounts, no tracking, no data collection, no ads.
Special thanks to Алексей Ситников for inspiration 

Vibe coded with [Claude.ai](https://claude.ai).
