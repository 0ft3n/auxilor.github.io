---
title: "How to make a custom reforge"
sidebar_position: 3
---

## Default Config

The default reforges.yml can be found here: 

[GitHub](https://github.com/Auxilor/Reforges/blob/master/eco-core/core-plugin/src/main/resources/reforges.yml)

## Breakdown of reforges.yml

reforges.yml is where the configs for all reforges are. It may initially seem daunting however it is very easy to configure and make your own reforges.

Simply, reforges.yml looks like this:

```yaml
reforges:
  - <reforge 1>
  - <reforge 2>
```

It's a big array of objects, each element in the list being a reforge. You can add and remove reforges by creating and removing elements from the list.

## Typical Reforge Config

```yaml
id: dynamic
name: "<gradient:#AAFFA9>Dynamic</gradient:#11FFBD>"
description:
- "&a+5% &fDamage"
- "&a+10% &fCrit Damage"
targets:
- melee
stone:
  enabled: true
  name: "<gradient:#AAFFA9>Dynamic</gradient:#11FFBD>&f Reforge Stone"
  lore:
  - "&7Place on the right of the"
  - "&7reforge menu to apply the"
  - "<gradient:#AAFFA9>Dynamic</gradient:#11FFBD>&7 reforge!"
  item: player_head texture:eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvMmM0YTY1YzY4OWIyZDM2NDA5MTAwYTYwYzJhYjhkM2QwYTY3Y2U5NGVlYTNjMWY3YWM5NzRmZDg5MzU2OGI1ZCJ9fX0=
  craftable: true
  recipe:
  - air
  - ecoitems:blank_reforge_stone ? air
  - air
  - iron_block
  - daylight_sensor
  - iron_block
  - air
  - phantom_membrane
  - air
effects:
- id: damage_multiplier
  args:
    multiplier: 1.05
  triggers:
  - melee_attack
- id: crit_multiplier
  args:
    multiplier: 1.1
  triggers:
  - melee_attack
conditions: []
```

## Understanding all the sections

**id:** The ID of the reforge. Only used internally, but it makes sense to have it be the same as the name

**name:** The name of the reforge, shown in lore and in the display name

**description:** The description appended in lore

**targets:** The items that this reforge can be applied to - you can create your own targets in target.yml, or [have a look at the default target.yml here](https://github.com/Auxilor/Reforges/blob/master/eco-core/core-plugin/src/main/resources/target.yml)

**stone:** Contains options about the reforge stone

**stone.enabled:** If a reforge stone is required for this reforge

**stone.name:** The name of the reforge stone item

**.lore: The lore** of the reforge stone item

**stone.texture:** The player head texture in base64

**stone.craftable:** If the stone should be craftable

**stone.recipe:** The stone's crafting recipe

**stone.price:** The custom application price for a stone to have (set to -1 to disable)

## Effects

Effects are the actual functionality of the reforge.

See this page for how to configure effects:

[Configuring an Effect](https://plugins.auxilor.io/all-plugins/configuring-an-effect)

## Conditions

Conditions are requirements that must be met in order for the reforge to activate its effects. In config, conditions look like this:

```yaml
id: above_hunger_percent
args:
  percent: 50
```

A condition consists of an ID and named options, **percent** in this case.

Condition IDs and their corresponding options can be found here:

[All Effects](https://plugins.auxilor.io/all-plugins/configuring-an-effect/all-effects)