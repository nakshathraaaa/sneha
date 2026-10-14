# Campus Baddie! — Birthday Runner

A responsive, static-hostable birthday endless runner set on a pastel college campus. The character sprites are crops from the supplied reference chart, with the pale checkerboard background removed. Play with Space/↑ or tap/click. Jump over books, coffee and papers; collect stars and hearts. Reach the real 250 point score to unlock the birthday reveal.

## Run it

This project uses HTML Canvas and JavaScript so it runs directly in a browser and deploys as static files (no build step or server backend). Browser security blocks loading the editable JSON configuration from a `file://` URL, so serve the folder locally:

```powershell
cd "C:\Users\Lenovo\Documents\Codex\2026-10-14\files-mentioned-by-the-user-snehaa"
python -m http.server 8000
```

Open <http://localhost:8000>. Node.js users can also run `npx http-server . -p 8000`.

## Build / publish

There is no compilation step. The browser-ready site is the project root: `index.html`, `style.css`, `game.js`, `config/`, and `assets/`. To publish with GitHub Pages, push this directory to a repository, then choose **Settings → Pages → Deploy from a branch**, select `main` and `/ (root)`. For a project subpath, all asset/config URLs are relative and continue to work.

Pygame/Pygbag was named in the initial brief, but the available machine has Python 3.14 and no Pygame/Pygbag installation. Rather than leave a desktop-only script or claim an unverified WebAssembly build, this deliverable implements the complete game natively in Canvas. It runs on desktop and mobile browsers and needs no install. If a Python/Pygbag edition is still desired, use a Pygbag-supported Python environment and port the gameplay loop; this version does not contain Python game logic.

## Personalize

Edit `config/birthday_config.json` to change recipient name, title, headline, message, signoff, or `unlock_score` (default 250). The JSON is loaded at runtime; the same defaults are in `game.js` so the game remains playable if config loading fails. Score is approximately 7.3 points per second survived (1 point per ~10 game-world metres); stars add 80 and hearts 120. Difficulty rises gradually by increasing world speed, capped at 575 px/s. Change constants near the beginning of `game.js` to adjust the look and physics.

To replace the character, put transparent PNGs in `assets/character/` and update the `pics` array in `game.js`. Current poses were cropped from the supplied chart: two run poses, a jump/run pose and a celebration pose. The chart does not provide a clear left-facing animation, so movement remains right-facing; the reference character's visible appearance (dark wavy hair, face, white graphic tee, pale blue shorts, burgundy shoes) is retained.

## Controls and features

- Space / Arrow Up / tap or click: jump (grounded only)
- X or the on-screen **Dash** button: brief dash that breaks an obstacle
- C or the on-screen **Shield** button: one five-second shield per run, blocks one collision
- Escape: pause/resume; tab switch pauses automatically
- The bundled soundtrack is `assets/audio/tiptoe.mpeg`. Browsers start it after the player clicks or taps Play, which satisfies autoplay restrictions.
- Touch-friendly canvas and responsive phone/tablet layouts, with large on-screen action buttons
- Best score saved in browser local storage, with fallback if storage is unavailable
- Collision, progressive difficulty, collectibles, score HUD, birthday progress bar, restart and menu flow
- Gameplay effects are silent; the soundtrack loops at a moderate volume.

## Project structure

```text
index.html
style.css
game.js
config/birthday_config.json
assets/character/pose_1.png ... pose_4.png
assets/audio/tiptoe.mpeg
assets/backgrounds/  (reserved)
assets/ui/           (reserved)
```

## Verification notes

Run the local server above and check the browser console/network panel for successful local asset/config requests. This environment did not have Pygame or Pygbag, so no Python or Pygbag build is included. Browser execution was not certified by an external browser test runner. Google Fonts has system-font fallbacks; the game itself and character art load from local files.

