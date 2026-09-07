# RHEA Cross-Chain Price Monitor

A read-only TypeScript command-line monitor that compares the estimated RHEA/USDT price across BNB Smart Chain and NEAR Protocol.

## How It Works

- Reads the RHEA/WBNB and WBNB/USDT pool state on BNB Smart Chain through public RPC calls.
- Queries Ref Finance pools on NEAR for the RHEA/NEAR and NEAR/USDT conversion path.
- Normalises both paths to RHEA/USDT and reports the absolute and percentage difference every 10 seconds.
- Uses on-chain view calls only; it does not hold keys, sign transactions, or execute trades.

## Stack

- TypeScript
- ethers.js
- near-api-js
- Uniswap V3-compatible pool contracts
- Ref Finance view functions

## Run Locally

Requirements: Node.js 20 or later.

```bash
git clone https://github.com/egor-karpov-spb/rhea-cross-chain-price-monitor.git
cd rhea-cross-chain-price-monitor
npm install
npm run typecheck
npm start
```

The process refreshes prices every 10 seconds. Stop it with `Ctrl+C`.

## Output

![Example console output](result_crypto.jpg)

## Limitations

- Pool addresses, token addresses, fee tiers, and pool identifiers are currently configured in source code.
- Displayed differences do not account for fees, slippage, liquidity, bridge costs, execution latency, or price impact.
- Public RPC availability can affect the output.
- This repository is an engineering experiment, not financial advice or an automated trading system.

## License

Released under the [MIT License](LICENSE).
