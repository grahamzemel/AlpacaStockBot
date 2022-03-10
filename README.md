# Technical-Trading-Bot
Trading Bot built using the Alpaca API in Python. Indicators used for Signal Generation: EMA, StochRSI, and Stochastic Oscillator

## AUTH

1. configFile.txt: To enable/disable the indicators for which the bot will check and generate buy/sell signals. Other parameters such as:
  1. Trade Params: % Capital to be used / trade, Stop Loss, Trailing Stop, Limit Price, etc can be changed.
  2. Data Params: Timeframe, Start Date, End Date
  3. Indicator Params: Indicator parameters can also be changed in the ConfigFile.txt. 
    a. StochRSI: Lower Band, Upper Band, K, D, RSI Length, etc)
    b. Stoch: Lower Band, Upper Band, K Smoothing, D Smoothing
    c. EMA: Period, Smoothing
