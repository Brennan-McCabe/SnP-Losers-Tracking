# S&P-Losers-Tracking
I read an article claiming that companies removed from the S&P500 outperform the index by 5% on average in the 5 years following their removal and I wanted to take a look.

To go about calculating this, I scraped S&P historical data from wikipedia and imported data from yfinance, cleaned the data in pandas, and ran everything through polars. Due to Wiki and Yahoo's handling of de-listed stocks, 218 of the 373 potential stocks were not factored into the calculations. It's possible to include the de-listed stocks, but it requires access to premium services. I can reach out to RBS about WRDS for CRSP data, but that can be added later.

To get a real idea for the returns, I wanted data from before, during, and after the delisting to see the full trend. I accumulated data for t-1 year, t-30 days, t-10 days, t-5 days, t+5 days, t+10 days, t+30 days, t+1 year, and t+5 years for each of the still-listed stocks removed from the S&P to see what the results bore.

Results of initial testing:

219 stocks excluded due to de-listing, 154 stocks used in calculations.    

=== S&P 500 Index Deletion Stats (Total Return) ===

| Holding Period | Sample Size (N) | Average Alpha vs SPY |
| :--- | :--- | :--- |
| **-1 Year** | 154 | +12.36% |
| **-30 Days** | 154 | -1.78% |
| **-10 Days** | 154 | -2.11% |
| **-5 Days** | 154 | -0.73% |
| **+5 Days** | 154 | +0.60% |
| **+10 Days** | 154 | +0.64% |
| **+30 Days** | 150 | +3.89% |
| **+1 Year** | 139 | +2.99% |
| **+5 Years** | 86 | -9.20% |

Breaking down the data:

First, let's acknowledge the -1 year alpha. +12.36 is an obvious outlier and it can be caused by a few different reasons. The top candidate is the survivorship bias. By excluding all companies that were de-listed, there's an inherent bias towards companies that are healthy, but dropped off of the S&P for various reasons. I suspect running the numbers with the full data would show a deeply negative correlation. If you magically knew the stocks that were going to be removed from the S&P, but would survive long-term following their removal and bought them a year in advance of said removal, the return for that batch would be on average 12.4% above the S&P return. The other pre-cognitive returns are all negative even with the bias in place.

The thirty day holding period stands out as the most actionable, but let's keep the survivorship bias in mind before trading on this. 

The thesis of this project and the impetus was that the 5 year holding period outperformed SPY by 5%, but the end result is not consistent with that. My calculated Alpha over a 5 year period is -9.2% and of course that's before considering that 219 of the 373 possible stocks were de-listed and excluded from the calculations. There is a possibility that the de-listed stocks were acquired, or went private and caused a boon for the investors, but the reasonable assumption is that a company trending downwards that was later de-listed did so because it was underperforming the market, not overperforming. I'll need access to higher quality data to dig further into that.

Technicals:

Python stack:

Polars, Pandas, yfinance, contextlib, matplotlib.pyplot

data sources:

https://en.wikipedia.org/wiki/List_of_S%26P_500_companies

Yahoo Finance

Next:

Without higher quality data on de-listed companies, the results are inconclusive, but lean against the proposed 5% alpha. I can reach out to RBS to see if they'll grant me access.

I'd like to take a closer look at that 30 day holding period and see what the more granular data has to say.

If I could look into the fundamentals of the companies that were removed from the S&P and find correlations between those that did well following removal or those that didn't, the results might be more actionable.
