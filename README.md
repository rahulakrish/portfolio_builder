# Objective

To help the average investor build a portfolio of stock and ensure maximum returns. Goals of the investor could range between short-term goals like saving for a dream vacation, down payment of a home etc. to long-term goals like saving for child's education, retirement etc.

The assumption here is that the investor already has an idea companies they want to invest in. The aim here is to  provide the investor an overview of the company performance and make predictions on future thereby helping them decide it it's worth their investment. Since the model is purely mathematical and cannot take into account black swan events, the onus still lies on the investor to look at a company holistically before taking the plunge.

I will also focus on diversification, a core tenet of a good investment strategy i.e by investing in companies across different sectors, the investor can minimize their risk and maximize returns.

# Methodology

1. Data of the chosen stock from 2017-2022 will be scraped from [Yahoo Finance](https://finance.yahoo.com/)  using python's  `yfinance`(documentation can be found [here](https://aroussi.com/post/python-yahoo-finance)) and `YahooFinancials` (documentation can be    
  found [here](https://pypi.org/project/yahoofinancials/)).

2. Using the data, 4 commonly used metrics to evaluate a stock will be plotted: ***returns, beta ratio, p/e ratio and dividend***

3. Different machine learning models will then be built to predict future stock price. Their errors will be compared and the model with the least error will be used gage future stock performance. 

4. Combined with stock performance and forecast information, then by feeding the chosen stock into the portfolio builder, the investor can look at combined returns and decide which portfolio is best-aligned with his/her goals.

# EDA

Example shown is for Apple('AAPL'). The same can be applied for any company of the investor's choice.

## Stock Performance



## Stock Returns



## Beta Value



## P/E Ratio



## Dividend History



# Time Series Modelling

To predict future performance, different time series models were devloped and their RMSE score comapred for evaluation. Eventually, the 
Facebook Prohet model on differenced data proved most effective:



## Forecast price of Apple('AAPL')



# Portfolio
If an investor is chooses to invest only in the automotive companies, here's what that would look like:



The investor can expect to lose money if he/she were to invest $1000 in Tesla,GM and Ford in the next year.

Now, let's diversify and choose companies from different sectors:automotive,tech and health care




The code checks to see if there is too little investment.
