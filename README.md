# Data Science Research Project

## Introduction
The stock market is a critical component of the US economy providing opportunities for
companies to raise capital and investors to purchase ownership. A primary function of the
markets is pricing companies listed for trade. For the most part this goal is efficiently
achieved. However the stock market, like any market, is driven by the forces of supply
and demand. Investor sentiment (feelings on the market) whether good or bad can cause 
the market to drift from “correct” fundamentally sound valuations creating opportunities 
for traders to substantially profit from corrections when prices revert back to fundamental valuations. 
This study explores whether news headlines from Wall Street Journal have any effect on broad S&P 500 
valuations over the ten years from 2015 – 2024. If any significant effect exists it can be
incorporating into decision processes to more accurately assess investment opportunity or 
capitalize on windows of opportunities.

## Software and Platform
The following is a list of all software (versions) used in this project:
- R (4.3.2)
- RStudio (2024.12.0+467)
- git (2.39.3 Apple Git-146)
- tidyverse (2.0.0)
- rvest (1.0.4)
- chromote (0.5.1)
- sentimentr (2.9.0)
- stargazer (5.2.3)
- AER (1.2-14)
- dynlm (0.3-6)

The following is the plaform used to run the software
- x86_64-apple-darwin20 (64-bit)
- macOS Sequoia 15.4.1

## Documentation Map

Map of your directory tree including all files and folder in this project

-   project/

    -   README.md

    -   data/

        -   imported_data/

            -   S&P 500 Historical Data.csv
         
            -   full_wsj_data.csv
         
            -   pe_ratio.csv
         
            -   spy_data.csv
         
            -   wsj_data_1.csv
         
            -   wsj_data_2.csv
         
            -   wsj_data_3.csv
         
            -   wsj_data_4.csv
         
            -   wsj_data_5.csv
         
            -   wsj_data_6.csv
         
            -   wsj_data_7.csv
         
            -   wsj_data_8.csv
         
            -   wsj_data_9.csv
         
            -   wsj_data_10.csv
         
            -   metadata/

                -   source.txt

                -   codebook.txt
             
                -   

        -   cleaned_data/

            -   full_data.csv
         
            -   pe_data.csv
         
            -   wsj_data_sent.csv
         
            -   metadata/

                -   source.txt

                -   codebook.txt

    -   output/

        -   .DS_Store

        -   articles_by_day_of_week.pdf
     
        -   bic_frame.csv
     
        -   change_pre_ratio.pdf
     
        -   change_pe_vs_daily_sent.pdf
     
        -   data_summary.txt
     
        -   de-trended_monthly_pe_histogram.pdf
     
        -   de-trended_monthly_pe_line.pdf
     
        -   de-trended_weekly_pe_histogram.pdf
     
        -   de-trended_weekly_pe_line.pdf
     
        -   distribution_of_daily_sent.pdf
     
        -   full_data_sec.csv
     
        -   models_summary_4.0.txt
     
        -   pe_ratio_&_moving_averages.pdf
     
        -   pe_ratio_over_time.pdf
     
        -   pe_ratio_vs_daily_sent.pdf

        -   variable_correlation_heat_map.pdf

    -   scripts/

        -   cleaning.qmd
     
        -   exploration_and_modeling.qmd
     
        -   import.qmd

## Conclusion
Results provide some answers to the question of how sentiment in news headlines from the WSJ
affects changes in market valuations, the PE ratios, for the S&P 500. Starting with the first 
regression model, LM 1, the positive and statistically significant coefficient of the daily_sent 
variable to a p-value of less than 0.01 indicates with relatively strong confidence that positive 
news is connected to higher PE ratios. This result suggests that when the news is optimistic the 
market valuations inflate relative to the economic fundamentals however fails to prove causality as
the daily_sent and pe_ratio data values occur at the same time. The low R squared value of 0.005 from 
LM 1 suggests that while the relationship between sentiment and valuations is present and significant 
it accounts for only small variations in market valuations as most of the change is driven by variables
not accounted for in this analysis. The second model, LM 2, seeks to prove causality by using the 
daily_sent value from the day before to show that sentiment affects the next pe_ratio. The sentiment
variable coefficient is little changes and still both positively correlated and statistically
significant to a p-value of less than 0.01 proving a causal relationship. The adjusted R squared
value was little change at 0.004 as there are still many omitted variables unaccounted for. Next, 
the auto regression models seek to incorporate the temporal nature of pe_ratio valuations.
Model AR 1 and AR 2 examine the differences in model accuracy at various utilizing different amounts
of previous pe_ratio values as dependent variables. AR 1 uses the previous 4 pe_ratios as the optimal
number calculated by the Bayesian information criterion formula. Model AR 2 uses the simple form of just
the previous value of pe_ratio. Both models showed greatly improved predictive accuracy and while AR 1 is 
technically more optimal the marginal improvement in accuracy is not worth the added complexity vs 
the model form of AR 1. Statistically significance on the lag terms of both AR 1 and AR 2 indicate recent
valuations have a large impact on current valuations. Interestingly statistical significance fell
dramatically for the daily_sent variable implying that fluctuations in valuations caused by news
sentiment has a more immediate effect that does not last more than a couple days. The adjusted R
squared value increased to an impressive 0.995. Models AR 3 and AR 4 utilized a de-trending approach on 
both the dependent pe_ratio variable and lagged pe_ratio independent variable on weekly and monthly
time frames. Both models showed statistical significance on de-trended and lagged independent 
variables but did not improve model predictivity over the much simpler AR 2 form. Finally AR 5 breakouts
several of the top journal columns under which the headline sentiment datawas published. 
Model AR 5 incorporates all daily_sent variables as well as previous day's
pe_ratio and achieves the highest model predictivity shown by adjusted R squared at 0.992. To continue
the sectional analysis a BIC framework was constructed to compare five of the most promising
journal columns: Business, Markets, Politics, Review and Outlook, and Tech. Only data observations
that contained daily_sent information for all of these journal columns could be used for this BIC 
framework so the number of observations was reduced to 1825 from the full 2516. The framework 
resulted in little difference between these journal columns but in order from least BIC value
(best model) to highest BIC value: Politics, Review and Outlook, Business, Markets, and Tech. 

This study presents evidence that news sentiment proxied by the WSJ headlines has a
statically significant effect on market valuations, proxied by the S&P 500 PE ratio. This supports
the hypothesis that investor behavior is at least in part affected by how information is portrayed
to them. Notably the drifts in valuations caused by the sentiment last for very short periods of
time implying that any short-term trader would benefit from conducting new sentiment analysis
when conducting investment choices but is not a useful metric when investing on a long-term
horizon.

While conclusions can be made, this study examines only one of the countless
nuances that impact changes in the stock market. One major threat to validly is the lack of a
control present to account for changes in valuations driven by fundamental shifts in economic
conditions. Numerous omitted variables exist that together could provide such a control but is
well beyond the scope of this study. Additionally, this study focused on macro level news of one
major source, all article published in the WSJ for ten years. Further research could incorporate
more news outlets or social media posts over a long period of time to repeat the macro level
sentiment analysis or could examine industry or sector specific sources to evaluate how focused
sentiment changes valuations at the company or sector level.

## How to Reproduce
Follow these instructions to replicate the workflow of the project:
1) Start with scripts/import.qmd file
- Download to data/imported_data the S&P 500 data from investing.com over the time period Jan 1, 2015 to Dec 31, 2024 (https://www.investing.com/indices/us-spx-500-histroical-data)
- Run all code chunks in import.qmd file following written instructions
- Code will:
    - scrape Wall Street Journal data & price to earnings data from WSJ archives and multpl.com
    -  Write all imported data files to data/imported_data
2) Move to scripts/cleaning.qmd
- Run all code chunks in the cleaning.qmd file following written instructions
- Code will:
    - read in data from data/imported_data
    - clean data by changing column data types and generating data points of interest such as sentiment score using sentimentr package
    - combine all data files into data/cleaned_data/full_data.csv
    - write all cleaned data files to data/cleaned_data/
3) End with scripts/exploration_and_modeling.qmd
- Run all code chunks in the exploration_and_modeling.qmd file following written instructions
- Code will:
    - Imported cleaned data files from data/cleaned_data/ for analysis
    - Visually explore relationships between variables storing graphs in output/
    - Generate table to summarize data file and store in output/
    - Numerically explore relationships ultizing linear and auto regression models
        - Generate diagnostic graphs to check assumptions required for linear model validity
        - Generate output table that compares summary statistics for all models generated in analysis, save table to output/
