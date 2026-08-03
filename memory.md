Last Updated: 2026-07-22

## Current Projects
- Web apps in Go/HTML (Tailwind, DaisyUI) — work, for Cognitive Advantage — ongoing
  - webkit extraction (shared Go module across noc + tactical-cloud): noc fully retrofitted (branch docs/webkit-extraction-plan, pushed). tactical-cloud retrofitted + no-OIDC admin bypass + one-cloud-per-node fix (branch webkit-retrofit/config, pushed, not merged) — as of 2026-07-21. Neither branch merged to main yet.
  - tactical-cloud: cloud create/join UX rework + per-cloud manage password gate landed on webkit-retrofit/config (not merged). Design-only doc drafted for the next feature: "Cluster" (a microk8s deployment across a chosen subset of a Cloud's participants, distinct from Cloud itself) — written up at tactical-cloud/scrapbook/cluster.md, not yet implemented. Directed by Pete's boss; Pete is skeptical of letting one swarm run more than one microk8s cluster but is building it as specified.
- D&D 5e campaign — GM, uses AI to tidy up notes — ongoing, weekly
- Game development in Godot — side project, occasional

## Open Decisions
- Cluster feature (tactical-cloud): script-metadata schema for the new "cluster" param type, where the peer-side execution guard hooks into api/ws_peer, and whether Cluster gets its own create/edit pages — all flagged as open in scrapbook/cluster.md, to resolve before implementation starts.
