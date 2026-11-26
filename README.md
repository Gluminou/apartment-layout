# Apartment Layout

To-scale, interactive floor plan of our apartment, with every piece of furniture placed room by room.

- Drag any piece, including from one room to another.
- Tap a piece to see its clearances to walls and other furniture.
- Rotate, Mirror (sofa), Remove (tap twice) and Reset to proposal. Removed pieces are listed under the furniture, tap one to put it back.
- A piece turns red when it goes past a wall, overlaps another piece or a built-in counter, or blocks a door swing.

One self-contained HTML file, no install. Open `index.html` in a browser, or use the GitHub Pages link once Pages is enabled.

Positions you move are saved in your browser on that device only.

## How updates work

- The plan (walls, rooms, door swings), the furniture list with its proposed positions, and the notes are not in this public repo. They are `content.json` in the private repo **Gluminou/apartment-layout-data**, written into its `data.json` under `apt-content` with `node tools/content.mjs put content.json data.json apt-content`. Devices connected with a key get them through `sync.js`; without a key the app shows only the key screen.
- `version.json` holds the app version. When `index.html` changes, the version is bumped and the app reloads itself onto the new version.
- Positions you move yourself are kept, unless the proposal for that same piece changes. Then the new proposal replaces it.
- **Refresh** forces a fresh load. **Share app** sends the link.

## Saving a layout

Tap **Save layout**. The app shares or copies a code starting with `APT1:` that lists every piece's position. Paste that code to Claude, who writes it into `content.json` in the private repo as the official layout, so every device shows it after the next open.

## Versions

The app shows its version number and date at the bottom, with a **Check for update** button and a **What's new** list. Release each change with:

```
node tools/release.mjs patch "What changed, in plain words"
```

`patch` for a fix, `minor` for something new on screen, `major` for a rework. The script keeps the page, `version.json` and `changelog.json` in step. The update section itself is `updates.js`, shared by all the apps.

## Sync between devices

`sync.js` (the same file in every Gluminou app) copies this app's data between devices through `data.json` in the private repo **Gluminou/apartment-layout-data**: where each piece sits and which pieces were removed, plus the plan itself. Each device connects once with a fine-grained GitHub key that has **Contents: Read and write** on that repo (**Read-only** gives view-only access). Paste the key in the **Sync between devices** section at the bottom of the page. On a computer the apps share one address, so a key entered in one app is offered to the others. Each app can still be disconnected on its own.

Changes from two devices are merged item by item. When both devices changed the same thing, the latest change wins. The repo history keeps every version.
