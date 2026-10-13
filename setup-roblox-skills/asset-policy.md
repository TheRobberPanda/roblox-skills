# Asset Policy

Seed for `docs/agents/assets.md`. Setup copies this file and fills in the chosen policy.

## Policy

**Mode:** Human-authored only

Claude and any MCP tool never create, draw, sculpt, generate, or edit game art. A human creates every asset in the project's authoring tool and imports it.

## Covered assets

- Character models
- Ball and other props
- All animations (dodge, throw, knock-out, stun, recovery, and so on)
- Textures and materials
- UI art and icons (AI-generated icons are the only exception, and each must be marked "to be remade by hand")
- Sounds and music (AI-generated music is a placeholder and must be replaced before release)
- Map parts and meshes

## What the agent may do

- Write scripts that use imported assets
- Set asset properties, attributes, and references
- Run release checks that find placeholders
- Search the Creator Store and run the security audit before any import

## Placeholder rule

An asset that hasn't been edited and renamed `_completed` is a placeholder. Release checks fail on any placeholder.

## Source of truth

Authoring files live in `assets/blockbench/` (or the folder this project chooses), grouped by category.
