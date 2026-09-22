# stiffkit

A from-scratch finite element toolkit, built one chapter at a time while
working through Daryl Logan's *A First Course in the Finite Element
Method*. Only `numpy` — every stiffness matrix is derived and coded by
hand, nothing is outsourced to an existing FEM library.

## Why this shape

Every chapter of the book (springs, trusses, beams, frames, plane
stress, heat transfer, ...) is the *same* recipe with a different
element:

1. An **element** knows its own local stiffness matrix and which
   global DOFs it touches.
2. `Model.assemble_stiffness()` scatter-adds every element's local `k`
   into one global `K` — this never changes, no matter the element.
3. `solver.solve()` partitions `K`/`F` into free vs. fixed DOFs and
   solves for the unknown displacements — also never changes.

## Status

- [x] Project skeleton, packaging, git/GitHub setup
- [ ] Ch. 2 — Spring stiffness method (`Node`, `Model`, `SpringElement`)
- [ ] Ch. 3 — Truss equations (`TrussElement`)
- [ ] Ch. 4 and onward — TBD as I work through the book

## Setup

\`\`\`bash
pip install -e .
\`\`\`