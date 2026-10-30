# Mona's Commit Rush — V3 implementation

## Scope
Improved game design, characters, visual effects and responsive UX while preserving the Copilot canvas starter integration. The existing `extension.mjs` and `main` branch are unchanged. All game code remains in the self-contained `.github/extensions/monas-octoverse-arcade-starter/game.html` (HTML, CSS, vanilla JavaScript, no external dependencies).

## V3 improvements
- Cartoon illustrations for Mona and Copilot, expressive eyes, bobbing, tentacles, scarf, glowing companion and new effects for shields, magnet and dash.
- Three themed game worlds: Contribution City, Pull Request Highway and Merge Galaxy, with multiple animated layers, neon highlights and moving starfields.
- More distinctive enemies: basic, faster and glitch-moving bugs, and lateral-moving bosses every 25 commits, with a warning.
- Golden commits, five-commit combos, mission milestones and shield rewards.
- Compact gameplay HUD, mission progress bar, in-world labels, contextual Copilot sidekick and expandable help panel.
- Responsive touch/keyboard control refinements, reduced-motion support and corrected P/Escape pause shortcuts when other buttons are focused.

## Preserved contracts
- Each green or golden commit collected increments the commit counter exactly once.
- Copilot produces one new tip at each 10-commit milestone.
- Game speeds up progressively. Red bugs can end the run; shield/dash protect the player.
- Game Over provides restart; local best score, sound toggle, pauses, pointer controls and keyboard controls remain supported.

## Validation
- PASS: JavaScript syntax via `node --check`.
- PASS: Chromium start, motion, dash, pause/resume, sound and keyboard shortcut behavior.
- PASS: Deterministic red-bug collision -> Game Over -> restart.
- PASS: No JS page errors and no horizontal overflow at 280, 320, 390, 768 and 1280 CSS px in Chromium.
- PASS: Rendered desktop/mobile screenshots inspected.
- NOT_RUN: Final integration test within GitHub Copilot App canvas.
- NOT_RUN: Extensive long-session gameplay tuning or full screen reader audit.

### Assets and publication
The game draws characters and worlds with local Canvas code and embeds splash illustrations as inline SVG; it does not call external CDNs or load network assets. Please follow the GitHub mascot brand guidelines for any public promotional use.
