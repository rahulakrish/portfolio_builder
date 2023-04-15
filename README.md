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

![image](https://user-images.githubusercontent.com/108379254/232229357-bbf214bf-d2fa-4d66-a39f-4dba5a51ab96.png)

## Stock Returns

![image](https://user-images.githubusercontent.com/108379254/232229391-1e4d4396-3d5d-4140-ad45-8efd7a1cfbcb.png)

## Beta Value

![image](https://user-images.githubusercontent.com/108379254/232229415-590cc491-1090-4a1a-9f7f-9c0ed61cba72.png)

## P/E Ratio

![image](https://user-images.githubusercontent.com/108379254/232229436-f909a1bf-47f2-4709-99b2-48fc6054647d.png)

## Dividend History

![image](https://user-images.githubusercontent.com/108379254/232229457-5ac85d88-23f9-40b0-a0f7-ed965bff4f36.png)

##Observations:

1. Stock Performance: Stock is generally on an upward trend.
2. Beta Value : Less than 1.0 signifying that it is low-risk.
3. P/E ration : Around 30 highlighting that it is over valued. Perhaps it would be better to wait for the p/e to come down.
4. Dividend: Like the stock price, is on an upward trend. A nice boost to the shareholders for investing in the company.


# Time Series Modelling

To predict future performance, different time series models were devloped and their RMSE score comapred for evaluation. Eventually, the 
Facebook Prohet model on differenced data proved most effective:

![image](https://user-images.githubusercontent.com/108379254/232229507-ab0b77b8-5c77-4c0a-bd27-c66367cd0608.png)

## Forecast price of Apple('AAPL')

![image](https://user-images.githubusercontent.com/108379254/232229544-be67df58-0628-4692-835b-2994398a571e.png)


# Portfolio
If an investor is chooses to invest only in the automotive companies, here's what that would look like:

![image](https://user-images.githubusercontent.com/108379254/232229573-5ccce38b-364c-4116-9987-fa94f91d4623.png)


The investor can expect to lose money if he/she were to invest $1000 in Tesla,GM and Ford in the next year.

Now, let's diversify and choose companies from different sectors:automotive,tech and health care

![image](https://user-images.githubusercontent.com/108379254/232229602-47e2020c-abf5-4d8c-b2fb-9b64fa75524c.png)

Thus, it is clear to see the benefit of diversification.

The code also checks to see if the investment is not sufficient:

![image](https://user-images.githubusercontent.com/108379254/232229697-e5a57c45-bcaa-4c9b-8829-63bb676873f7.png)

# Conclusions

## Limitations

1. All the models are purely mathematical models and cannot take into account black swan events.
2. More sophisticated models using Deep Learning can be built to get more accurate forecasts.
3. Dividend data is not incorporated while calculating overall returns.
4. Currently, the invested amount is distributed equally amongst all the stocks.
   The amounts can be tuned based on the investor's appetite for risk.
   
 ## Recommendations
 
 1. By plugging in amounts and companies in the model, the investor can play around and maximize his/her returns.

2. Looking at the stock market in general, there was a drastic spike around 2020.
   There has not been a decline to pre-2020 levels and hence, it might be prudent to collect past data only
   from 2020 onwards rather than from all the way back to 2017.
   
   ## More Information
 - [Notebook](notebook.ipynb)
 - [Presentation](presentation.pdf)

## Repository Structure

```
├── README.md
├── notebook.ipynb
├── notebook.pdf
├── presentation.pdf 
└── repo.pdf