# Layers and object identity — Levlin Bridge

How a Revit model is organised once it arrives in Autodesk 3ds Max: what the layers are called, what an object is, and what stays attached to it across revisions.

**Status: in final testing. Not released.** This page is reference material only — there is no download here. Product page: https://levlin.net

## Layers mirror Revit categories

Every object arrives on a layer named after the Revit category it came from, prefixed with `Levlin /`. The mapping is one to one — there is no grouping decision to configure and no preset to choose.

| Revit category | 3ds Max layer |
|---|---|
| Walls | Levlin / Walls |
| Floors | Levlin / Floors |
| Doors | Levlin / Doors |
| Windows | Levlin / Windows |
| Curtain Walls | Levlin / Curtain Walls |
| Stairs | Levlin / Stairs |
| Railings | Levlin / Railings |
| Furniture | Levlin / Furniture |

The pattern continues for every other category present in the model. One further layer, `Levlin / Deleted in Revit`, is created only when it is needed — see the Safeguard reference.

## What an object is

Objects arrive as native 3ds Max geometry. Not proxies, not links, not a single merged mesh.

| | |
|---|---|
| **Native** | Editable in 3ds Max like anything you modelled yourself. |
| **Named** | Each object carries its own name, not a generated index. |
| **Separately selectable** | Selecting one wall selects one wall. |
| **Multi-material where the source is** | An element made of several Revit materials arrives carrying all of them, not fused into one shell. |

This is the difference that decides the rest. When geometry is grouped by material on the way in, element identity is destroyed, and every revision afterwards has to guess which piece is which. Levlin Bridge keeps the element as the unit, so a revision can be matched to the exact object it belongs to.

## Instances, not copies

Repeated elements reference geometry that is already in memory rather than duplicating it.

On a representative model, 4,246 objects resolve to 2,324 unique meshes. The remaining objects are instances. Scene weight tracks unique geometry, not object count.

## Real-world UVW on import

Materials land at correct physical scale on arrival. This applies both to materials that come across from Revit and to any 3ds Max material you swap in afterwards.

Two cases sit outside that default:

| Case | Why | What to do |
|---|---|---|
| **Scanned materials** | They carry their own scale conventions. | They still need an artist's pass. |
| **Very large surfaces** | Real-world mapping does not suit a multi-kilometre terrain. | Bring that piece in as its own model. |

## What survives a revision

Nothing in your scene changes unless the element itself changed in Revit. Materials, modifiers and UVW stay exactly where you left them on every element whose source geometry did not move.

This is a consequence of the identity rule above, not a setting. Because the element is still the same object, the work attached to it has somewhere to stay.

## Claim and Release — taking an object off the leash

Sometimes you want an object to stop following Revit geometry entirely.

| Action | Result |
|---|---|
| **Claim** | Levlin Bridge keeps your geometry and updates only its position. |
| **Release** | The object follows Revit geometry again. |

Converting an object to an Editable Poly transfers ownership the same way. Your work is kept rather than overwritten on the next pull.

## More than one model in the same scene

A 3ds Max scene can hold several Revit models at once — the site model, the structural model, the building next door.

Each is imported once and kept current by Pull. Each sits on its own Levlin layers. None of them is rebuilt when another changes. The only thing Levlin Bridge refuses is importing the same model twice.

## See also

The Safeguard reference covers what happens to layers and objects when elements are deleted in Revit. The version matrix covers which Revit and 3ds Max releases are supported.

Contact: hi@levlin.net
