# Alpaca Stock Bot
Alpaca Stock Trading Bot built using the Alpaca API in Python. Indicators used for Signal Generation: EMA, StochRSI, and Stochastic Oscillator.
## Setup

1. Change **AUTH/authAlpaca.txt** to your corresponding API keys (found on your [homepage](https://app.alpaca.markets/)). The paper trading URL is a dummy account that funds you with $100k to experiment with (not real money, but real market data).  

    * Input your keys in this format: 
    
    `{ "APCA-API-KEY-ID" : "*******",
    "APCA-API-SECRET-KEY" : "*************",
    "BASE-URL" : "https://paper-api.alpaca.markets"}`
2. Change **AUTH/ConfigFile.txt** to your desired configuration. Change the start and end date for measurements, take profit, stop loss, all that good stuff. 
3. In **AUTH/Tickers.txt**, insert all the tickers you'd like to trade in this format: `SPY AAPL MSFT TSLA`. See file for examples.

## Running
Note: If you'd like to run this full-time with no interaction on a server, scroll past step 1. 

1. Run `python3 main.py`. Pretty simple. The bot will periodically examine each ticker (~60s rotation per `configfile.txt`) and determine whether or not to make a trade for said ticker. If not, it will move on and cycle through them all until the end of time.
2. **To run 24/7 without any human interaction, head to [DigitalOcean](https://cloud.digitalocean.com) and create a droplet**. 
3. Your droplet's settings are up to you, the cheapest one will work for this (Regular SSD, ~$6 per month). Create your droplet on a server relatively close to you for lower latency.
4. Enter the droplet's console/terminal using either the web interface or your own computer. From here, run these two commands: `sudo apt-get update` and `sudo apt-get upgrade`.
5. Run the commands: 
    * `sudo apt install python3-pip` 
    * `pip3 install pandas`
    * `pip3 install alpaca_trade_api`
    * `sudo apt install npm`
    * `sudo npm install pm2@latest -g`
    * `cd AlpacaStockBot`
    * `pm2 start main.py --interpreter=python3`
6. Follow any more prompts, and list running instances with the command `pm2 list`. Follow the logging of the bot with `pm2 logs`. 
7. You may now safely exit the bot and monitor the trades from your Alpaca interface.

## Extra Info
After the bot starts, the **ORDERS** folder will populate with three spreadsheet (CSV) files.
1. Orders.csv: CSV file with all the trades (buy and sell both) placed by the bot
2. Open Orders.csv: CSV file with all the open positions held by the bot. The bot will check for returns using this file and take action based on any take profits or stop losses listed.
3. Time and Coins.csv: This file will ensure that no 2 (or more) trades are placed for the same ticker in the _sleep_time_between_trades_ period (see `configfile.txt`)

Contact me at [grahamzemel.com](https://grahamzemel.com/contact) with questions/suggestions, or reach out to the original creator at tejas.linge101@gmail.com. Thanks!
