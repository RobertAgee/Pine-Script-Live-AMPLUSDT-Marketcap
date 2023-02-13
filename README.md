# Pine-Script-Live-AMPLUSDT-Marketcap
How and Why to add live AMPL/USDT marketcap tracking for lower timeframe charts

<img src="https://s3.tradingview.com/snapshots/s/SiEG1IL0.png">

# What is AMPL?  How can it be traded profitably?
AMPL is a crypto with unique tokenomics. AMPL "rebases" (inflates or deflates supply) nightly in order to bring 1 AMPL closer to $1, ie prices above $1 inflate the supply to bring prices down, and prices below $1 deflate the supply to bring prices up. However, what does remain the same is the % of the total marketcap you own. That means that your % of the marketcap remains the same throughout each rebase.  

# How can it be traded profitably?
The rebasing mechanic creates short periods of high volatility followed by periods trading flat.  Timing when and how these volatility cycles can be very profitable for intraday and short swing traders.

# Why is this tool needed?
<b>Most cryptos trade on price, but AMPL trades on marketcap value.</b> Because AMPL's current price is not 1:1 with marketcap value like most cryptos, price data alone isn't useful for technical analysis. Tradingview only offers daily marketcap data, which isn't useful for lower timeframes.  This tool provides plotted candlestick marketcap data for any timeframe.

# How is the live marketcap calculated?
Simply enough, because rebases only take place on a daily timeframe (and thus the supply only changes once per day), we calculate the current AMPL marketcap by multiplying the latest daily supply by the current price.

# How can this tool be used?
It can be treated like a price ticker and plugged into normal TA indicators like MACD or RSI to signal entries and exits.

<img src="https://www.tradingview.com/x/iHQodVPV/">

<code>// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © CubanEmissary
//@version=5
indicator("Live AMPL Marketcap")
//
// Select desired timeframe
tf = input.timeframe('', 'Timeframe')
//
// Request timeframe ohlc for candle plots
ampl_price_open = request.security("KUCOIN:AMPLUSDT", tf, open)
ampl_price_low = request.security("KUCOIN:AMPLUSDT", tf, low)
ampl_price_high = request.security("KUCOIN:AMPLUSDT", tf, high)
ampl_price_close = request.security("KUCOIN:AMPLUSDT", tf, close)
//
// Request current supply of AMPL
ampl_supply = request.security("AMPL_SUPPLY", 'D', close)
//
// Calculate marketcap ohlc by multiplying price ohlc by current supply
ampl_mcap_open = ampl_price_open * ampl_supply
ampl_mcap_low = ampl_price_low * ampl_supply
ampl_mcap_high = ampl_price_high * ampl_supply
ampl_mcap_close = ampl_price_close * ampl_supply
//
// Plot current value and candle data for timeframe
plot(ampl_mcap_close, 'AMPL MCAP', color = close >= open ? color.green : color.red)
plotcandle(ampl_mcap_open, ampl_mcap_low, ampl_mcap_high, ampl_mcap_close, title='AMPL MCAP', color = ampl_mcap_open < ampl_mcap_close ? color.green : color.red, wickcolor= ampl_mcap_open < ampl_mcap_close ? color.green : color.red)
</code>
