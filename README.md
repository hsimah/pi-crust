# pi-crust

A plywood Raspberry Pi cyberdeck enclosure designed parametrically in FreeCAD,
for third-party CNC routing or laser cutting and assembly at home.

## Files

- [PiCrust.FCStd](PiCrust.FCStd): editable FreeCAD model.
- [FREECAD_CHEATSHEET.md](FREECAD_CHEATSHEET.md): mouse controls, corrected shortcuts, formulas, and modeling tips.
- [AGENTS.md](AGENTS.md): learning preferences and review-before-commit instructions for assistants.

## Components

| Component | Identification | Still needed for CAD |
| --- | --- | --- |
| Computer | Raspberry Pi 3 B+ | Installed cooling/accessories, mounting height, required port access |
| Display kit | VSLCD K000332: M.NT68676.2A controller + 13.3-inch 1366×768, 40-pin LVDS LCD | Panel model label, outer dimensions, visible area offset, mounting features, cable routing |
| Display controller | M.NT68676.3 marking visible in screenshots; original listing says M.NT68676.2A | Board dimensions including connector overhangs, tallest components, mounting-hole positions |
| Display controls | Separate narrow button PCB connected by ribbon cable; configure before installing screen | Internal retention only; no external button access or cutouts |
| Keyboard | Royal Kludge RK61 | Housing measured about 290 × 100 mm; verify key travel, mounting height, and cable clearance |
| Power supply | Existing Anker 100W, three ports, smart display (user description); retain working setup | Body dimensions, space with extension-cord socket and USB plugs connected, mounting and ventilation |

Display listing: [VSLCD K000332](https://www.vslcd.com/lcd-controller-board-m-nt68676-2a-13-3-1366x768-lvds-40pin-lcd-screen.html).
Keyboard reference: [RK61 product page](https://rkgamingstore.com/products/rk61-60-percent-keyboard);
the user's variant has not yet been established.

Product identities above are user-provided except where screenshot evidence is noted. No fabrication dimensions are verified.
The display diagonal and resolution do not specify its physical outline or mounting.

## Parametric design intent

- Use millimetres and named FreeCAD spreadsheet parameters.
- Keep component dimensions, hole patterns, and connector sizes fixed when resizing the case.
- Drive panel geometry from component placement, internal clearances, and measured plywood thickness.
- Reserve space for plugged-in connectors, cable bends, ventilation, and assembly access.
- Choose joints and cutting compensation after selecting the fabrication process and supplier.
- Check the layout with paper templates and joint fit with a cut sample before ordering panels.

## Current model — reviewed 2026-09-23

This is a work-in-progress layout, not production-ready cutting geometry. The saved
model was inspected through its FCStd archive and Document.xml: archive integrity,
object records, expressions, placements, and Boolean references were reviewed.
No pending recompute/invalid object flags were present. This was not a live FreeCAD
recompute, solid-validity check, or complete interference test.

- Overall envelope: 350 × 300 × 272 mm, with nominal 6 mm plywood.
- Matching side panels, horizontal keyboard deck, front, sloping screen bezel,
  rear panel, and a top cap overlapping the side tops.
- Screen slope rises 200 mm over a 60 mm run: 208.806 mm long, tilted about
  16.699 degrees from vertical. Screen opening: 295 × 168 mm; verify against LCD.
- Rear panel: 337 × 259 × 6 mm, with 0.5 mm clearance around its perimeter.
- Four 20 mm mounting cubes meet the rear panel's inner face at Y = 294 mm.
  Their lower corners are X = 6 or 324 mm, Y = 274 mm, Z = 6 or 246 mm.
  Lower blocks meet the base; upper blocks meet the top cap. All four sizes and
  placements are driven by expressions. Left/right block labels refer to the rear view.
- Rear cord notch uses a 10 mm radius cylinder centered at X = 175, Z = 6 mm.
  It is approximately a 20 mm-wide semicircular exit, not a 10 mm-diameter hole.
- Keyboard cutout in the saved CAD is still 292 × 102 mm. The discussed change
  to 288 × 98 mm to conceal the housing has NOT been applied in this revision.
  That smaller opening is provisional: check a template and full key travel first.

## Assembly plan and remaining work

- Keep the existing working Anker charger inside, plugged into one intact extension
  cord exiting the rear. Cord outside diameter is approximately 8 mm.
- The back will be removable, secured with four screws into the mounting blocks;
  glue the blocks to the fixed enclosure, not to the back. Screw sizes, back clearance
  holes, and block pilot holes are not finalized or modeled yet.
- Fixed panel joints still need glue strips/blocks and assembly details. The cap
  avoids a bevel cut at the screen top; support the square-cut bezel internally.
- The owner plans double-sided tape/Velcro for the LCD, Pi, and charger, and Velcro
  cable management. Confirm suitable mounting surfaces, component/cable clearances,
  and access through the removable back before fixing everything in place.
- Conceal the keyboard housing below the deck with keys exposed. Add support rails
  or a shelf and verify the installation path and full key travel through 6 mm plywood.
- Add ventilation, protected cord-exit edges, and a cord restraint fixed to the base.
- Confirm actual plywood thickness, screen fit, required external Pi ports, and the
  cutting service's tolerances, minimum holes, and CNC corner-radius requirements.
- Export flat panel cutting files once those details are settled. No production
  cutting files exist yet. A CAD commit is a progress checkpoint, not cutting approval.

## Selected enclosure direction

An early-1990s-style all-in-one desktop, informed by the user's wooden cyberdeck
reference image. Fixed enclosure with a trapezoidal side profile, an angled screen
face, and a horizontal keyboard deck projecting in front. The top of the screen sits farther back than its bottom; the current tilt is
derived from the side profile.

The computer, display electronics, keyboard, and existing Anker adapter belong
inside the enclosure. Retain the user's working power setup. A single intact
extension cord exits the rear and plugs into the wall; its socket connects to
the Anker inside. Reserve room for that socket, the adapter, USB plugs, and cable
bends, with adapter ventilation and a restrained cord exit. The previous USB-C
input/replacement-supply proposal is superseded; no custom power board is planned.

The user reports a high-pitched noise when powering the display from the Pi's
USB-A port; its cause is not established. Screenshots show that the controller's
actual power input is a round barrel connector. The source-end cable electronics
and voltage rating cannot be identified from these photos. Preserve the working
cable rather than assume that its USB source connector establishes its output voltage.
The reference image's speakers, small auxiliary display, camera, and side knob
are not requested components.

Initial layout parameters should include screen tilt, keyboard deck height and
depth, screen bezel margins, electronics clearance, and plywood thickness.
Derive overall width from the larger of the screen assembly and keyboard envelopes
plus margins. Derive depth from the angled screen, keyboard, and internal component
envelopes. Keep component dimensions independent of enclosure proportions.
The rear panel is the removable service panel; fastening details remain to be completed.

## Screenshot review

Seven local PNG screenshots were inspected on 2026-09-22.

- `Screenshot from 2026-09-22 17-15-09.png`: overall hardware layout; keyboard
  retains its housing and the Pi has a transparent case.
- `Screenshot from 2026-09-22 17-15-23.png`: LCD edge and tape; panel thickness
  cannot be read confidently enough for a mounting design.
- `Screenshot from 2026-09-22 17-15-39.png`: Pi HDMI and micro-USB connections,
  controller HDMI and barrel power, separate display button board, Anker body.
- `Screenshot from 2026-09-22 17-15-45.png`: keyboard housing and cable exit;
  Anker mains prongs and connected USB cable.
- `Screenshot from 2026-09-22 17-15-52.png` and
  `Screenshot from 2026-09-22 17-15-56.png`: LCD tape measurements suggest an
  outline roughly 305 mm wide and 190 mm high. These are visual estimates only:
  tape alignment, perspective, and cropped endpoints prevent fabrication precision.
- `Screenshot from 2026-09-22 17-16-00.png`: controller clearly marked
  M.NT68676.3; mounting holes, connectors, LVDS harness, and button ribbon visible.

Model the LCD outline separately from the visible screen opening. Reserve room
behind it for the connector and harness. Controller mounting must account for
HDMI and barrel plugs projecting beyond the PCB. Retain the button board inside
without external access; configure the display before installation. Allow the
keyboard to be removed for service. Pi-case retention remains a
layout choice; do not assume bare-board dimensions describe the pictured assembly.

## First-build priorities

The user prioritizes getting a practical prototype built quickly over a fully
refined enclosure. Start with approximate component envelopes, generous internal
clearance, simple panels, and a removable service panel. Keep dimensions
parameterized so fit corrections are easy. Do not block the first layout on
precise component models, button spacing, or optional features. Verify fit-critical
dimensions (LCD opening/support, keyboard fit, material thickness, and joints)
before ordering cuts. There are no external display-control openings.
