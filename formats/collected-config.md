---
id: formats.collected-config
title: Collected configuration format
summary: Outer MessagePack collections, plain JSON/base64 record payloads, example
  shape contracts and serializer limits.
topics:
- template-registration
- asset-resolution
- dialogue
- quests
covers:
- JSONCollection
- JsonCollect
- MessagePack
- base64
- schema
state: current
evidence:
- extracted-data
- offline-experiment
- native-default
builds:
- gameassembly-237196995381
reviewed: '2026-10-02'
related:
- systems.template-loading
- audits.2026-10-02-template-collections
sources:
- file: work/template-loading/extraction.json
- file: work/template-loading/collection-audit.json
- file: work/template-loading/verification.json
---

# Collected configuration format

## Outer collection

The saved extraction decodes each outer MessagePack `JSONCollection` as `[directory, {logicalKey: string}]`. Plain `.bytes` collection strings contain JSON; `.mp.bytes` strings contain base64 binary payloads. Collection keys, serialized primary IDs, `ConfigDir` values and Unity container paths identify different things.

See the [native JSON and binary routes](../systems/template-loading.md#native-json-and-binary-routes) for routing and lazy deserialization, and the [saved collection manifest](/template-loading/extraction.json) for bundle/serialized-file/PathID/container identities and hashes.

## Plain and binary records

The eight plain families total 22,855 records in this saved snapshot. Six have binary counterparts with matching key sets. Pair-preserving MessagePack stream decoding handles array map keys and multiple top-level objects; a naive single-object dictionary decoder can produce false failures. Passing structure/base64 checks does not prove native formatter field meanings or binary/plain semantic equivalence.

Three plain records contain duplicate JSON properties. Strict offline parsing records these authored-data findings; native acceptance or rejection is unverified.

## Example schemas

[Examples](./template-loading/examples) and [schemas](./template-loading/schemas) preserve the smallest complete shipped record found per investigated family. Required fields mean required by that example shape contract, rather than a proven minimal native/runtime schema. Graph and POI examples contain shipped empty placeholders. The records retain dependencies and are research fixtures rather than standalone working mods.

Observed loose records and compiled collection entries are separate source versions. The [template-family table](../systems/template-loading.md#set-to-loaderconsumer-map) preserves their different totals; collection presence does not establish source selection, loaded content or runtime reachability.
