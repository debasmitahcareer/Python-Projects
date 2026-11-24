# When a company report better Earnings Changes, does the stock also perform better around earnings announcements?

**Author:** Debasmita Halder · BAN 4550, Fall 2026 · Industry: SIC 49, Electric, Gas \& Sanitary Services · Comparison industry: SIC 62, Securities & Commodity Brokers

## The question

Duke Energy wants to know whether an improvement in earnings per share (EPS) is linked to a better stock market reaction near its earnings announcement date. I looked at Duke's industry and compared it with the Securities and Commodities industry.

## Main result

In both industries, the group with higher EPS changes had better average three day abnormal stock returns (CAR) than the group with lower EPS changes. For SIC 49, the High group had an average CAR of +0.99% and   -0.39% for the Low group. The difference was 1.38 percentage points. For SIC 62, the difference was 2.82 percentage points.

I used the data from 2021-2024. In this timeframe ,Duke's Industry SIC 49  used 1,610 announcements from 118 companies. The Low, Middle, and High groups had 537, 536, and 537 announcements. SIC 62 had 936 announcements from 67 companies, with 312 in each group.

![Figure 1](Figures/Figure1.png)

The bars show the average three day stock returns for each group. The black lines are 95% confidence intervals and n shows the number of announcements.

## Is the difference real?

I used a t-test to compare the High and Low groups in each industry. The results were:

|Result|SIC 49|SIC 62|
|-|-:|-:|
|High minus Low CAR|+1.38 percentage points|+2.82 percentage points|
|t-statistic|4.11|4.50|
|p-value|<0.001|<0.001|

Both p-values are below 0.05. This gives evidence that the High and Low groups have different average returns in both industries.

I also ran a simple regression with EPS change as X and three-day CAR as Y. The coefficient shows how the estimated CAR changes when EPS change increases.

|Regression result|SIC 49|SIC 62|
|-|-:|-:|
|Coefficient (b)|0.0938|0.1256|
|R-squared|1.66%|2.29%|



The coefficients are positive. For example, a 0.01 increase in price-scaled EPS change is associated with about 0.094 percentage points higher CAR in SIC 49. However, EPS changes explain only around 2% of the variation in three-day CAR. This means the relationship is positive but weak.



Each dot is one announcement. The lines show the estimated relationship for each industry. The graph is zoomed in, so some extreme observations are outside the displayed area.

![Figure 2](Figures/Figure2.png)

As another check, I limited the extreme CAR values at the 1st and 99th percentiles for Duke and it's associate industry. The coefficient became smaller in both industries, but stayed positive. This suggests extreme returns affect the original regression results.

## Why the industries differ

I checked whether the industries had different shares of announcements where EPS decreased. The shares were very similar: 41.0% in SIC 49 and 42.9% in SIC 62. This did not give a clear explanation for the difference in their stock reactions.

I then compared how much the three day abnormal returns changes. SIC 49 had a standard deviation of 5.04%, while SIC 62 had 7.53%. This shows that stock reactions varied more around earnings announcements in SIC 62. This may be related to the larger High–Low difference,but doesnot prove the reason.Then I proceed with regression analysis and it shows positive statistical relationship .It means higher EPS changes were associated with higher abnormal returns on average. 

![Figure 3](Figures/Figure3.png)

## Advice for the client

* **Business implication:** Duke Energy should explain the reasons behind its earnings results and monitor how investors react. Better EPS does not always mean the stock will outperform the market.
* **Limitation:** The study shows a relationship, not cause and effect. I compare earnings with the same quarter last year. Duke alone had only 16 announcements, which is too small data to compare and forecast as well.
* **Next questions:** Predictive: Would analyst forecasts, guidance, and interest rates help explain future stock reactions? Prescriptive: What type of earnings communication should Duke test to help investors better understand its results?

## Data

* Sources: Compustat (`comp.fundq`), CRSP (`crsp.dsf`, `crsp.dsi`) accessed through WRDS.
* CRSP link file 



Note : The main study uses earnings announcements from 2021 to 2024. 

## How the tables fit together

!\[Merge map](Figures/MergeMap.png)

I started with quarterly company financial data from Compustat and linked each company to its CRSP stock identifier. I joined earlier quarterly information to calculate EPS changes and combined daily stock returns with market returns to calculate abnormal returns. I then matched the returns to the trading days around each earnings announcement.

## How I checked the results

I checked for duplicate company-quarter records and counted how many trading-day returns were available for each announcement. I kept only announcements with all three days available for the main CAR analysis. I also checked the data from table and calculate eps and car in excel as well. 

I also checked the effect of extreme returns by comparing the original regression with a winsorized version.

As an extra analysis, I compared three days and eleven days windows and found that EPS changes explained less return variation over eleven days.So it mean Sic 62 change very frequenty near announcement days.


!\[Standard deviation](Figures/Figure4.png)

## Changes since Project 2

This table needs to be completed using the actual corrections made after Project 2. I should not list a correction unless it was a change from my submitted Project 2 notebook.

|What was wrong|How I fixed it|How the results changed|
|-|-|-|
|1.Column name changes<br />2. Add connection close at last of the code ,<br />3.Quarter calculation changed|Use the class notebook for quarter calculation|column name and quarter calculation steps are now readable.<br />|

If there were no corrections, replace the row with `None`.

## Where the code came from

I used the BAN 4550 class notebook for the WRDS queries merges, event-window calculation, t-tests, and regression method. I adapted the work for the two industries and additional checks. I also used AI assistance for explaining results(scatter plot,troubleshooting code, and ppt checking whether cover all points,regression bar betwwen induatries). 

|AI tool|Link (or PDF in docs/)|What I used it for|
|-|-|-|
|ChatGPT|\| ChatGPT | [View Conversation](https://chatgpt.com/share/6b04c8a8-6774-83e9-87f8-fdf20ae7cf55)|Code troubleshooting, explanations of statistical results,

## Files

```text
README.md
notebooks/
    Halder\_Debasmita\_Project3.ipynb
figures/
    figure1.png
    figure2.png
    figure3.png
    merge\_map.png
docs/
    Halder\_Debasmita\_Project3.pdf
```

Update the notebook and PDF filenames above to match the files actually submitted.

