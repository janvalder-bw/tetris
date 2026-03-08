Build a Tetris game as a single self-contained HTML file.

VISUALS
- Black and white only. Pieces are white with black border, background is black, grid lines are dark grey (#222).
- Clean, minimal. No colors, no gradients, no shadows. No decorations.
- Responsive layout: centered on screen, canvas scales to fit viewport height (max ~600px tall).

CONTROLS
- Desktop: Arrow Left/Right to move, Arrow Up to rotate, Arrow Down to soft drop.
- Mobile: swipe left/right/up/down on the canvas (swipe up = rotate, swipe down = drop).
- Show modal with instructions (desktop, mobile) before game starts.

UI
- Score displayed above the canvas, plain monospace text.
- When game ends: show "GAME OVER" overlay with final score and a RESTART button.
- No other UI elements.

TECHNICAL
- Pure HTML + vanilla JS + Canvas API only. No libraries, no external resources.
- Everything in one file. Must work offline.
- Standard Tetris rules: 7 tetrominoes, line clears score points, pieces lock on landing.