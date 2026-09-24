# FreeCAD cheatsheet for Pi Crust

For FreeCAD 1.1.3 on Fedora. Menus show the shortcuts configured in your installation; those take precedence over this sheet. Keyboard focus matters: click the 3D view before using view shortcuts.

## Everyday controls

| Key | Action |
| --- | --- |
| Ctrl+S | Save |
| Ctrl+Z / Ctrl+Y | Undo / redo |
| F5 | Recompute/refresh the document |
| Space | Toggle visibility of selected objects |
| F2 | Rename the selected tree item |
| Delete | Delete the selection; check what is selected first |
| Esc | Exit the active drawing tool or cancel the current operation |
| Ctrl+click | Select additional objects, edges, or vertices |
| V, then F | Fit the model in the view; press sequentially |
| 0 | Axonometric view |
| 1 / 2 / 3 | Front / top / right view |
| 4 / 5 / 6 | Rear / bottom / left view |

Earlier conversation advice gave Ctrl+R for recompute and mixed up several view keys. The table above corrects those defaults. Sources: [Refresh](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_Refresh.md), [front](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewFront.md), [top](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewTop.md), [right](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewRight.md), [rear](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewRear.md), [bottom](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewBottom.md), [left](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Std_ViewLeft.md).

If an object does not update, try F5. To force a refresh, right-click the document in the tree, choose **Mark to recompute**, then press F5. Check for errors if values still stay unchanged.

## Mouse: CAD navigation style

Choose **Navigation styles → CAD** from the 3D-view context menu if needed.

| Gesture | Action |
| --- | --- |
| Scroll wheel | Zoom |
| Hold middle button and drag | Pan |
| Hold middle button, then also left or right button and drag | Rotate |
| Left-click | Select |
| Click empty space | Clear selection |
| Double-click a sketch in the tree | Enter sketch editing |

Navigation gestures differ in other styles. See [FreeCAD mouse navigation](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Mouse_navigation.md).

## Enter formulas quickly

1. Select the object and open its **Data** properties.
2. Double-click the numeric value you want to control.
3. Press **=** to open its expression editor, or click the **f(x)** expression button.
4. Enter the expression and confirm. In the expression editor, omit the leading equals sign.

For example, an existing sheet alias can drive a panel thickness with `<<Parameters>>.PlywoodThickness`. Include units for added distances: `+ 1 mm`, not `+ 1`. Spreadsheet formula cells themselves use a leading `=`; the property expression dialog does not.

If a property displays an ellipsis button instead, try its right-click **Expression…** command. To return to a fixed value, remove its binding in the expression editor, then enter the value. See [FreeCAD expressions](https://github.com/FreeCAD/FreeCAD-documentation/blob/main/wiki/Expressions.md).

## Placement without surprises

- **Placement → Position → x/y/z** moves an object.
- **Placement → Axis → x/y/z** specifies the rotation axis, not its location. `(1, 0, 0)` means rotate around X.
- **Placement → Angle** sets the amount of rotation.
- In our enclosure: X is left-to-right, Y is front-to-back, Z is upward.
- A cube's Length/Width/Height follow its local X/Y/Z directions. Rotating the cube rotates those directions too.
- A cylinder's Radius is half its diameter. Its Height follows its local Z axis; rotate that axis to make a horizontal drilling tool.

## Sketcher essentials

- Open the sketch by double-clicking it; selecting it once only shows object properties.
- A continuous polyline joins consecutive segments. Close it by making the last endpoint coincident with the first.
- **Horizontal / Vertical** sets alignment and does not ask for a dimension.
- **Horizontal distance / Vertical distance** sets a measurement and opens a value dialog.
- **Coincident** keeps endpoints together. **Point-on-object** allows sliding along the selected line.
- Degrees of freedom count remaining independent movements. Fully constrained means geometry is fixed by its constraints; it does not certify manufacturability.
- To anchor a corner, select its point, Ctrl-select the origin, then use **Constrain coincident**.
- If constraints are redundant, clear selection and remove only the specific redundant constraint. Numbers change after deletion; re-read the solver message each time.

## Boolean cuts and reusable parts

- Select the material object first, then Ctrl-select the cutting tool; use **Part → Boolean → Cut**.
- Extend a cutter a little beyond both panel faces. Only the overlapping material is removed.
- Expand a Cut in the tree to edit its original panel and tool. Originals are normally hidden; Space toggles visibility.
- To undo a recent cut, use Ctrl+Z. To remove an older Cut, delete the result while retaining its inputs when prompted, then show the original panel.
- To make a linked copy, Alt-drag an object onto the document name and release. A link reuses the source shape. Give it its own placement when positioning the other side.
- To check whether something is actually nested, collapse the apparent parent; indentation alone can mislead.

## Before saving for review

Recompute with F5, check visible errors, hide cutters/originals that should not be displayed, and save with Ctrl+S. Review the saved file again before committing: changes made in the GUI may not have been discussed yet.
