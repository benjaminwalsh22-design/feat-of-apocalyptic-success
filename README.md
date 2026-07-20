# The Feat of Apocalyptic Success — Web Edition

An installable web game for an advanced young learner. Rebuild a ruined world
one **Feat** at a time by solving logic puzzles that stretch spatial reasoning
and planning — wrapped in a bold "explorer at dusk" adventure. This build has **three** fully playable Feats — **"Claim the Castle"**
(power-routing), **"Light the Beacon"** (block coding), and **"Purify the Well"**
(fractions & ratios) — plus the world-map, salvage, and adaptive-difficulty shell
the remaining Feats will slot into.

**Art direction — "Solarpunk meets Scavenger Sci-Fi."** A reclaimed, colorful
post-apocalypse rather than a gloomy wasteland: weathered metal panels, glowing
clean-energy conduits with animated current, a plasma reactor core, reclaimed
radio-relay spires, and neon-accented UI. The home screen is an illustrated,
scrollable **Overworld** — outposts strung along a glowing energy conduit that
lights up as you reclaim each region. All icons are custom vector art (no emoji),
and buttons are tactile terminal keycaps. Tuned for high readability for ages
8–12.

No Mac, no Xcode, no app store, no cost. You host these files on GitHub Pages and
add the page to her iPad/iPhone home screen — after that it launches full-screen
from an icon and works offline, just like a native app.

## Files

```
index.html              the whole game (logic + art + UI in one file)
manifest.webmanifest    makes it installable as an app
sw.js                   service worker → loads instantly, works offline
icon-180 / 192 / 512    app icons (home screen + splash)
.nojekyll               tells GitHub Pages to serve the files as-is
```

---

## Deploy it on GitHub Pages (about 5 minutes, free)

1. **Make a free account** at https://github.com if you don't have one.
2. Click **New repository** (the green button). Name it something like
   `feat-of-apocalyptic-success`, set it to **Public**, and click
   **Create repository**.
3. On the new repo page, click **uploading an existing file**. Drag in **all**
   the files from this folder (`index.html`, `manifest.webmanifest`, `sw.js`,
   and every `icon-*.png`, plus `.nojekyll`). Click **Commit changes**.
4. Go to **Settings → Pages** (left sidebar).
5. Under **Build and deployment → Source**, choose **Deploy from a branch**.
   Set the branch to **main** and the folder to **/ (root)**. Click **Save**.
6. Wait ~1 minute, then refresh. GitHub shows your live link near the top:
   **`https://YOUR-USERNAME.github.io/feat-of-apocalyptic-success/`**

That link is the game. Open it anywhere.

## Put it on her home screen (so it runs like an app)

On her iPad or iPhone:

1. Open the GitHub Pages link **in Safari** (this part must be Safari).
2. Tap the **Share** button (the square with an up-arrow).
3. Scroll down and tap **Add to Home Screen**, then **Add**.
4. A castle icon appears on her home screen. Tapping it launches the game
   **full-screen with no browser bars** — and it works even with no internet.

To update the game later, just re-upload a changed `index.html` to the repo
(and bump `CACHE = 'foas-v1'` in `sw.js` to `foas-v2` so devices pull the new
version). Her saved progress stays on the device.

---

## How to play

**Claim the Castle** — Tap pipe tiles to rotate them and route power from the
**⚡ reactor** to every **🏰 tower**. **Reset** restarts the same puzzle, **Hint**
fixes one pipe, **New** deals a fresh board.

**Light the Beacon** — Build a little *program* to fly the drone to the
**📡 beacon**, collecting every **💎 power cell**. Tap blocks to add them:
**Forward**, **Turn Left/Right**, **Repeat** (a loop — tap inside it to fill its
body, use −/+ to set how many times), and, at higher levels, **If Path Ahead** (a
conditional). Press **▶ Run** to watch the drone follow the program; if it bumps a
wall it just resets so she can tweak and try again. The clever trick to discover:
`Repeat { If Path Ahead: Forward }` glides to a wall without having to count steps
— real loops-and-conditionals thinking.

**Purify the Well** — Mix the cleansing formula by filling reagent tanks to match
a target **fraction** ("fill the vat to 3/4") or **ratio** ("3 parts Purifier to
1 part Spring Water — make 8 units"). A live readout shows the current mix
*reduced to lowest terms*, so she practices equivalent fractions and scaling a
ratio to a total. Correct mix → the spring runs clean.

All Feats have no lives, no timers, and no way to lose, and each has its own
adaptive challenge level that rises automatically the faster and cleaner she
solves. Claiming a Feat earns salvage and unlocks the next one on the map.

## Under the hood

Everything runs client-side in one HTML file: the puzzle logic, an HTML5 Canvas
renderer, pointer/touch input, adaptive difficulty, and progress saved to the
device via `localStorage`. The puzzle generator is procedural and was
stress-tested across **3,200 generated boards on all 8 difficulty levels** —
every one is solvable, always has pipes to turn, and never starts already
finished.

## What's next

Three Feats down. The map still lists *Crack the Vault* (deduction) and
*Rebuild the Bridge* (balance-algebra) — each a new puzzle module that reuses
this same map, salvage, and difficulty plumbing.
