# Safeguard — what happens when elements are deleted in Revit

Deletion is the one operation Levlin Bridge will never decide on its own.

**Status: in final testing. Not released.** This page is reference material only — there is no download here. Product page: https://levlin.net

## The problem it exists for

Every link-based route into 3ds Max has the same failure mode. The model changes, the link reloads, and geometry disappears from the scene with no way back. Whatever was attached to that geometry — materials, modifiers, UVW — goes with it.

The loss is silent. Nothing asked, nothing logged, and by the time it is noticed the work is gone.

## What Levlin Bridge does instead

When a pull finds that elements were removed in Revit, it stops before touching your scene and reports what it found.

Nothing has changed in 3ds Max at that point. This step never runs automatically, and there is no setting that makes it run automatically.

## The three answers

| Answer | What happens |
|---|---|
| **Keep** | The objects stay exactly where they are, on their own layers, untouched. Revit no longer has them; your scene still does. |
| **Delete** | The objects are removed. This happens only because you said so. |
| **Set aside** | The objects move to a frozen layer named `Levlin / Deleted in Revit`, still carrying their materials, UVW and modifiers. |

## Set aside, in detail

Set aside is the answer to reach for when you are not sure yet.

| | |
|---|---|
| **Where they go** | A single frozen layer, `Levlin / Deleted in Revit`. |
| **What comes with them** | Materials, UVW and modifiers, still attached to the objects. |
| **Visible?** | Yes. Named, listed in the Layer Manager, and counted. |
| **Reversible?** | At any time. |

It is a waiting room, not a graveyard. The objects are parked, not degraded.

## If the element comes back in Revit

Design decisions get reversed. When an element that was set aside returns in Revit, the next pull returns the object too — to its own category layer, unfrozen, with the work still on it.

You do not re-import, re-assign materials, or rebuild the modifier stack. The object goes back to where it was.

## What Safeguard does not do

| | |
|---|---|
| **It does not run silently** | There is no automatic mode. |
| **It does not touch elements that were not deleted** | The rest of the pull behaves normally. |
| **It does not strip the objects** | Nothing is flattened, collapsed or unassigned on the way to the frozen layer. |

## Worked example

A revision removes 87 elements in Revit. On the next pull in 3ds Max, Levlin Bridge stops and reports that 87 elements were removed and that nothing has been changed yet.

Answering **Set aside** moves those 87 objects to `Levlin / Deleted in Revit`, frozen, with their materials and modifiers intact. The other layers are unaffected, and the rest of the revision applies as normal.

Two weeks later the design is reversed and the elements return in Revit. The next pull moves those 87 objects back to their own layers and unfreezes them. Nothing was rebuilt.

## See also

The layers reference explains how objects are named and organised, and what stays attached to them across revisions. The version matrix covers which Revit and 3ds Max releases are supported.

Contact: hi@levlin.net
