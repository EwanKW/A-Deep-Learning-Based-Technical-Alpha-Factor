# A-Deep-Learning-Based-Technical-Alpha-Factor

- The factor is identified and computed using an LSTM deep neural network. The network receives input from a stock's profile, which comprises a recent trend relative to the market. This profile is made up of a $1\times10\times7$ three-dimensional tensor. The tensor contains time-series data of seven features: standardized (relative) volume, amount, turnover, open price change, high price change, low price change, and close price change, over the most recent 10 transaction days (2 weeks). The output is a predicted value of the stock's standardized excess return. This method closely resembles the work of technical analysts, which examines a stock's recent price trend to predict future performance.
- The network was trained using the market data of all tickers (about 5000 in total) in the Chinese A-share market from November 1, 2021, to March 1, 2022. It was trained to predict their daily forward return based on their profiles. The score output by the trained network is used as the alpha factor with daily frequency.
- I tested the factor's explainability to return and its stability from March 1, 2022, to May 1, 2022. The factor is quite effective with an **average information coefficient of 0.07**, an **information ratio of 0.91**, good monotonicity in stock selection, and **annualized Sharpe ratios of 2.66 for a long portfolio** (14.48 for a long-short portfolio).

**Statistical Testing Metrics**
| Mean IC | IC std | ICIR | Proportion that IC > 0 | Proportion that abs(IC) > 0.02 | Mean RankIC | RankIC std | RankICIR | Proportion that RankIC > 0 | Proportion that abs(RankIC) > 0.02 | abs(t-value) mean | Proportion that abs(t-value) > 1.96 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0.0737 | 0.0808 | 0.9126 | 81.21% | 85.91% | 0.0863 | 0.1047 | 0.8241 | 78.52% | 89.26% | 5.8454 | 83.89% |

**Portfolio Performance Metrics**
| Portfolio          | Average Daily Return | Annualized Cumulative Return | Annualized Sharpe Ratio | Maximum Drawdown | Hit Rate |
|--------------------|----------------------|------------------------------|-------------------------|------------------|----------|
| Long Portfolio     | 0.21%                | 68.0%                        | 2.66                    | -93.1%           | 59.1%    |
| Short Portfolio   | 0.21%                | 66.9%                        | 2.69                    | -94.1%           | 51.7%    |
| Long-Short Portfolio | 0.21%              | 70.7%                        | 14.48                   | -98.9%           | 84.6%    |


Since the data is confidential, I regret that I cannot provide all of it. However, the structure of the data is shown in the notebook, so you can use this framework with your own data. The model parameters are attached.
