# Campus Baddie! — Birthday Runner

A responsive, static-hostable birthday endless runner set on a pastel college campus. The character sprites are cropped from the supplied reference chart with the checkerboard background removed. Play with Space/↑ or tap/click. Jump over books, coffee and papers; collect stars and hearts. Reach 250 points to unlock the birthday reveal.

## Run locally

Serve the project folder with `python -m http.server 8000` and open http://localhost:8000.

## Deploy with GitHub Pages

This is a static site with no build step. In this repository, open Settings → Pages → Deploy from a branch, select `main` and `/(root)`, then save.

## Controls

- Space / Arrow Up / tap or click: jump
- X or on-screen Dash: brief obstacle-breaking dash
- C or on-screen Shield: one five-second shield per run
- Escape: pause/resume

Best score is stored locally in the browser. Birthday text and the 250-point unlock threshold are configurable in `config/birthday_config.json`.

Character sprites are in `assets/character/`. The sprite chart does not include a clear left-facing pose, so running sprites face right.

The original brief requested Pygame/Pygbag; this project uses Canvas/JavaScript for direct static browser deployment. No Pygame/Pygbag build is included.
