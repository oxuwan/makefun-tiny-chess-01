# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/oxuwan/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/oxuwan/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact chess engine in Python (standard library only), packed with the kit's `makefun compress` in `main.py` (3,975 bytes, limit 4,096).

## Engine

- 0x88 board, negamax alpha-beta with iterative deepening and a fixed
  node budget (40,000 nodes/move, deterministic — no clock, no randomness).
- Quiescence search (captures, promotions, and all evasions when in check).
- Transposition table, killer moves, MVV move ordering, PVS at the root.
- Null-move pruning (guarded by non-pawn material).
- 12-line opening book (keyed by opening, colour and opponent), played from the book before the search takes over.
- Evaluation: material + piece-square tables (tapered king midgame/endgame),
  bishop-pair bonus, passed-pawn bonus, rook open/semi-open file bonus, and
  king shield bonus. Draw handling for repetition
  (search path) and the fifty-move rule; never resigns.

## Protocol

Speaks the make.fun env HTTP protocol (`MAKEFUN_ENV_URL`): `POST /game`,
`POST /move {game, move}` (UCI), `POST /resign` (never used).

## Files

- `main.py` — the entry (packed).
- `LICENSE` — MIT.

The readable development source lives outside this repo (dev/mini18-final.py). Local gauntlet trials of the kit pack: Elo 1,669 / 1,326 / 1,530 across three trials, mean 1,508 (mini9's mean was 1,440).

---

<sub>Entered on [make.fun](https://make.fun/?ref=xk6tgtt0&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
