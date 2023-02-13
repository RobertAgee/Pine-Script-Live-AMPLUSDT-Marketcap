# Pine-Script-Live-AMPLUSDT-Marketcap
How and Why to add live AMPL/USDT marketcap tracking for lower timeframe charts

# What is AMPL?
AMPL is a crypto with unique tokenomics. AMPL "rebases" (inflates or deflates supply) nightly in order to bring 1 AMPL closer to $1, ie prices above $1 inflate the supply to bring prices down, and prices below $1 deflate the supply to bring prices up. However, what does remain the same is the % of the total marketcap you own. That means that your % of the marketcap remains the same throughout each rebase and ultimately the value being speculated on is the value of AMPL's underlying marketcap. Because of the rebasing mechanics, for short periods of time AMPL becomes a highly volatile asset, and thus can be very profitable for intraday and short swing traders.

# Why is this indicator needed?
Because the price is not 1:1 reflective of the actual marketcap value like most cryptos, price data alone isn't useful for technical analysis. And, while Tradingview does offer daily timeframe data for the AMPL marketcap, the price action we are most interested in takes place on hourly timeframes. Thus, we must somehow calculate the marketcap value ourselves when using lower timeframes to enter and exit.

# How is the live marketcap calculated?
Simply enough, because rebases only take place on a daily timeframe (and thus the supply only changes once per day), we can take the latest supply and multiply it by our lower timeframe pricing to chart a live AMPL marketcap value on which we can do our normal technical analysis . 
