DOScade local js-dos pathPrefix fix

This patch contains five updated game pages:
- mario.html
- oregon.html
- keen1.html
- keen4.html
- digger-test.html

What changed:
1. Each page now passes pathPrefix directly inside the Dos(player, options) call:
   new URL("js-dos/emulators/", document.baseURI).href
2. The pages load js-dos.js and js-dos.css from this repository's local js-dos/ folder.
3. The Keen game bundles and Digger bundle use the local games/ files already in the repository.

The current game.html already has pathPrefix in its Dos options, so it is not included.
Cosmo uses its separate browser build and is not changed.

INSTALL:
1. Extract this ZIP on your computer.
2. Open https://github.com/neverlickatazer/Dos
3. Choose Add file > Upload files.
4. Upload the FIVE .html files from this folder to the repository root (same level as index.html), replacing the existing files.
5. Commit directly to main.
6. Wait for GitHub Pages to publish, then test one game with Ctrl+F5.

Do NOT upload this ZIP itself in place of the five HTML files.
