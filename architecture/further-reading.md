# Further Reading

- [The Twelve-Factor App](https://12factor.net) — the deployment/operations
  half of this playbook (config, backing services, disposability, logs)
  leans directly on it.
- *Clean Architecture* (Robert C. Martin) — the layering/dependency-
  direction half (layered authority, one composition root, boundary
  validation) is this playbook's application of the same ideas; its SOLID
  chapters are the source for [[behavioral-substitutability]] (Liskov
  Substitution) and [[narrow-role-specific-interfaces]] (Interface
  Segregation), generalised past their original OOP-inheritance framing.
- *Domain-Driven Design* (Eric Evans) — [[bounded-contexts]] and
  [[ubiquitous-language]] are this playbook's take on two of its core
  ideas.
- The [Data Product Canvas](https://www.datamesh-architecture.com/data-product-canvas)
  (Data Mesh) — [[well-formed-interface]] generalises its eight quality
  facets beyond literal data products to any unit a system exposes.
- [Basics of the Unix Philosophy](https://cscie2x.dce.harvard.edu/hw/ch01s06.html)
  (Eric Raymond, distilling McIlroy/Pike/Thompson) — the single largest
  source for this playbook's principles tier; its seventeen rules map
  either onto a dedicated principle here or, where the idea already
  existed under a different name, are noted inline in that principle's
  "Why it matters" section.
- [Deconstructing the "Unix philosophy"](https://www.tedinski.com/2018/05/08/case-study-unix-philosophy.html)
  (Ted Kaminski) — a critique of the above: composition is the actual
  core idea, text streams are just one instantiation of it, and "do one
  thing" taken dogmatically fights against the task a real user showed up
  for. [[public-interfaces-are-one-way-doors]] and the caveats inside
  [[modularity]] and [[well-formed-interface]] come from here.
