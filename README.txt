# DOScade local js-dos patch

This patch changes the two supplied game pages to load the js-dos player from your own GitHub Pages repository instead of `v8.js-dos.com`.

## Important: the emulator files are not included in this patch

The HTML files are ready to use, but a working local installation also needs the official js-dos v8 distribution files. I have not fabricated or substituted those compiled files. Keep the full distribution together in the `js-dos` folder, including its `emulators` assets (worker scripts and WebAssembly files). The js-dos documentation explains that the player and emulator deployment files are separate parts of the browser installation:
https://js-dos.com/emulators.html

The official getting-started guide says the player can be installed from the releases page or through npm:
https://js-dos.com/dos-api.html
Official source/releases:
https://github.com/caiiiycuk/js-dos/releases

## Repository layout

After adding the official distribution, your repository should look like this:

    index.html
    game.html
    digger-test.html
    js-dos/
      js-dos.js
      js-dos.css
      emulators/
        (all emulator worker, wasm, and supporting files from the matching v8 distribution)
    games/
      noahs-ark.jsdos
      chex-quest.jsdos
      mario-letters.jsdos
      ...

Do not upload only `js-dos.js` and `js-dos.css`; the emulator's worker/WASM files are also required. Keep all files from one matching js-dos release together.

## Apply the patch

1. Back up your current `game.html` and `digger-test.html`.
2. Replace those two files with the matching files in this patch.
3. Add the complete official js-dos v8 browser distribution under the repository's `js-dos/` folder, preserving its internal paths.
4. Commit and push the changes to GitHub Pages.
5. Test `game.html?game=noah`, `game.html?game=chex`, and `digger-test.html`.

## What this patch deliberately leaves alone

- `index.html` and its eight game links
- the Cosmo game page and its current working setup
- your game bundle files

## One remaining external dependency

The shared `game.html` still loads JSZip from jsDelivr because it uses JSZip to unpack your locally stored game bundles before passing their files to js-dos. This is separate from the js-dos player itself. If your network also blocks jsDelivr, JSZip should be copied locally too and its script tag changed to a local path.

The Digger demo bundle URL remains on the js-dos host in `digger-test.html`; it is only a test page and does not affect the four locally stored bundles in `game.html`. Once the local player is confirmed working, we can move that Digger bundle into your repository as well.
