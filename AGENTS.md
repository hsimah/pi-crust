# Working on Pi Crust

## Learning preferences

- The owner is learning FreeCAD and has little woodworking or mechanical-design experience.
- Prefer short, concrete GUI instructions with the exact object, property, and expected result. Explain why a step matters in plain language.
- Let the owner try modeling independently, then review the saved result when asked. Do not take over CAD editing or generate replacement models unless requested.
- Treat questions about capabilities as questions, not automatic authorization to implement them. In particular, do not create parameter exports or synchronization tools unless explicitly requested.
- Keep momentum toward a practical first build. Avoid adding unnecessary features or seeking perfection.
- If screenshots are ambiguous, say so. Do not confidently infer constraints or object relationships from appearance alone.

## Review before every commit

The owner may change the model without showing the assistant. Never rely solely on an earlier screenshot or review.

1. Inspect the current Git status and diff, including staged files. Stage only files relevant to the request.
2. Re-read the latest saved `PiCrust.FCStd` before committing CAD, or pushing a CAD revision not yet reviewed. Compare the saved state with the intended design and the prior commit.
3. Check dimensions, units, aliases, expressions, placements, Boolean dependencies, linked objects, and recompute/error flags. Check that matching components agree and removable panels have clearance.
4. An FCStd is a ZIP archive: read `Document.xml` for a non-mutating inspection. This does not replace a FreeCAD recompute, visual inspection, or solid/interference validation. State the limits of the checks actually performed.
5. Do not silently repair or overwrite the owner's CAD. Explain unexpected changes and offer precise GUI corrections. Known unfinished design work can be committed as a clearly documented work in progress.
6. Review documentation against the saved model. Do not describe proposed changes as already implemented.
7. Verify the staged diff before committing and report the commit. Push only when requested; never force-push as a routine action.

Do not commit reference photos, screenshots, or FreeCAD backup files unless requested. The CAD file contains only saved work; unsaved GUI edits are not visible to Git.

## Project decisions and lessons

- FreeCAD 1.1.3, installed as a Flatpak on Fedora. The user sometimes says FastCAD but means FreeCAD.
- F5 is refresh/recompute in this installation; earlier Ctrl+R advice was wrong. See `FREECAD_CHEATSHEET.md` for corrected view keys as well.
- Fixed early-1990s all-in-one desktop style: horizontal keyboard deck and backward-leaning screen, plywood panels, removable back.
- Retain the working internal Anker 100W charger and cables. One intact extension cord exits the back. No replacement USB-C input electronics are planned.
- Display buttons remain internal. No speakers, extra display, or camera are requested.
- The owner plans tape/Velcro mounts for the screen, Pi, and charger, and Velcro cable management. Hardware fit, suitable attachment surfaces, ventilation, and cord restraint still need checking.
- Keyboard housing should be concealed under the deck with the keys exposed. Outside housing is approximately 290 x 100 mm; the keycap envelope is inferred from about 2 mm inset per edge, not a verified cutting dimension.
- Keep design inputs in the existing FreeCAD spreadsheet. Do not globally scale component dimensions, screw sizes, or plywood thickness.
- Distinguish Position x/y/z from rotation Axis x/y/z; horizontal/vertical alignment from distance constraints; coincidence from point-on-object; radius from diameter.
- Current design status and outstanding work are in `README.md`.
