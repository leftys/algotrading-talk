---
theme: white
fragments: false # TODO remove # set fragments by {.fragment}
---

<!-- TODO move some bullet points into notes? -->

# Algo-trading v kryptu

<img src="imgs/logo-mini.svg" width="50%" alt="Liquidity labs" />

Jan Škoda

note: intro story?
note: define algo-trading?

---

## About me

- Jan Škoda
- AI degree from MFF UK
- ex Head of Research in Quantlane
- Founder of Liquidity Labs
- Founder of Crypto Lake market data service

note: test 123
note: second note

--

## About Liquidity Labs

- liquidity provider / market maker
- on (DeFi) altcoins, on CEXes
- aim: contribute to stability
- we cooperate with token projects and exchanges

<img src="imgs/logo-mini.svg" width="50%" alt="Liquidity labs" />

note: we are funded by token projects and exchanges, not just from trading revenue. this is unique among algo-trading.
note: LP/MM term

--

## Outline

- what is **liquidity**, it's role in market
  - liquidity providers
  - adversary effects
  - issues of DEXes
  - who pays for liquidity? exchange rebates, project deals
- **algo-trading** {.fragment}
  - examples, good & bad
  - caveats (overfit, skew, )
- **Market (Maker) adversaries**
  - manipulations
  - insider trading
- retail traders, does it make sense?
  - where it does make sense?
- running a one-man-show project takeaways
  - more efficient than a small team
  - automation

<!-- concept of agreessivity? -->
<!-- fake volume? -->

---

## Liquidity

- Asset is:
  - Liquid = easy & cheap to buy / sell
  - Illiquid = high transaction costs, slippage, unstable price

<div class="fragment" style="margin: 0 100px 0 100px;">
	<div style="display: flex; justify-content: space-between; gap: 10px;">
    <img src="imgs/slippage_btc.png" width="50%" alt="Slippage on BTC" />
   <img src="imgs/slippage_ltc.png" width="50%" alt="Slippage on LTC" />
	</div>
	<small>BTC and LTC slippage, source: Kraken Analytics</small>
</div>

note: trading slower is better, but impractical in volatility
note: ltc price could drop ~3% more percent once it dropped 1%

--

## Goal: maximize liquidity

--

## Liquidity providers (*LP*)

- Lock their assets into AMM positions (eg. Uniswap DEX) or limit orders (eg. Binance CEX)
- Face risks of hacks, exchange defaults, changing prices and adverse selection
- Expect returns from spreads (order-book) or fees (AMM)
- Sometimes incentivized by exchanges or token projects (rebates, deals)

--

## Liquidity mechanics on CEX

Example with order book:

- MM quotes with $10 spread and 1 ETH quantity
- ETH/USD price goes from 1990 to 2000
- MM had buy order at 1985 and sell at 1995
- MM sold and has now -1 ETH position sold at 1995
- Price trends higher to 2010
- MM buys back at 2005, realizes $10 loss

<!-- TODO imgs -->

--

## AMM profitability

<img src="imgs/eth_usdc_profitability.webp" width="100%" alt="ETH/USDC profitability" />
<small>Uniswap v3 ETH/USDC pools. Source: <a href="https://crocswap.medium.com/">https://crocswap.medium.com/</a></small>

--

## Why AMMs lose money?

- Adverse fills and impermanent loss
- Low volume, high volatility
- Fees are not enough to cover losses
- Fees don't adapt to market conditions (volatility)
  - In order books, MMs just widen the spread

--

## DEX solutions?

- Order book DEXes -- <a href="https://openserum.io/">Open Serum</a> (Solana spot), <a href="https://trade.dydx.exchange/">DyDx</a>, <a href="https://app.hyperliquid.xyz/">Hyperliquid</a> (both perps on L2)
- Dynamic fees -- <a href="https://www.crocswap.com/">CrocSwap</a> (AMM)
- Failed(?) attempts -- <a href="https://cointelegraph.com/news/bancor-pauses-impairment-loss-protection-citing-hostile-market-conditions">Bancor pauses IL protection</a>

--

## Who pays for liquidity?

- AMMs: Retail LPs unaware of risks/profitability, takers on high-fee pools
- CEXes:
  - Exchanges pay rebates to big MMs (eg. 0.01%)
  - Projects sponsor MM activity on their tokens
    - Actually they sometimes sponsor *wash trading* as well

---

## Algo-trading

- There are many more algorithmic-trading strategies besides MM
- By style:
  - arbitrage, mean-reversion, trend-following, pair-trading
  - front-running, spoofing, manipulation {.fragment}
- By implementation: {.fragment}
  - machine-learning model based
- By frequency: {.fragment}
  - *HFT*, mid-frequency, on daily candles
- By data type: {.fragment}
  - on-chain metrics, news, social media sentiment

--

## The Process

- Idea
  - Based on psychology/behaviour,
- Data gathering
- Parameter optimization
- (Backtest)
- Live trading

--

## Caveats

- *Alpha* decay
- Execution issues
- Risk premiums {.fragment}
  - Lets buy dips after each quick -5% move and sell after 3 days
  - Earns 1% each time, but once in a while looses 10%+.
- Skewed returns

--

## Backtest & optimization issues

- Overfitting
  - even manually!
- Forward looking bugs
- Execution precision

--

## Execution issues

- Slippage
- Adverse selection for limit orders
- Front-running

--

## Performance

- Sending packets before receiving
- Not allocating memory
- Fitting into cache
- Reality: exchanges are slow

---

## Market (Maker) adversaries

- manipulations
- insider trading

--

## Manipulations

- Pump & dumps
- On small-cap tokens with low liquidity
- Attacker slowly accumulates position (buys partly from MMs) {.fragment}
- (optional) Attacker pays influencers to promote the token
- Attacker buys aggressively to pump the price (mostly from MMs)
- MMs have to buy-back at higher price {.fragment}
- Attacker sells to MMs and last buyers
- When price starts to fall, attacker sells the rest aggressively, causing the price to collapse

--

## Insider trading

- Project teams have access to non-public information
- Team members or management use it to front-run the market before announcements

--

## Insider trading

<img src="imgs/time_pelosi.png" alt="Trader of the year" class="r-stretch" class="fragment" />

<a href="https://nypost.com/2022/10/05/house-speaker-nancy-pelosi-has-accrued-millions-from-husbands-trades-report/">Nancy Pelosi (source)</a>

note: husband bought Nvidia before subsidies were considered
note: husband bought Tesla as his wife was pushing subsidies

---

## Chances of retail traders

- Retail traders are at a disadvantage
  - High fees, information assymeties, manipulated news, influencers, bad actors...
  - This applies to crypto as well
  - Solo trader psychology: gambling, overconfidence, mistakes
  - Lower the trading frequency, the better (HODL)

note: don't do even algo-trading alone?

--

## Please don't "day trade"

<img src="imgs/day-trading.jpg" alt="Day trading" />

note: there are better ways to spend your time/energy in crypto

<!--
- retail traders, does it make sense?
  - where it does make sense?
- running a one-man-show project takeaways
  - more efficient than a small team
  - automation
-->
