# ctrader
Cryptotrader with React
ctrader is a Python library that provides tools for analyzing and trading financial markets, with a focus on cryptocurrency markets. It includes functionality for backtesting trading strategies, as well as live trading through supported exchanges.

Installation
To install ctrader, simply run:

bash
Copy code
pip install ctrader
Getting started
Here's a quick example of how to backtest a trading strategy using ctrader:

python
Copy code
import ctrader

# Load historical price data for Bitcoin from the Bitfinex exchange
data = ctrader.load_price_data('bitfinex', 'BTC/USD', '1d', '2018-01-01', '2021-01-01')

# Define a simple moving average crossover strategy
def sma_crossover_strategy(data):
    short_sma = data['close'].rolling(window=50).mean()
    long_sma = data['close'].rolling(window=200).mean()
    signals = (short_sma > long_sma).astype(int).diff().fillna(0)
    return signals

# Backtest the strategy using the historical data
results = ctrader.backtest_strategy(data, sma_crossover_strategy)

# Print the results
print(results)
This will output the performance metrics for the strategy, including the total return, annualized return, Sharpe ratio, and more.

Contributing
Contributions to ctrader are welcome! Please see the contribution guidelines for more information.

License
ctrader is distributed under the MIT license. See LICENSE for more information.
