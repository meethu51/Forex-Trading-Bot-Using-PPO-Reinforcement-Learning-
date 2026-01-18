# Reinforcement Learning Forex Trading Bot

## Overview

This project implements a reinforcement learning–based trading bot for the foreign exchange (Forex) market.
The system uses historical price data to train an RL agent that learns to make Buy / Sell / Hold decisions in a simulated trading environment.

The primary goal of this project is research and experimentation—to explore how reinforcement learning can be applied to financial time-series decision making, including reward design, environment modeling, and agent behavior under transaction costs.

⚠️ This project is for educational and research purposes only and is not intended for live trading or financial advice.

## Key Features

Custom Gym-style trading environment

Discrete action space: Hold / Buy / Sell

Historical backtesting using CSV price data

Technical indicator–based state representation

Separate training and evaluation pipelines

Capital tracking and basic transaction cost modeling

```bash
Project Structure
.
├── data/
│   ├── EURUSD_Candlestick_1_Hour_BID_*.csv
│   └── test_*.csv
├── indicators.py
├── trading_env.py
├── train_agent.py
├── test_agent.py
├── Requirements.txt
└── README.md
```

## File Overview

trading_env.py
Defines the custom trading environment, including:

State representation

Action handling

Reward calculation

Balance and position tracking

indicators.py
Computes technical indicators used as features in the agent’s observation space.

train_agent.py
Handles agent training on historical data.

test_agent.py
Evaluates a trained agent on unseen data.

data/
Contains historical Forex OHLC price data in CSV format.

## Data

The project uses historical EUR/USD candlestick data (hourly timeframe) stored as CSV files.

Each dataset typically contains:

Open

High

Low

Close

(Bid prices)

The training and testing datasets are time-separated to simulate realistic out-of-sample evaluation.

## Trading Environment Design
## Action Space
```sql
0 → Hold
1 → Buy
2 → Sell
```

## Observation Space

The agent observes a vector composed of:

Price-based features

Technical indicators

Current position state

The observation window slides forward one timestep at a time, mimicking real-time trading.

## Reward Function

The reward function is designed to reflect trading performance, typically based on:

Change in account balance

Profit and loss from open positions

Transaction costs (if enabled)

Note: The reward design is intentionally simple and can be extended with:

Risk penalties

Drawdown constraints

Volatility-adjusted returns

## Training

To train the agent:
```bash
python train_agent.py
```

During training:

The agent interacts with the environment step-by-step

Actions are selected according to the RL policy

Rewards are accumulated and used to update the agent

Training progress can be monitored through printed logs or balance evolution.

## Evaluation

To test a trained agent on unseen data:
```bash
python test_agent.py
```

Evaluation runs the agent in inference mode without learning and reports:

Final balance

Trade behavior

Cumulative reward

## Results

Results will vary depending on:

Hyperparameters

Reward design

Indicator selection

Market regime

No claims are made regarding profitability or robustness.

## Limitations

No live market integration

Simplified transaction cost model

No slippage or spread dynamics

No risk management constraints (e.g. max drawdown)

Single-asset trading only

This project should be viewed as a foundation, not a production system.

## Future Improvements

Potential extensions include:

Improved reward shaping (Sharpe ratio, drawdown penalties)

Risk-aware position sizing

Multi-asset or portfolio trading

Market session modeling

Transition to equity index trading (e.g. S&P 500 / SPY)

Advanced RL algorithms and ensemble agents

## Installation

Clone the repository

Install dependencies:
```bash
pip install -r Requirements.txt
```

Ensure datasets are placed in the data/ directory

## Disclaimer

This project is not financial advice.
Trading financial instruments involves substantial risk, and past performance does not guarantee future results.
The author assumes no responsibility for any losses incurred.
