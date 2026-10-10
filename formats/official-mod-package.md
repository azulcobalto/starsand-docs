---
id: formats.official-mod-package
title: Official mod package format
summary: 'Official mod package format: preserved findings, source scope, and unresolved
  verification.'
topics:
- official-mods
covers:
- mod.json
state: current
evidence:
- metadata
- extracted-data
builds:
- unknown
reviewed: null
---

# Official mod package format

Official ModKit packages use an existing garment fallback of matching clothing type and slot. The repository README records `mod.json` Entry assets/data mappings, `assets/manifests/assets.json`, and `data/clothing.json`. Formula books and production formulas are recorded there as unimplemented for mods; construction semantics are unknown. Package serialization and runtime acceptance are separate contracts.

See [root schema](../../readme.md#mod-structure) and [acceptance flow](../systems/official-mod-loading.md).
