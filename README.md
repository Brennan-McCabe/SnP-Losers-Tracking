# S&P-Losers-Tracking
I read an article claiming that companies removed from the S&P500 outperform the index by 5% on average in the 5 years following their removal and I wanted to take a look.

To go about calculating this, I scraped S&P historical data from wikipedia and imported data from yfinance, cleaned the data in pandas, and ran everything through polars. Due to Wiki and Yahoo's handling of de-listed stocks, 158 of the 373 potential stocks were not factored into the calculations. It's possible to include the de-listed stocks, but it requires access to premium services. I have reached out to my university's business school to see about gaining that access.

To get a real idea for the returns, I wanted data from before, during, and after the removal to see the full trend. I accumulated data for t-1 year, t-30 days, t-10 days, t-5 days, t+5 days, t+10 days, t+30 days, t+1 year, and t+5 years for each of the still-listed stocks removed from the S&P to see what the results bore.

To clarify, t-1 year means buying a stock 365 days before its removal date from the S&P 500 and holding it until the day of its removal. T+1 year would mean buying on the day of the removal and holding for 365 days.

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


**Analysis:**

The data shows the article was completely off-base and there was not only no positive correlation, but a strong negative correlation that indicates you should actually short stocks that fall off the S&P 500. I need to acknowledge that my data is incomplete as 158 of the 373 stocks were excluded, but the logical conclusion is that stocks that were trending downward and became de-listed did so due to underperformance, not exceeding the market. If the missing stocks were added, the expectation would be that the numbers would look even worse.

With that in mind, let's revisit the article and see why they made their claim and how. Well, actually, I'm going to check out the research paper on which the article was based:

https://www.researchaffiliates.com/content/dam/ra/publications/pdf/1043-nixed-the-upside-of-getting-dumped.pdf

There are some key details that the original article left out.

1. The returns are benchmarked against the Russell 2000, not the S&P 500. The article makes the argument the stocks drop out of the S&P 500 and also often the Russell 1000, so they belong in the Russell 2000 and should be compared accordingly. Further down in the article, there is a figure with the deletions plotted against the Russell 2000, 1000, S&P 500, and Nasdaq 100. The claim is that the deletions beat everything except the Nasdaq from 1990-2022. Including data to 2024, the S&P and Russell 1000 both surpassed the deletions index.

2. The stocks that make up the index include deletions from the Nasdaq 100, S&P 500, and Russell 1000, not just the S&P 500. This changes the very essence of the question. A stock that fell from the Nasdaq 100 could still be a top performer. It may even return and still be part of the "Deletions" index. On the other end of the spectrum, the Russell 1000 filters through many many more stocks than the other included indices.

3. The index includes portfolio rebalancing where as my model has a strict buy and hold protocol. Rebalancing the portfolio drastically changes the arithmetic. Being allowed to drop the dead weight and add more to winners changes this from a passive fund to an actively managed fund, yet the paper also explicitly excludes taxes and fees.

**Conclusion:**

The obvious conclusion is that the article I read was poorly sourced. They fundamentally misunderstood the research paper their article was based on and posed a seemingly preposterous claim that turned out to be just that. Research Affiliates created an interesting project that led to an actively traded index (NIXT), and while their claim that the index outperforms seems optimistic, it was true when they said it.

**Technicals:**

**Python stack:**

Polars, Pandas, numpy, scipy, yfinance, contextlib, matplotlib.pyplot

**data sources:**

https://en.wikipedia.org/wiki/List_of_S%26P_500_companies

Yahoo Finance

**Next:**

I think I'm done with this for now.
