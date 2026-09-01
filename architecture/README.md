# Architecture Playbook — Index

Durable architectural principles, patterns, and standards, distilled from
building several real web apps side by side and written to be generic —
apply to any project, in any language or framework.

One idea per file, so each can be linked to, updated, and cited on its own.
Files cross-reference each other with `[[slug]]`. This index is the only
place that should ever get long — treat it as the compiled table of
contents; if this playbook is ever rendered into one document, this file
defines the order and grouping.

Three tiers, most abstract to most concrete — read top-down when designing
something new, bottom-up when reviewing whether existing code follows it:

- **Principles** — *why*. Values a design should satisfy, independent of
  language or framework.
- **Patterns** — *how*. Recurring, reusable shapes that satisfy one or more
  principles.
- **Standards** — *what, exactly*. Naming and structural conventions.
- **Glossary** — shared vocabulary the above use, defined once.

## Principles

- [Layered authority](principles/layered-authority.md) — one layer is authoritative; everything else is a view.
- [Single source of truth](principles/single-source-of-truth.md) — shared reactive state lives in exactly one place.
- [Law of Demeter across layers](principles/law-of-demeter-across-layers.md) — talk to your neighbor, never reach through them.
- [Fail fast, no fallbacks](principles/fail-fast-no-fallbacks.md) — validate at the boundary, halt loudly on failure.
- [Explicit modeling](principles/explicit-modeling.md) — represent truths explicitly, not as incidental side effects.
- [Decide once, at the authority](principles/decide-once-at-the-authority.md) — compute a decision once, where its rule lives.
- [One composition root](principles/one-composition-root.md) — exactly one place wires concrete dependencies.
- [Minimal necessary abstraction](principles/minimal-necessary-abstraction.md) — build what's asked; don't guess at generality.
- [Boundary validation](principles/boundary-validation.md) — validate at the edges, trust the interior.
- [Uncertainty travels with the value](principles/uncertainty-travels-with-the-value.md) — never present a guess as a fact.
- [Extract after duplication proves itself](principles/extract-after-duplication-proves-itself.md) — don't pre-build shared libraries.
- [Backing services are attached resources](principles/backing-services-are-attached-resources.md) — swap one out via config, never code.
- [Disposable processes](principles/disposable-processes.md) — fast startup, graceful shutdown, boring to restart.
- [Logs are event streams](principles/logs-are-event-streams.md) — write to stdout/stderr; storage and routing aren't the app's job.
- [Well-formed interface](principles/well-formed-interface.md) — discoverable, addressable, understandable, trustworthy, natively accessible, interoperable, valuable alone, secure.
- [Bounded contexts](principles/bounded-contexts.md) — a concept's meaning is authoritative only within its boundary.
- [Ubiquitous language](principles/ubiquitous-language.md) — code and domain conversation share exactly one vocabulary.
- [Modularity](principles/modularity.md) — simple parts connected by clean interfaces, so most problems stay local.
- [Clarity over cleverness](principles/clarity-over-cleverness.md) — write for the human maintainer, not for a small performance win.
- [Separate policy from mechanism](principles/separate-policy-from-mechanism.md) — what changes fast and how it's done mutate on different timescales.
- [Design for transparency](principles/design-for-transparency.md) — build in visibility to internal state from the start.
- [Robustness through simplicity](principles/robustness-through-simplicity.md) — robustness falls out of transparency and simplicity, it isn't a separate feature.
- [Fold knowledge into data](principles/fold-knowledge-into-data.md) — prefer complexity in a data structure over complexity in procedural logic.
- [Least surprise](principles/least-surprise.md) — an interface should do what its audience already expects.
- [Purposeful silence](principles/purposeful-silence.md) — say nothing when there's nothing surprising to report.
- [Economise programmer time](principles/economise-programmer-time.md) — programmer time is the expensive resource; default to spending machine time instead.
- [Prefer generated code](principles/prefer-generated-code.md) — write a generator for repetitive, error-prone hand-written shapes.
- [Prototype before polishing](principles/prototype-before-polishing.md) — get it working, un-optimised, before tuning it.
- [Distrust one true way](principles/distrust-one-true-way.md) — no design is optimised for every case its designer didn't anticipate.
- [Scoped extensibility](principles/scoped-extensibility.md) — self-describing formats for contracts you don't fully control, not license for speculative code generality.
- [Reuse existing standards](principles/reuse-existing-standards.md) — check for a fitting standard before designing a bespoke one; adopt only the slice you need, keep the seam open for the rest.
- [Public interfaces are one-way doors](principles/public-interfaces-are-one-way-doors.md) — you can add to a shipped interface freely, but removing or reshaping it costs whoever already depends on it.
- [Behavioral substitutability](principles/behavioral-substitutability.md) — any implementation of a shared contract must be swappable for another without surprising the caller.
- [Narrow, role-specific interfaces](principles/narrow-role-specific-interfaces.md) — expose the surface a consumer actually uses, not one interface covering every consumer's needs.

## Patterns

- [Self-registering unit](patterns/self-registering-unit.md) — a unit registers itself; the composition root just loops.
- [Registry and compose](patterns/registry-and-compose.md) — many sources merge into one record per entity.
- [Typed projection at the wire boundary](patterns/typed-projection-at-wire-boundary.md) — loose internally, typed and allowlisted externally.
- [Layered trust guards](patterns/layered-trust-guards.md) — one guard per trust class, narrowest guard wins.
- [Dependency struct, not positional args](patterns/dependency-struct-not-positional-args.md) — name the collaborators, don't position them.
- [Config loader chain](patterns/config-loader-chain.md) — one chain declares every config key, resolved once at boot.
- [Two independent pipelines](patterns/two-independent-pipelines.md) — don't share derived state between differently-timed renderers.
- [Single observable stream](patterns/single-observable-stream.md) — one writer, many subscribers, client-side.
- [Design-sketch-before-code](patterns/design-sketch-before-code.md) — write the fit/strain/non-scope sections before implementing.
- [Noun-verb interaction diagram](patterns/noun-verb-interaction-diagram.md) — one page, entities as nodes, verbs as edges, scoped to core behavior.
- [Boring composition over dynamic loading](patterns/boring-composition-over-dynamic-loading.md) — one static import beats runtime plugin loading.
- [Restart before rebuild](patterns/restart-before-rebuild.md) — a dev container's default refresh is a restart; rebuild only when a dependency manifest actually changed.
- [Layered secret scanning](patterns/layered-secret-scanning.md) — a local pre-commit scanner plus a CI scan, since neither alone is enforcement; baseline pre-existing findings so it fails only on what's new.

## Standards

- [Name by architectural role](standards/name-by-architectural-role.md) — Adapter/Service/Controller/View/Source/Guard/Loader.
- [Commenting code](standards/commenting-code.md) — a comment states a fact about the code, never a restatement of it or a narration of the diff.
- [Commit messages](standards/commit-messages.md) — subject is imperative and concise; a body, when it earns one, carries the why, never a line-by-line narration of the diff.
- [Many small single-purpose files](standards/many-small-single-purpose-files.md) — no sectioned mega-files.
- [Directory layout mirrors layering](standards/directory-layout-mirrors-layering.md) — layers get their own directories, not just names.
- [Uniform self-registering interface](standards/uniform-self-registering-interface.md) — every unit exposes the same minimal method surface.
- [Guards named for the check](standards/guards-named-for-the-check.md) — name the condition, not the intended user.
- [One declaration site per config key](standards/one-declaration-site-per-config-key.md) — no raw env reads outside the loader.
- [Subsystem-prefixed env vars](standards/subsystem-prefixed-env-vars.md) — one exact prefix per dependency, one consistent attribute suffix style.
- [Inferred values get their own field](standards/inferred-values-get-their-own-field.md) — a sibling flag, never an overloaded meaning.
- [Normalise correlation keys once per direction](standards/normalise-correlation-keys-once-per-direction.md) — one place in, one place out.
- [Verify against a running instance](standards/verify-against-a-running-instance.md) — closest analog to production, not ad hoc execution.
- [Semantic versioning](standards/semantic-versioning.md) — MAJOR is a product-launch decision, MINOR for operator action required, PATCH for everything else.

## Glossary

- [Composition root](glossary/composition-root.md)
- [Guard](glossary/guard.md)
- [Fail fast](glossary/fail-fast.md)
- [Source of truth](glossary/source-of-truth.md)
- [Wire contract](glossary/wire-contract.md)
- [Projection](glossary/projection.md)
- [Self-registration](glossary/self-registration.md)
- [Rule of Three](glossary/rule-of-three.md)

See [Further reading](further-reading.md) for the external sources this
playbook draws on and which principles come from which.

## Maintaining this playbook

- One idea per file. If a new entry needs "and also," split it.
- Every file gets frontmatter (`name`, `type`, `description`) and links
  related ideas with `[[slug]]`.
- Add new files under the right tier directory, then add one line to this
  index — the index must stay a table of contents, never inline content.
- A `[[slug]]` that doesn't resolve yet is fine — it marks something worth
  writing, not an error.
- Citing a new external source? Add it to [Further reading](further-reading.md),
  not here.
