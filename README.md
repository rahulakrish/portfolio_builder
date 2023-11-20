# Objective

To help the average investor build a portfolio of stock and ensure maximum returns to achieve his/her goals. 
The aim here is to  provide the investor an overview of performance of each stock belonging to the portfolio, portfolio performance and predict future peformance based on historical data thereby helping them make an informed decision. 

This notebook is only serves as a demonstration and should not be miscontrued for financial advice. As with any investment, there is an element of risk and returns can never be guaranteed.

Optimal portfolio build will also be demonstrated using a principle called [Modern Portfolio Theory](https://en.wikipedia.org/wiki/Modern_portfolio_theory), a model introduced by economist Harry Markowtiz in 1952.  MPT advocates for diversification : owning a portfolio of assets from different classes is less risky than holding a portfolio of similar assets. By owning stock from different sectors as opposed to concetrating on a single sector, an investor is less exposed to risk.

[PyPortfoliOpt](https://pyportfolioopt.readthedocs.io/en/latest/) is a Python library that will be used for this purpose.

# Methodology

1. Data of the chosen stock from 2019-till will be scraped from [Yahoo Finance](https://finance.yahoo.com/)  using python's  `yfinance`(documentation can be found [here](https://aroussi.com/post/python-yahoo-finance) and `YahooFinancials` (documentation can be found [here](https://pypi.org/project/yahoofinancials/)).

2. Conduct EDA including stock performance, risk, growth etc. . 

3. Different machine learning models will then be built to predict future stock price. Their errors will be compared and the model with the least error will be used to predict future stock performance. 

4.  Based on predicted data, optimal portfolios will be built.

# EDA

For demonstrative purposes, let's build a porfiolio of stock of the following companies: General Electric, J.P.Morgan, Microsoft and Prcter & Gamble.

## Stock Performance

![Screenshot 2023-11-20 124528](https://github.com/rahulakrish/portfolio_builder/assets/108379254/79024d32-d8f7-4a54-b49c-c2a4cb569f9e)

### Average Daily return
Comparing the avaerage daily return of the portfolio against the S&P 500

![Screenshot 2023-11-20 124900](https://github.com/rahulakrish/portfolio_builder/assets/108379254/78d4806f-17dd-478f-95b5-b6fa7dac45cf)


### Growth
What if we invested $1000 in each stock at the beginning? What would the current value be? This will give the cumulative return of each stock

![Screenshot 2023-11-20 125050](https://github.com/rahulakrish/portfolio_builder/assets/108379254/6f91f7e0-6e1f-49d1-9256-90cd9b810610)

For MSFT, we can see that \$1000 invested in 2019 would've grown to approx. $3600, netting a cumulative return of approx. 260%!

### Portfolio Cumulative Return

Now that we've seen how the individual stocks have performed over time, similarly, we now have to see how a portfolio of these socks would've performed and compare it to the S&P 500

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/b788c675-1bd6-469f-b50c-3b1bbe5760e0)

From the graph, we can see that the cumulative return of the portfolio is approx. \$2500.
This means an initial investment of \$1000 would've grown to $2500. In terms of percentage, that equates to 150%.
The S&P 500 in comparison has grown only 75%.

## Dividend History

A Dividend is the distirbution's of the company's profit to it's shareholders. Not every company pays dividends. Companies can also choose to re-invest their profits for future growth than reward shareholders. For an investor, investing in a company that pays dividends is an easy way to earn extra income on top of their initial investment. Shown here is the dividend for MSFT

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/f242c9e3-9a40-45e6-8b2a-77b629d3ebfe)

MSFT's rising dividend yield bodes well for investors.

### Risk

#### Beta Value

Beta value of a stock is used to signify risk i.e. if a stock is risky or not. By comparing the stock movement
relative to the overall market such as the S&P 500, the stock can be classified as risky or not. By definition, the market
has a beta value of 1.0. If the beta value of the stock is greater than 1.0, then it is classified as risky and less so if the
value is less than 1.0. Shown here is the beta value of MSFT: 

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/59acc1db-7125-43f4-be0e-0afc2378eefe)

#### Portfolio Risk

Portfolio risk can be calculated using the covariance matrix.Portfolio variance takes into account individual variance, weights and their correlation.

The risk of a portfolio is not simply the weighted variance of the individual assets. Since the stocks are correlated,
it becomes more complicated. The correlation between assets tell us how they move related to each other.Hence, the risk calculated should also account for the correlation.

The standard deviation of a portfolio is a measure of its risk or volatility. It quantifies how much the returns of the portfolio tend to deviate from the average (mean) return over a specific time period. A higher standard deviation indicates greater volatility, while a lower standard deviation suggests lower volatility.

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/3a8d7dd7-be57-4fe5-9f2c-293199d5222a)

From, the matrix it is clear to see that GE (17.3%) is the most volatile stock compared to the others.

#### Interpreting risk

The high standard deviation of 23.4% signifies that the portfolio has experienced significant price or return fluctuations. These fluctuations can be both positive and negative, and they can be substantial. Investors with a lower risk tolerance may find such volatility concerning.

On the flip side, despite the high-risk profile, the portfolio has generated an impressive return of 135% over the 5 year period.

Hence, the interpretation of the portfolio's risk depends upon the investor.  Investors with a higher risk tolerance may be more comfortable with the portfolio's volatility if it leads to higher returns, while those with lower risk tolerance may find the risk level less acceptable.


## Modern Portfolio Theory

The modern portfolio theory (MPT) is a practical method for selecting investments in order to maximize their overall returns within an acceptable level of risk. This mathematical framework is used to build a portfolio of investments that maximize the amount of expected return for the collective given level of risk.

American economist Harry Markowitz pioneered this theory in his paper "Portfolio Selection," which was published in the Journal of Finance in 1952.
He was later awarded a Nobel Prize for his work on modern portfolio theory.

A key component of the MPT theory is diversification. Most investments are either high risk and high return or low risk and low return. Markowitz argued that investors could achieve their best results by choosing an optimal mix of the two based on an assessment of their individual tolerance to risk.

Source: [Modern Portfolio Theory](https://urldefense.com/v3/__https://www.investopedia.com/terms/m/modernportfoliotheory.asp__;!!MvWE!A8D_jcz9THgiMXgFsXMRvyYcgjSYKFhsDBtsLLrfeoCrX24cQF5tnVpx8eat9vHSIrZxytGZ2FcSWhMtzNT4h6BJfA$">https://www.investopedia.com/terms/m/modernportfoliotheory.asp)

### PyPortfolioOpt

PyPortfolioOpt is a library that implements portfolio optimization methods, including classical mean-variance optimization techniques and Black-Litterman allocation, as well as more recent developments in the field like shrinkage and Hierarchical Risk Parity.

More information can be found [here](https://urldefense.com/v3/__https://pyportfolioopt.readthedocs.io/en/latest/UserGuide.html__;!!MvWE!A8D_jcz9THgiMXgFsXMRvyYcgjSYKFhsDBtsLLrfeoCrX24cQF5tnVpx8eat9vHSIrZxytGZ2FcSWhMtzNSr676PzQ$">https://pyportfolioopt.readthedocs.io/en/latest/UserGuide.html) and [here](https://urldefense.com/v3/__https://github.com/robertmartin8/PyPortfolioOpt*an-overview-of-classical-portfolio-optimization-methods__;Iw!!MvWE!A8D_jcz9THgiMXgFsXMRvyYcgjSYKFhsDBtsLLrfeoCrX24cQF5tnVpx8eat9vHSIrZxytGZ2FcSWhMtzNThKKJu4Q$">https://github.com/robertmartin8/PyPortfolioOpt#an-overview-of-classical-portfolio-optimization-methods)

We will be using PyPortfolioOpt to optimize our portfolio.

### Efficient Frontier

is a graphical representation of portfolio risk(standard deviation) vs return.

- At every level of return, investors can create a portfolio that offers the lowest possible risk.
- For every level of risk, investors can create a portfolio that offers the highest return.

- Any portfolio that falls outside the Efficient Frontier is considered sub-optimal for one of two reasons: it carries too much risk relative to its return, or too little return relative to its risk.

#### Efficient Frontier for Max Sharpe

The Sharpe Ratio is a measure of risk-adjusted performance for an investment or a portfolio. Simply put, the Sharpe Ratio calculates the excess return per unit of risk. A higher Sharpe Ratio indicates a better risk-adjusted performance. Investors generally prefer investments or portfolios with higher Sharpe Ratios because they provide a better return for the amount of risk taken.

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/64c58d98-35da-424a-a978-19f8f08e5ab7)

#### Efficient Frontier for Min Volatility

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/e275341e-7c9e-4457-a1fe-5230c57102d3)

We can see how the two approaches produce different results. PyPortfolioOpt offers more options to customize a portfolio.

### How to optimally allocate the money based on the weights?

Based on the weights, latest price and amount invested, the next step is to ensure that the amount invested is maximized for each asset's allocated weight.

For eg. if the stock price of GE is \$100 and the total amount invested is \$1000, per the allocation, we have to invest 4.8% in GE which equates to \$48.

We use the DiscreteAllocation class for this. It prioritzies buying shares of the asset that is furthest away from the allocation i.e if the portfolio calls for bying 10 shares of an asset, but with the allocation we have only 10 shares, the other asset allocations are sacrificed to reduce the gap. This way, the left over money is minimized.

We will be using \$1800 as an example and like earlier compare portfolios for max sharpe and min volatility.

Max Sharpe:

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/3c51793a-57da-4481-b11c-41eba3307207)

Min Volatility

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/e22a4eb2-9032-4229-8b58-b085169d7a43)

# Future price prediction - Time Series Modeling

Now that we have some insight on each stock and how to optimally build a portfolio, the next step is to predict future performance of the stocks that we want for our portfolio.

To make predictions, we will build a series of time-series models and select the model with the least RMSE.

We will be using 'AAPL' data for demonstrative purposes

### Stationarity Check

Time series models are usually built on the premise that models are stationary i.e there are patters to the data and by analyzing these patterns, future performance can be predicted with a degree of certainity. However, this rarely happens in real life. There is always some trend or seasonality or a combination of both in the data.Hence the first step is to check for stationarity and then convert non-stationary to stationary data.


![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/d9090df8-20d2-4853-9971-17d91cd5e5b1)

By simply taking the difference, we can remove non-stationarity from the data set. We can see from the above plot that the mean though not perfectly flat is fairly linear signifying that we have removed the trend.
Since the p-value from the Dickey-Fuller is lesser than the significance value, we can reject the null-hypothesis and thus conclude that the data is now stationary.

### Model predictions

Next step is to build different models to predict future price and select the model with the least RMSE

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/a092ceb4-d8cb-4eb8-8d4d-1719904c1669)

From the plot, we can see that the FB Prophet model clearly outshines the rest with a RMSE score of $5.12 . Hence, we will use that for making predictions for stocks in our portfolio.

Predicting, the price of AAPL for the next year:

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/c08c0da1-03ab-4511-bb02-59e11cb68512)

## Building Portfolio

Shown here is the predicted price of another stock in the portfolio: Procter & Gamble (PG)

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/e0a8f45f-aeb0-4d46-9a2f-6de35a983212)

### Predictions of portfolio

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/e60992c3-25f3-482f-95db-8c144bc5134c)

### Applying Modern Portfolio Theory

We now need to calculate the efficient frontier for max_sharpe and min_volatilty based on our predictions

#### Max Sharpe

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/6c87cebe-a9ae-4918-be58-29b4caf7140e)

From the above, we can see that the , based on forecast returns, if we look to maximize the sharpe ratio, we can expect an annual return of 28%.

Using the same intial amount of $1800, the recommended allocation would have no investment in J.P.Morgan and the left over amount would be $38.73

#### Min Volatility

![image](https://github.com/rahulakrish/portfolio_builder/assets/108379254/d6f3e01f-d48d-4138-8b91-7803a0dddfa3)

For minimun volatility, we can see the difference in allocation when compared to the portfolio optimized for max_sharpe.

# Conclusions

1. All the models are purely mathematical models and cannot take into account black swan events.
2. Obviously, the strnegth of the forecast is goverened by the model. SHown here is only a basic model with only historical stock price used to predict future price. Clearly, more features like volume of shares, yearly income etc. and other macro economic factors can be added and more sophisticated models developed to make more wholesome and accurate predictions.
3. Similarly, the PyPfopt library optimization was done only for maximum sharpe and minimum volatility. There are more options that the user can play with to generate more portfolios.

# Appendix

### How to use the notebook:

1. Assign stocks into the following line: `portfolio,portfolio_df = stocks('GE,JPM,MSFT,PG')`. In place of 'GE,JPM,MSFT,PG', put in stocks of your choice.

2. Run the following functions to get historical portfolio data:

> * `stock_performace(portfolio)` - plot performace of each stock in the portfolio from 2019 till date.

> * `get_average_returns(portfolio)` - plot average return of the portfolio in comparision to the S&P 500.

> * `get_ind_cum_return(portfolio)` - plot hypothetical growth of $1000 invested in each stock.

> * `get_portfolio_cumulative_return(portfolio)` - plot hypothetical growth of $1000 invested in the portfolio.

> * `get_dividend(portfolio)` - plot dividend data for each stock in the portfolio

> * `calculate_beta(portfolio)` - plot each stock in the portfolio

> * `covariance(portfolio)` - plot portfolio risk

> * `hist_returns(portfolio)` - plot trends in the returns of the portfolio

> * `sharpe_df,sharpe_weights = ef_max_sharpe(portfolio_df)` - efficient frontier optimizing for max sharpe value. `sharpe_df` will output portfolio performace and `sharpe_weights` will list out optimal allocation of \$1800 in the portfolio and also the leftover money.

> * `vol_df,min_vol_weights = ef_min_volatility(portfolio_df)` - efficient frontier optimizing for min volatility.`vol_df` will output portfolio performance and `min_vol_weights` will list out optimal allocation.


*The functions listed above only plot data based on historical performance and merely serve as a guide. The following functions are to predict future performance:*

> * Assign ` forecast_portfolio = plot_forecast_price(portfolio)` and run.
This will  plot future stock price for each stock in the portfolio based on historical stock price

> * `returns_forecast(forecast_portfolio)` - plot future portfolio performance

> * `forecast_sharpe(forecast_portfolio)` - output portfolio performance and allocation optimized for max sharpe value

> forecast_volatility(forecast_portfolio) - output portfolio performance and allocation optimized for min volatility.
