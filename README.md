# BTC Momentum Bot — fresh project package

Includes mobile dashboard, Hyperliquid BTC price and 5-minute candle feeds, RSI/momentum/support/resistance signals, account diagnostics, adjustable risk controls, a guarded trade endpoint, and a scheduled exit monitor.

## Critical honesty note
This package is a fresh deployable scaffold, **not a verified finished live-trading bot**. `trade.mjs` deliberately blocks new entries because protective trigger orders and fill verification are not implemented. The scheduled monitor can submit reduce-only exit orders when enabled, but its exit logic must be tested. Do not enable live trading expecting entries to work. Crypto futures can lose funds rapidly.

## Deploy
1. Create a new empty GitHub repository.
2. Unzip this package and upload the *contents* of the `btc-momentum-bot` folder to the repository root (not just the ZIP).
3. Import that repository as a new Netlify site and deploy.
4. Check `/.netlify/functions/price`, `/.netlify/functions/candles`, and `/.netlify/functions/account`.

## Netlify environment variables
- `HYPERLIQUID_ADDRESS`: account address (`0x...`)
- `HYPERLIQUID_API_PRIVATE_KEY`: dedicated authorized Hyperliquid agent wallet private key; store only in Netlify, never in GitHub or chat
- `BOT_TRADING_ENABLED=false` initially
- Optional `MAX_ORDER_USD=10`
- Optional `DEFAULT_STOP_LOSS_PERCENT=2`
- Optional `DEFAULT_TAKE_PROFIT_PERCENT=0` (disabled)
- Optional `EXIT_MODE=hybrid` (`hybrid`, `stop_only`, `momentum`)

The agent wallet must be authorized for the account. Spot USDC is not automatically Perps margin. Never share private keys.
