# Apartment Layout

To-scale, interactive floor plan of our apartment, with every piece of furniture placed room by room.

- Drag any piece, including from one room to another.
- Tap a piece to see its clearances to walls and other furniture.
- Rotate, Mirror (sofa) and Reset to proposal.
- A piece turns red when it goes past a wall, overlaps another piece or a built-in counter, or blocks a door swing.

One self-contained HTML file, no install. Open `index.html` in a browser, or use the GitHub Pages link once Pages is enabled.

Positions you move are saved in your browser on that device only.

## How updates work

- `furniture.json` holds the furniture list, the proposed positions and the notes. The app fetches it fresh every time it is opened or brought back to the screen, so a home-screen shortcut picks up changes without reinstalling.
- `version.json` holds the app version. When `index.html` changes, the version is bumped and the app reloads itself onto the new version.
- Positions you move yourself are kept, unless the proposal for that same piece changes. Then the new proposal replaces it.
- **Refresh** forces a fresh load. **Share app** sends the link.
