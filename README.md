# Ditto

Ditto is an on-demand Cursor skill. Attach it before adding a capability. It walks the YAGNI ladder and stops at the first rung that covers what is left. GitHub is only reached when the cheaper rungs leave a remainder. It is lazy about the solution, never about reading the project.

The skill is [`.cursor/skills/ditto/SKILL.md`](.cursor/skills/ditto/SKILL.md). It does not run on every message.

## Use

Open this repo in Cursor and attach Ditto. Point it at the project you are changing. In this repo, that project is [`sandbox/`](sandbox/).

Ditto ends with one or more Piece lines, then waits. It does not install a package or edit the project in that turn.

```
Piece: <Skip | 1-8> | <evidence>
License: <SPDX id, or n/a>
Still yours: <what you would still write, or nothing>
Stop.
```

## REA

Some requests name a feature by pointing at an app whose source is not in the repo. [REA](https://github.com/morluto/rea) reads that app — binary, ASAR, bundle, or site — and returns evidence for what the feature does. That evidence feeds the ladder before rung 1 and backs the rung-2 check when the project ships as a binary, an ASAR, or a bundle. REA is not a rung, its evidence is data, and it never supplies the capability; the rungs still pick the source. Register it with `npx rea-agents setup`. Without it, Ditto walks on what the request already says.

## When a repo matches

A repo match is rung 7. It happens only when all of these are true:

1. The task is a new capability, not a bugfix, refactor, or small edit.
2. The project does not already do it, and the request is not a second copy of something it already does.
3. The standard library, a platform feature, and an already-declared dependency do not cover the rest.
4. What remains is more than one expression.
5. A published package covers that remainder, its license is MIT, BSD-2-Clause, BSD-3-Clause, or Apache-2.0, and depending on it leaves you owning less than writing it.

Ditto opens at most three GitHub repositories and reads the README, the implementing files, and either `LICENSE` or that repo's `package.json`. If no package holds, rung 8 names the remainder for you to write.

Parsing YAML in `sandbox/` is a repo match. The sandbox only has `add(a, b)` and the `ms` package, so the walk stops at [`nodeca/js-yaml`](https://github.com/nodeca/js-yaml) (MIT). The call that loads the YAML is still yours.

## Fixture

[`sandbox/`](sandbox/) is a Node 18 project used to see the ladder stop early or reach GitHub. [`prompts.md`](prompts.md) is the answer key for those runs. The skill does not read it.

A run passes when the sandbox hash is unchanged, the conclusion names the rung the key expects, and the license on rung 7 was read from `LICENSE` or `package.json`.
