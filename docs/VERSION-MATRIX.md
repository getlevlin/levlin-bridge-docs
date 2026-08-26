# Version support — Levlin Bridge

Which Autodesk Revit and Autodesk 3ds Max releases Levlin Bridge supports, and what happens when the two do not match.

**Status: in final testing. Not released.** This page is reference material only — there is no download here. Product page: https://levlin.net

## The rule

Any supported Revit works with any supported 3ds Max. The two versions do not have to match, and upgrading one never forces you to upgrade the other.

This matters because the two versions are usually decided by different people. The Revit release is fixed by the client or the BIM standard on the project. The 3ds Max release is fixed by the plug-ins the visualisation team depends on. Levlin Bridge does not require those two decisions to agree.

## The 24 combinations

| | Revit 2022 | Revit 2023 | Revit 2024 | Revit 2025 | Revit 2026 | Revit 2027 |
|---|---|---|---|---|---|---|
| **3ds Max 2024** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2025** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2026** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2027** | yes | yes | yes | yes | yes | yes |

Six Revit releases across four 3ds Max releases. All 24 combinations are supported.

## Why the version freedom costs nothing here

The other route that gives you this freedom is a full FBX re-export. It works, but it rebuilds the receiving scene from scratch every time, so the materials, modifiers and UVW work done in 3ds Max is lost on each revision.

Levlin Bridge gives the same version freedom without that cost. On the way out to 3ds Max only the difference moves, so the scene is updated rather than replaced, and the work that is already in it survives.

## Upgrading mid-project

| Situation | Result |
|---|---|
| The BIM team upgrades Revit mid-project | The 3ds Max scene keeps working. No re-import, no rebuild. |
| The visualisation team upgrades 3ds Max | The Revit side is unaffected. |
| Both upgrade, at different times | Still supported — any combination in the table above is valid. |

## Platform

| | |
|---|---|
| **Windows 11** | Full functionality, with native title-bar theming and dark-theme dialogs. |
| **Windows 10** | Full functionality. |

Levlin Bridge is a Windows plug-in. There is no macOS or Linux build, because Revit itself is Windows-only.

## Renderers

Levlin Bridge delivers native 3ds Max objects carrying standard materials. It does not install a renderer, does not replace one, and does not touch your render setup.

V-Ray, Corona, Arnold, Redshift and any other 3ds Max renderer treat the arriving geometry exactly as they treat objects you modelled yourself.

## Seats and updates

| | |
|---|---|
| **One seat, two machines** | A desktop and a laptop on the same seat. |
| **Updates** | Continuous, tracking each new Revit and 3ds Max release as it ships. |

## If your version is not listed

Revit releases older than 2022 and 3ds Max releases older than 2024 are not supported. Write to hi@levlin.net with the versions you are on and we will tell you plainly whether that is likely to change.

## See also

The full reference index is in the repository README. The product page is https://levlin.net

Contact: hi@levlin.net
