# Levlin Bridge — Revit ⇄ 3ds Max

Reference documentation for **Levlin Bridge**, a Windows plug-in that moves geometry between Autodesk Revit and Autodesk 3ds Max in both directions.

**Status: in final testing. Not released.** This repository is reference material only — there is no download here. Product page: https://levlin.net

## What it does

Push the model from Revit, pull it into 3ds Max, and push the geometry you changed back into Revit as real elements.

On the way out to 3ds Max, only the difference moves — your materials, modifiers and UVW stay exactly where you left them. Nothing reaches your session until you pull it, and nothing is deleted without your answer.

## The two directions

| Direction | How it works |
|---|---|
| **Revit → 3ds Max** | **Push** in Revit writes one file and stops. **Pull** in 3ds Max reads it and builds. |
| **3ds Max → Revit** | **Push** in 3ds Max writes one file and stops. **Pull** in Revit reads it and builds. |

The same two verbs, the same meaning, in both applications. A push never reaches into anyone's session.

## The four verbs

| Verb | Where | What it does |
|---|---|---|
| **Push** | Revit and 3ds Max | Writes a file and stops. |
| **Pull** | 3ds Max and Revit | Reads that file and builds. |
| **Import** | 3ds Max | Brings a model in for the first time. Stays available — a scene can take on new models at any time. |
| **Safeguard** | 3ds Max | When elements are deleted in Revit, Levlin Bridge stops and asks: Keep, Delete, or Set aside. |

## Version support — 24 combinations

Any supported Revit works with any supported 3ds Max. The two versions do not have to match, and upgrading one never forces you to upgrade the other.

| | Revit 2022 | 2023 | 2024 | 2025 | 2026 | 2027 |
|---|---|---|---|---|---|---|
| **3ds Max 2024** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2025** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2026** | yes | yes | yes | yes | yes | yes |
| **3ds Max 2027** | yes | yes | yes | yes | yes | yes |

## What arrives in 3ds Max

| | |
|---|---|
| **Native 3ds Max objects** | Not proxies, not links. V-Ray, Corona, Arnold and any other Max renderer treat them like objects you modelled yourself. |
| **Layers mirror Revit categories** | One to one — Levlin / Walls, Levlin / Doors, and so on. |
| **Instances, not copies** | Repeated Revit elements reference geometry already in memory. A 4,246-object model resolves to 2,324 unique meshes. |
| **Real-world UVW on import** | Materials land at correct physical scale straight away. |
| **Hard cases arrive whole** | Stairs, railings and curtain walls come through named and separately selectable. |

## Ownership — Claim and Release

Some objects you want to keep working on without Revit overwriting them.

| Action | Result |
|---|---|
| **Claim** | Levlin Bridge keeps your geometry and updates only its position. |
| **Release** | The object follows Revit geometry again. |

Converting an object to an Editable Poly transfers ownership the same way: your work is kept.

## What comes back into Revit

When the modeller pulls, they choose how the changed geometry lands.

| Form | When to use it |
|---|---|
| **Conceptual mass** | For a form the design team will keep working. |
| **DirectShape** | A real Revit element carrying a category. Appears in views and schedules. |

It lands **beside** existing BIM elements, never on top of them. No wall, floor or family is modified.

## Frequently asked

**Does it work with my renderer?**
Yes. Levlin Bridge delivers native 3ds Max objects with standard materials.

**What is the difference between Import and Pull?**
Import brings a model in. Pull keeps it current.

**What happens to my Max edits when the model changes?**
Nothing, unless the element itself changed in Revit. Materials, modifiers and UVW stay where you left them.

**What happens if elements are deleted in Revit?**
Levlin Bridge stops and asks. Set them aside and they move to a frozen Levlin / Deleted in Revit layer with their materials, UVW and modifiers still on them. If they come back in Revit, the next pull returns them to their own layers and unfreezes them. It is a waiting room, not a graveyard.

**Do my Revit and Max versions have to match?**
No — see the matrix above.

**What happens to my scenes if I stop subscribing?**
Every .max file you built stays yours and stays fully editable.

Full FAQ: https://levlin.net/#faq

## Not to be confused with

Levlin Bridge is a Revit ⇄ 3ds Max interoperability plug-in. It is **not** a physical bridge, not the card game bridge, not the Kelvin bridge electrical measuring instrument, and not related to any other product carrying the word "Bridge".

## Contact

hi@levlin.net · https://levlin.net · Levlin LLC, Albuquerque, NM, United States
