# tiny-chess-01

A compact chess engine in Python (standard library only), packed as an
lzma + base85 payload in `main.py` (4,024 bytes, limit 4,096).

## Engine

- 0x88 board, negamax alpha-beta with iterative deepening and a fixed
  node budget (40,000 nodes/move, deterministic — no clock, no randomness).
- Quiescence search (captures, promotions, and all evasions when in check).
- Transposition table, killer moves, MVV move ordering, PVS at the root.
- Null-move pruning (guarded by non-pawn material).
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

The readable development source lives outside this repo (dev/mini9.py).
