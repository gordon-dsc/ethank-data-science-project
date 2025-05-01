# Data Science Research Project

## Introduction
The stock market is a critical component of the US economy providing opportunities for
companies to raise capital and investors to purchase ownership. A primary function of the
markets is pricing companies listed for trade. For the most part this goal is efficiently
achieved. However the stock market, like any market, is driven by the forces of supply
and demand. Investor sentiment (feelings on the market) whether good or bad can cause 
the market to drift from “correct” fundamentally sound valuations creating opportunities 
for traders to substantially profit from corrections when prices revert back to fundamental valuations. This study explores whether
news headlines from Wall Street Journal have any effect on broad S&P 500 valuations over the
ten years from 2015 – 2024. If any significant effect exists it can be incorporating into decision
processes to more accurately assess investment opportunity or capitalize on trading windows.

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
conclusion of project - how it answers research question

## How to Reproduce

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
