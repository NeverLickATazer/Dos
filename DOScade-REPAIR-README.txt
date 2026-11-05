DOScade repair package — local js-dos hosting

WHAT THIS FIXES
- Every DOS game page now loads js-dos from this repository instead of
  requesting the player from v8.js-dos.com.
- Worker/WebAssembly requests are directed to js-dos/emulators/.
- JSZip is loaded locally instead of from jsDelivr.
- Digger's game bundle is copied into games/digger.jsdos by the setup workflow.
- Commander Keen 1 and 4 use the game bundles already stored in games/.

IMPORTANT
The ZIP does not contain compiled js-dos runtime files. Those files are generated
from the official npm packages by the included GitHub Actions workflow. They
must not be replaced with placeholder files: js-dos needs its matching worker
and WebAssembly assets.

HOW TO APPLY
1. Back up your current GitHub repository.
2. Extract this ZIP and replace the contents of your repository with the files
   in the Dos-main folder. Keep the repository's existing GitHub Pages settings.
3. Push the updated files to the same GitHub repository/branch.
4. In GitHub, open the repository's Actions tab.
5. Select "Install local js-dos runtime" and click "Run workflow".
6. Wait for the workflow to finish successfully. It will add the official
   js-dos files, emulator assets, local JSZip, and Digger bundle to the repo.
7. Wait for GitHub Pages to publish, then test each game from the home page.

WHAT IS PRESERVED
- The existing homepage and its eight game links.
- The working Cosmo page and its files.
- Existing game bundles and game-specific settings.
- The Commander Keen keyboard controls.

TROUBLESHOOTING
- If the workflow fails at the copy step, open the workflow log. It means the
  upstream npm package layout changed and the copy paths need adjustment.
- If the workflow fails while downloading Digger, the upstream Digger bundle
  host was unavailable to the GitHub runner at that time.
- Do not copy only js-dos.js and js-dos.css. The complete emulators folder is
  required for the workers and WebAssembly modules.

The local-runtime approach follows the js-dos deployment guidance: the browser
player can be downloaded from the official releases/npm package, and the
emulators pathPrefix must point to the matching emulator deployment files.
