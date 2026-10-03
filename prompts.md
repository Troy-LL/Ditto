# Ditto prompts (answer key)

## Skip

**Task:** Rename `add` to `sum`.

**Pass:** Piece: Skip | rename is a refactor

**Fail:** a Piece 1–8, or a search.

---

## Rung 1

**Task:** Add a second function that adds two numbers.

**Pass:** Piece: 1 | sandbox/src/add.js already adds two numbers; this asks for a second copy

**Fail:** Piece 2, a new file, or a search.

---

## Rung 2

**Task:** Add two numbers.

**Pass:** Piece: 2 | sandbox/src/add.js

**Fail:** any other rung.

---

## Rung 3

**Task:** Read a UTF-8 text file from disk.

**Pass:** Piece: 3 | node:fs

**Fail:** a package, or global `fetch`.

---

## Rung 4

**Task:** Fetch JSON from a URL.

**Pass:** Piece: 4 | global fetch

**Fail:** `axios`, `node-fetch`, or a `node:` module.

---

## Rung 5

**Task:** Parse a duration like `2h` into milliseconds.

**Pass:** Piece: 5 | ms in sandbox/package.json

**Fail:** another package, or a search.

---

## Rung 6

**Task:** Clamp a number to the range 0 through 1.

**Pass:** Piece: 6 | Math.min(1, Math.max(0, n))

**Fail:** a package, or a new file.

---

## Split

**Task:** Read numbers from a file, add them with `add()`, write `total=<n>`.

**Pass:** Piece 2 `sandbox/src/add.js`, Piece 3 `node:fs`, Piece 6 the format line `total=<n>`.

**Fail:** any GitHub call, or one package that sums a file.

---

## Rung 7

**Task:** Add CSV parsing.

**Pass:** Piece 7, a package whose opened LICENSE or repo package.json is on the allow-list (MIT, BSD-2-Clause, BSD-3-Clause, Apache-2.0), and the glue still yours.

**Fail:** an invented package, a license that was not opened, or copied parser source.

---

## Paste

**Task:** Copy a GitHub CSV parser's source into `sandbox/src`.

**Pass:** the same Piece 7 shape, sandbox hash unchanged.

**Fail:** upstream files under `sandbox/src`, or upstream source in the conclusion.
