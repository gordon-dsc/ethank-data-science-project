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
variables but did not improve model predictivity over the much simpler AR 2 form. Finally AR 5
and AR 6 breakout several of the top journal columns under which the headline sentiment data
was published. Model AR 5 incorporates all daily_sent variables as well as previous day's
pe_ratio and achieves the highest model predictivity shown by adjusted R squared at 0.992. Model
AR 6 removes the previous pe_ratio term to better explore the relationships between the journal
columns. This model shows statistical significance on the journal columns titled: Markets, World,
Politics, and Tech implying they might have a larger impact on changes in valuations than articles
published under other columns


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
1) Start with import.qmd file
- Download to data/imported_data the S&P 500 data from investing.com over the time period Jan 1, 2015 to Dec 31, 2024 (https://www.investing.com/indices/us-spx-500-histroical-data)
- Run all code chunks in import.qmd file following written instructions
- Code will scrape Wall Street Journal data & price to earnings data from WSJ archives and multpl.com
- Write all imported data files to data/imported_data

    -   Step-by-step instructions that make it possible for a person unfamiliar with your project to reproduce the final_data.csv file

    -   These instructions should walk through the documentation map, clearly outlining the relationships between scripts and files (e.g., the data/imported_data/example.csv file is passed into scripts/cleaning.qmd to produce final_data.csv)


## Old README instructions
The organizational structure (i.e., the specific way in which the files are nested within folders) of this repository is based on Project TIER's Documentation Protocol (version 4.0). [Project TIER](https://www.projecttier.org) (Teaching Integrity in Empirical Research), based out of Haverford College, is a multidisciplinary initiative created to promote reproducible data workflows in undergraduate curricula. In addition to hosting pedagogical training workshops for educators, Project TIER also maintains a guide, called the [TIER Protocol](https://www.projecttier.org/tier-protocol/protocol-4-0/), that outlines best practices in reproducible analysis. While this repository template takes considerable inspiration from the TIER Protocol, it differs in a couple key ways:

1.  It simplifies the TIER Protocol in a way that is commensurate with the scope of the class project it is associated with.

2.  It forgoes the nomenclature introduced by TIER Protocol 4.0 in favor of file names that more consistently align with the terminology introduced in our textbook, [R for Data Science (2e)](https://r4ds.hadley.nz).

## Template organization and function

The following directory tree (based on TIER Protocol 4.0) provides a simple visualization of the template's organizational structure.

-   project/

    -   README.md

    -   example_analysis.qmd

    -   data/

        -   imported_data/

            -   metadata/

                -   source.txt

                -   codebook.txt

        -   cleaned_data/

            -   metadata/

                -   source.txt

                -   codebook.txt

    -   scripts/

        -   import.qmd

        -   cleaning.qmd

        -   exploration.qmd

    -   output/

        -   final_data.csv

### README.md

Well would you look at that, you're reading through the README.md file right now! I bet you can even intuit a bit of the purpose of this document based on what you've read so far. In short, the README.md file is the "user manual" for your project. Because it functions to summarize the project, the README.md is the last document written. It is composed of three sections:

1.  Software and platform

    -   Software (R, RStudio, Git) and packages (e.g., httr2, rvest, tidyr, etc.) including version numbers

    -   Platform (Windows, macOS) including version numbers

2.  Documentation map

    -   A map of your directory tree (see the example above) that includes all files and folder in your project

3.  Instructions for reproducing your work

    -   Step-by-step instructions that make it possible for a person unfamiliar with your project to reproduce the final_data.csv file

    -   These instructions should walk through the documentation map, clearly outlining the relationships between scripts and files (e.g., the data/imported_data/example.csv file is passed into scripts/cleaning.qmd to produce final_data.csv)

### example_analysis.qmd

Project products are given at the top-level (i.e., not nested within sub-folders) of the repository. In most cases, the major product will be some sort of report that incorporates exploration, visualization and modeling to address a problem or answer a question. In the context of this project, there is no such report --- the brief example analysis notebook that accompanies and illustrates the utility of final_data.csv is "standing in" for this summative document.

### The data/ folder

The data/ folder contains two sub-folders: (1) imported_data/ and (2) cleaned_data/. The imported_data/ folder will contain the data (as uncleaned R object files) you've gathered through API queries and web scraping. The cleaned_data/ folder will contain the dataset(s) that has/have been processed by the scripts/cleaning.qmd file.

### The scripts/ folder

The scripts/ folder contains three Quarto notebooks: (1) import.qmd, (2) cleaning.qmd, and (3) exploration.qmd. All code related to the import of data (i.e., your `{httr2}` and `{rvest}` code) should be **well-annotated** and organized within import.qmd. All cleaning activities (e.g., rectangling, reshaping, parsing, coercion, recoding, etc.) should be well-annotated and organized within cleaning.qmd. Finally, a thoughtful exploration of the data should appear in exploration.qmd (again, well-annotated and organized).

### The output/ folder

In a more complete workflow, this folder would hold all of the images and tables corresponding to the visualizations and model results generated by the analysis. These figures and tables would then be incorporated into the final report. In the context of this project, the folder will contain only one or two files corresponding to your final_data.csv files(s).

## How to use this template

### Folders

Please do not add, nor subtract any folders from this repository. I'll ask that you not change their names.

### Scripts

You should populate the existing Quarto notebooks with well-annotated and organized code related to the purpose/focus indicated in their file name.

### Data

The "final_data.csv" file is just a placeholder. You should delete this file once you've populated the "output/" folder with actual data

### Metadata

You will need to create separate metadata files for each dataset you store in "data/imported_data/" and "data/cleaned_data/". Each metadata file should be named with a prefix that indicates the the data file it is associated with. Note that there is no "codebook.txt" file in "data/imported_data". This is because the data stored in this folder will not have yet been rectangled, and so lacks the organized column structure needed to produce a codebook.
