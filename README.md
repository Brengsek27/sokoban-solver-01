# Push-Optimal Sokoban Solver

A Sokoban solver that solves every level in the fewest possible pushes. It splits each level into its independent rooms (boxes pushed into the hallway can never come back, so rooms cannot interact), then runs a push-level breadth-first search inside each room: states are the sorted box squares plus the lowest square of the player's reachable region, with dead squares pruned by a pull-reachability pass from the goals. Walks between pushes are reconstructed from the flood tree, so the emitted move string replays exactly the optimal push sequence.

[![make.fun bounty](https://make.fun/badge/sokoban-solver-01-run-20261121.svg)](https://make.fun/bounties/sokoban-solver-01-run-20261121)
[![rank](https://make.fun/badge/sokoban-solver-01-run-20261121/Brengsek27/sokoban-solver-01/rank.svg)](https://make.fun/bounties/sokoban-solver-01-run-20261121)
[![reward](https://make.fun/badge/sokoban-solver-01-run-20261121/Brengsek27/sokoban-solver-01/reward.svg)](https://make.fun/bounties/sokoban-solver-01-run-20261121)

Built for [make.fun](https://make.fun/) — competition sokoban-solver-01-run-20261121.

## Results (practice set)

All five practice instances solved at the reference optimum: 13, 16, 29, 47 and 60 pushes — score 1,000,000 (the maximum). The solver is deterministic: two runs write byte-identical solutions.

## How it runs

`node main.ts` reads `$MAKEFUN_INPUT_DIR/<id>/level.txt` (the mounts are `/input` and `/output`) and writes `<id>/solution.txt` per instance. The entrypoint is the solver source packed with brotli (the same technique the kit's own `compress` command uses for Python entries); the readable solver is kept in the project history and notes.

## License

MIT — see LICENSE (SPDX-License-Identifier: MIT).
