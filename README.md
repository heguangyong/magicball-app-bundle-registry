# MagicBall App Bundle Registry

Single source of truth for MagicBall app bundle bindings.

## Purpose

This repository stores the control-plane registry that binds one concrete application to three projections:

1. Runtime projection
2. Ontology projection
3. Engineering projection

It is intended to back SCE `app_bundle` synchronization and MagicBall three-mode switching.

## Recommended Structure

```text
bundles/
  index.json
  <app-key>/
    bundle.json
```

## `bundles/index.json`

The top-level index should list known bundles and point to each bundle manifest.

Example:

```json
{
  "version": "1.0",
  "generated_at": "2026-03-08T00:00:00.000Z",
  "bundles": [
    {
      "app_id": "app.customer-order-demo",
      "app_key": "customer-order-demo",
      "file": "customer-order-demo/bundle.json"
    }
  ]
}
```

## Bundle Manifest Expectations

A bundle manifest should include:
- `app_id`
- `app_key`
- `app_name`
- `runtime_release_id`
- `ontology_bundle_id`
- `engineering_project_id`
- `default_scene_id`
- `environment`
- `status`
- `runtime`
- `ontology`
- `engineering`
- `scene_bindings`

## Relationship To Other Repositories

- `magicball-app-bundle-registry`
  - control-plane binding truth
- `magicball-app-service-catalog`
  - app distribution and release catalog
- application source repositories
  - real engineering codebases managed through Engineering Mode

## Current Status

This repository is initialized with the minimal structure required for SCE registry sync.
