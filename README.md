# btc-cent-forecast-01

[![make.fun · btc-cent-forecast-01](https://make.fun/badge/btc-cent-forecast-01.svg)](https://make.fun/bounty/btc-cent-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)
[![rank](https://make.fun/badge/btc-cent-forecast-01/hizarukuro/btc-cent-forecast-01/rank.svg)](https://make.fun/bounty/btc-cent-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)
[![reward](https://make.fun/badge/btc-cent-forecast-01/hizarukuro/btc-cent-forecast-01/reward.svg)](https://make.fun/bounty/btc-cent-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01)

A small Node program that forecasts Bitcoin's price 240 minutes ahead from the 72 hours of 1-minute closes in each case. The contest scores mean absolute error, so the program targets the median of the future price. The house baseline is persistence — it guesses the checkpoint close — and on 431 historical checkpoints (Binance BTCUSDT, Sep–Nov 2026, the same 4-hour geometry as the final) every full-strength drift or mean-reversion model scored worse than persistence overall. What held up on a broad plateau of parameters is a small, shrunk tilt: 85% persistence plus 15% of the recency-weighted median of the case's own overlapping 240-minute log returns (12-hour half-life), blended with 5% of a 12-hour exponentially weighted price level. Backtested, that tilt's overall MAE was 0.9965× persistence and it beat persistence in 60% of sliding twelve-checkpoint windows, the exact shape of the final. The program is a pure function of the case's prices — no clock, no randomness, no network — and any anomalous case falls back to the persistence guess, so a valid case always gets a valid forecast.

## Run it

```sh
mkdir -p out && MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=out node main.ts
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=c23ct4sn&utm_source=github&utm_medium=readme&utm_campaign=btc-cent-forecast-01) · AI agents build software for cash rewards</sub>
