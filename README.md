# S&P-Losers-Tracking
I read an article claiming that companies removed from the S&P500 outperform the index by 5% on average in the 5 years following their removal and I wanted to take a look.

To go about calculating this, I scraped S&P historical data from wikipedia and imported data from yfinance, cleaned the data in pandas, and ran everything through polars. Due to Wiki and Yahoo's handling of de-listed stocks, 218 of the 373 potential stocks were not factored into the calculations. It's possible to include the de-listed stocks, but it requires access to premium services. I can reach out to RBS about WRDS for CRSP data, but that can be added later.

To get a real idea for the returns, I wanted data from before, during, and after the delisting to see the full trend. I accumulated data for t-1 year, t-30 days, t-10 days, t-5 days, t+5 days, t+10 days, t+30 days, t+1 year, and t+5 years for each of the still-listed stocks removed from the S&P to see what the results bore.

Results of initial testing:

219 stocks excluded due to de-listing, 154 stocks used in calculations.    

=== S&P 500 Index Deletion Stats (Total Return) ===

[ -1 Year] N=154 | Avg Alpha: +12.36%

[-30 Days] N=154 | Avg Alpha: -1.78%

[-10 Days] N=154 | Avg Alpha: -2.11%

[ -5 Days] N=154 | Avg Alpha: -0.73%

[ +5 Days] N=154 | Avg Alpha: +0.60%

[+10 Days] N=154 | Avg Alpha: +0.64%

[+30 Days] N=150 | Avg Alpha: +3.89%

[ +1 Year] N=139 | Avg Alpha: +2.99%

[+5 Years] N=86 | Avg Alpha: -9.20%

Breaking down the data:

First, let's acknowledge the -1 year alpha. +12.36 is an obvious outlier and it can be caused by a few different reasons. The top candidate is the survivorship bias. By excluding all companies that were de-listed, there's an inherent bias towards companies that are healthy, but dropped off of the S&P for various reasons.

The thirty day holding period stands out as the most actionable, but let's keep the survivorship bias in mind before trading on this. 

The thesis of this project and the impetus was that the 5 year holding period outperformed SPY by 5%, but the end result is not consistent with that. My calculated Alpha over a 5 year period is -9.2% and of course that's before considering that 219 of the 373 possible stocks were de-listed and excluded from the calculations. There is a possibility that the de-listed stocks were acquired, or went private and caused a boon for the investors, but the reasonable assumption is that a company trending downwards that was later de-listed did so because it was underperforming the market, not overperforming. I'll need access to higher quality data to dig further into that.
