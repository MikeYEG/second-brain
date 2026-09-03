---
type: infrastructure
status: active
tags: [home, frigate, docker]
updated: 2026-09-03
---


# Frigate NVR Box

Home camera system — Frigate NVR 0.17.x.

## Hardware
- Docker host on Ubuntu 24.04, i7-6700 (Skylake HD 530 iGPU), Quadro M4000 (Maxwell)
- USB Coral for object detection; Intel iGPU via VAAPI for decode
- Both GPUs are too old for 0.17's GPU inference stacks → enrichments run on `device: CPU` permanently (OpenVINO path segfaults the embedding process)

## Cameras
Four Reolink cameras — three "suite" yard cams + east balcony; detect on 896x512 substreams. Frigate+ subscriber (plus:// model).

## Config notes
- Face recognition, semantic search, and LPR enabled
- Cameras are roof-mounted (underside), so frontal faces aren't achievable. For "specific person on the property" alerting, use person-only zone alerts on the `nw_edge` zone of `reolink-suite-nw` → Home Assistant notification.
- Wildlife labels tracked: deer, rabbit, fox (as coyote bucket), bear, horse — alongside person/pets/vehicles
- MQTT to Home Assistant
