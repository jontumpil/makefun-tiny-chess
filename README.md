# Tiny Chess — a 3,910-byte chess engine for make.fun

[![Competition](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![Rank](https://make.fun/badge/tiny-chess-01/jontumpil/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![Reward](https://make.fun/badge/tiny-chess-01/jontumpil/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine written for the **make.fun** tiny-chess-01 bounty.
The whole engine is a single `main.py` of **3,910 bytes** (cap: 4,096): the
readable source is compressed with lzma and stored as a latin-1 payload that
the file unpacks and executes at startup. No other file is read at runtime.

## How it plays

- 0x88 board, fully legal move generation (castling, en passant, promotions)
- Negamax with PVS (principal variation search) and check extensions
- Transposition table with mate-score adjustment; stored bounds are used
  for real cutoffs, not just move ordering
- Quiescence search over captures and promotions, with full evasions when
  in check (fail-soft)
- Move ordering: TT move, MVV-LVA captures, two killer moves per ply,
  history heuristic
- Tapered evaluation: material plus piece-square tables for middlegame and
  endgame, blended by a material phase counter, all updated incrementally
- Zobrist hashing; positions already seen in the game score as draws
  (repetition-aware: it does not shuffle a won position into a threefold)
- Fixed budget of 80,000 nodes per move — fully deterministic, no clock,
  no randomness anywhere in move choice

## This revision

Version 4 adds transposition-table bound cutoffs and killer moves over the
previous entry, keeps repetition-aware scoring of positions already seen
in the game, and re-golfs the whole program so the stronger search still
fits the 4,096-byte cap with room to spare.

## Running

The engine talks to the make.fun trial environment: it polls
`MAKEFUN_ENV_URL` for games, applies the dealt opening, and answers with
its move until every game is done.

## License

MIT — see `LICENSE`.
