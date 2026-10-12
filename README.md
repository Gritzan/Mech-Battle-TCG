# MechBattle Virtual Table

## Pages
- `index.html`: home (Play / Deck Builder).
- `play.html`: the match table (rooms, decks, field, counters).
- `deckbuilder.html`: graphic deck builder (Mech → Mothership → Commander → Spec Parts → Main Deck → Energy Deck → Review & Export).
- `cards.json`: **the card catalog** (both pages read it).
- `cards/`: card images.

## Publish on GitHub Pages (free)
1. Create a public GitHub repository, e.g. `mechbattle`.
2. **Add file → Upload files**: drag in everything from this folder (including `cards/`), then **Commit**.
3. **Settings → Pages → Deploy from a branch → `main` / `(root)` → Save**.
4. Your site is at `https://<your-user>.github.io/mechbattle/`.

## The card catalog (`cards.json`)
One entry per card, keyed by exact card name:
```json
"Plasma Cannon Mk. II": { "type": "part" },
"Falcão Alpha": { "type": "mech", "image": "falcao.webp" }
```
- `type`: `mech`, `mothership`, `commander`, `spec`, `part`, `action` or `energy`.
- The deck builder shows each step's cards from this file. Replace the examples with your real cards.
- Only `part` cards get the Energized counter in the game.

## Images
- One file per card in `cards/`, WebP, about 400-600 px wide.
- Default file name = card name as a slug: lowercase, accents removed, each run of characters other than a-z and 0-9 becomes one `-`, none at the start or end. `Plasma Cannon Mk. II` → `cards/plasma-cannon-mk-ii.webp`.
- Use `"image"` in `cards.json` to override a file name. Cards without an image show as text.

## Decks
- In the builder, finish at **Review & Export**: copy the list, download it, or **Save locally**.
- Saved decks live in this browser's storage. `play.html` offers them in a drop-down on its first screen, so you don't need to copy and paste.
- Rules used by the builder: Spec Parts max 1 copy each, Main Deck max 3 copies each, Energy Deck up to 10 copies of a card. Change them in the `ST` list at the top of the script in `deckbuilder.html`.

## Rooms
Rooms use the free public PeerJS signaling server (loaded from unpkg). It only helps browsers find each other; game data goes directly between them. To avoid unpkg, download `peerjs.min.js` 1.5.4 into the repo and point the `<script src>` in `play.html` at it.
