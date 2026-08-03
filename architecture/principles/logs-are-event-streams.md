---
name: logs-are-event-streams
type: principle
description: An application writes a plain, timestamped event stream to stdout/stderr and never manages its own log files, rotation, or routing — that's the execution environment's job.
---

An application never manages its own log files, rotation policy, or
routing. It writes a plain, timestamped stream of discrete events to
stdout/stderr (or an equivalent unbuffered output) and lets whatever is
running it — a container runtime, a systemd unit, a log-shipping sidecar —
capture that stream and decide where it ends up: a file, a log
aggregator, a terminal.

The application's only job is producing the events; storage, rotation,
retention, and searchability are all downstream concerns that belong to
the execution environment, not the codebase.

**Why it matters:** decoupling "what happened" from "where it's stored"
means the same code behaves identically on a laptop, in a container, or
under an orchestrator — nothing has to change based on deployment target.
It also removes an entire category of things the application would
otherwise have to get right itself: log file paths, disk usage, rotation
timing, and what happens when the disk fills up.
