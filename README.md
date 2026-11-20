# makefun-tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/jontumpil/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/jontumpil/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine that fits in 4 KB of Python: a 0x88 board,
alpha-beta search with a transposition table and principal-variation
search, a quiescence search that searches every check evasion, and a
tapered piece-square evaluation maintained incrementally. It searches a
fixed number of nodes per move (never a clock), so every game replays
move for move. The readable source is packed into the 4 KB entrypoint
with the kit's lzma compressor.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py
```

The engine plays every game through the competition environment server
(see the tiny-chess-01 kit): it polls `/game`, answers with `/move` in
UCI notation, and plays all eight house opponents in one process.

---

<sub>Entered on [make.fun](https://make.fun/?ref=w7fy1fnp&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
