Build a Tetris game as a single self-contained HTML file.

VISUALS
- Black and white only. Pieces are white fill with black border, background is black, grid lines are dark grey (#222).
- Clean, minimal. No colors, no gradients, no shadows. No decorations.
- Responsive: centered on screen, canvas scales to fit viewport height (max ~600px tall).

CONTROLS
- Desktop: Arrow Left/Right move, Arrow Up rotate, Arrow Down soft drop.
- Mobile: on the canvas use touch—store touchstart clientX/clientY in variables (e.g. let touchStartX, touchStartY); on touchend use event.changedTouches[0].clientX/clientY. Swipe left/right = move; swipe up (finger moves up, endY < startY) = rotate; swipe down (endY > startY) = drop.
- On page load show ONLY the instructions modal. Start the game ONLY when the user clicks a "Start" or "START" button (do not call startGame() or init() on page load).

UI
- Score above the canvas, plain monospace (e.g. "Score: 0").
- Game over: overlay "GAME OVER", final score, and a RESTART button. No other UI.

TECHNICAL
- Pure HTML + vanilla JS + Canvas API. No libraries, no external resources. One file, works offline.

Data structures
- Board: 2D array grid[row][col], 20 rows × 10 columns. Row 0 = top, column 0 = left.
- Current piece: object with .shape (2D array of 0/1) and .pos or .x/.y (or .row/.col) for position. Initialize this object before the first tick (e.g. in startGame after resetting the grid).

Rendering (critical)
- Every game tick and after every move/rotate/drop: (1) clear the canvas, (2) draw grid lines, (3) draw all locked cells from the grid, (4) draw the current piece. If you have an updateBoard() or drawBoard() that draws the grid state, call it every time before drawing the current piece.

Tetrominoes (exactly 7, use these shapes so rotation/collision stay consistent)
- I: [[1,1,1,1]]
- O: [[1,1],[1,1]]
- T: [[0,1,0],[1,1,1]]
- S: [[0,1,1],[1,1,0]]
- Z: [[1,1,0],[0,1,1]]
- J: [[1,0,0],[1,1,1]]
- L: [[0,0,1],[1,1,1]]

Game logic
- Collision: for each 1 in the piece, compute board row = piece.row + row, board col = piece.col + col. If board row < 0, ignore (above playfield). If board row >= 20 or board col < 0 or board col >= 10, or if grid[board row][board col] is non-zero, then collision.
- Line clear: when a row is full, remove it and push a new empty row at top. After removing a row, check the same row index again (the row that fell down) so you don't skip lines; or use a while loop until the row is not full.
- Lock: when the piece cannot move down, write its cells into the grid at current position, then clear lines, then spawn the next piece. If the next piece overlaps the grid at spawn, game over.
- Spawn: set current piece to a new random shape and position (e.g. center top). If collision at spawn, game over.
- Do not reassign variables declared with const (e.g. if block size depends on resize, use let or a function that returns the current size).
