# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/duevan07/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/duevan07/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in one Python file under 4,096 bytes (`main.py`, standard library only, Python 3.13), written from scratch for the make.fun bounty "tiny-chess-01". The file is a zlib+base85 payload that unpacks and execs the engine; nothing else is read or imported. It replays the game from `start_fen` and `moves`, generates moves on a 64-square board with precomputed rays (castling, en passant, promotion, check detection), and searches with iterative-deepening PVS: transposition table, killer move, null move, reverse futility and futility pruning, late move reduction, check extension, and a capture/promotion quiescence search that resolves checks at the horizon. Evaluation is tapered middlegame/endgame material plus piece-square tables, rebuilt at every root with position-specific terms (passed, isolated and doubled pawns, king shield, open files, bishop pair, king tropism). It is deterministic: no clock, no randomness, a fixed node budget per move (60k against the depth rungs, 120k otherwise, halved every 70 plies); when the budget runs out it plays the best move of the last completed depth. Run with `MAKEFUN_ENV_URL` set: `python main.py`.

Practice gauntlet (2026-11-24): Elo 1451, 4 wins / 2 losses, 331 spare plies.

## Run it

```sh
MAKEFUN_ENV_URL=<url> python main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=re5wz9pk&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
