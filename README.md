# S&P-Losers-Tracking
I read an article claiming that companies removed from the S&P500 outperform the index by 5% on average in the 5 years following their removal and I wanted to take a look.

To go about calculating this, I scraped S&P historical data from wikipedia and imported data from yfinance, cleaned the data in pandas, and ran everything through polars. Due to Wiki and Yahoo's handling of de-listed stocks, 158 of the 373 potential stocks were not factored into the calculations. It's possible to include the de-listed stocks, but it requires access to premium services. I can reach out to RBS about WRDS for CRSP data, but that can be added later.

To get a real idea for the returns, I wanted data from before, during, and after the delisting to see the full trend. I accumulated data for t-1 year, t-30 days, t-10 days, t-5 days, t+5 days, t+10 days, t+30 days, t+1 year, and t+5 years for each of the still-listed stocks removed from the S&P to see what the results bore.

**Results of testing:**

158 stocks excluded due to missing historical data, 215 stocks used.

### S&P 500 Index Deletion Stats: Statistical Analysis

| Period | N | Avg Alpha | Std Dev | Sharpe | P-Value | Sig? |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **-1 Year** | 177 | -5.45% | 16.45% | -0.33 | 0.000 | *** |
| **-30 Days** | 178 | -0.94% | 4.90% | -0.19 | 0.012 | ** |
| **-10 Days** | 178 | -0.55% | 3.25% | -0.17 | 0.024 | ** |
| **-5 Days** | 178 | -0.58% | 2.82% | -0.21 | 0.006 | *** |
| **+5 Days** | 178 | +0.19% | 3.76% | +0.05 | 0.504 | |
| **+10 Days** | 177 | -0.79% | 6.06% | -0.13 | 0.083 | * |
| **+30 Days** | 173 | -5.26% | 14.65% | -0.36 | 0.000 | *** |
| **+1 Year** | 157 | -48.11% | 22.83% | -2.11 | 0.000 | *** |
| **+5 Years** | 86 | -109.74% | 78.45% | -1.40 | 0.000 | *** |

> *Significance Levels: \*\*\* (p<0.01), \*\* (p<0.05), \* (p<0.10)*


**Breaking down the data:**


**Technicals:**

**Python stack:**

Polars, Pandas, numpy, scipy, yfinance, contextlib, matplotlib.pyplot

**data sources:**

https://en.wikipedia.org/wiki/List_of_S%26P_500_companies

Yahoo Finance

**Next:**

More work to be done.
