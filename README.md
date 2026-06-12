# Nobel_Prize_Jupyter_Notebook
Exploration of All Nobel Prize Winners and Identification of Hidden Patterns
Table of Contents

    Exploratory Data Analysis
    Findings

Project Overview

The Nobel Prize is perhaps the most recognized scientific prize ever in the world. In this regard, awards are each year bestowed in the areas of Medicine, Chemistry, Physics, Economics, Literature and Peace.

Accordingly, this comprehensive data analysis project conducted in Python is intended to examine all the Nobel Prize winners to date in an attempt to identify and explore undiscovered patterns hidden in an overarching dataset.

Alfred Nobel

Made available by the Nobel Foundation, the analysed data uncovers all prize winners from 1901 all the way to 2023.
Data Sources

The dataset used for this analysis is the "nobel_dataset.csv" file, containing detailed information about each award winner up to date, ever since the Prize was established.
Tools

    Anaconda Navigator:
        To access the Jupyter Notebook for Python

Data Preparation and Preprocessing

The following data preparation and preprocessing tasks were undertaken:

    The dataset was first inspected and then imported into two separate Pandas DataFrames.
    NaN/non-existing values of certain records within particular columns were removed in one DataFrame.
    An overhaul dictionary was designed to replace countries' former names with their current names, owing to political reasons and relevancy.
    A column named Decade was formed to be able to classify prize winners and categorise pertinent data as per 10-year periods.

Exploratory Data Analysis

EDA involved exploring the Nobel Prize data to answer key questions, including but not limited to:

    Who was the first woman ever to receive a Nobel Prize, and in what category?
    Which 10 countries have secured a Nobel Prize most up to date, and how many times?
    From which year did the country that has achieved the most Nobel Prizes up to date manage to establish dominance?
    How does the visualisation of all Nobel Prize winners appear per award category, gender and decade?
    During the Second World War, how did the award distribution per category and country look?
    During the Cold War, how did the award distribution of each country per category look?

Data Analysis

Designed to separate one-time female Nobel winners from the multiple ones, the following code helped me consolidate my Pandas DataFrame knowledge in subsetting, looping, concatenating and most importantly masking techniques.

# Bringing in only the first award record for multiple female award winners

first_of_multiple_female_winners = pd.DataFrame()

for female_winner_name in multiple_female_winners:
    
    enumerated_award_winner = multiple_female_nobel_df[(multiple_female_nobel_df['full_name'].str.contains(female_winner_name))]
    enumerated_award_winner = enumerated_award_winner[enumerated_award_winner['year'] == enumerated_award_winner['year'].min()]
    
    first_of_multiple_female_winners = pd.concat([first_of_multiple_female_winners, enumerated_award_winner], axis=0, ignore_index=True)


# Via the masking technique, preparing a DataFrame which includes all winners being awarded this Prize only for once in their lifetime

single_female_winners = female_nobel_df[~female_nobel_df['full_name'].isin(multiple_female_winners)]


# Combining the two DataFrames by Axis-0

first_all_female_winners = pd.concat([single_female_winners, 
                 first_of_multiple_female_winners], axis=0).sort_values(by=['year']).reset_index(drop=True)

Findings

The critical analysis results are summarised as follows:

    Marie Curie was the first woman ever to receive a Nobel Prize in Physics.

    The United States (US) has come out on top by winning the most Nobel Prizes by far to date, followed by the UK, Germany, France, Sweden and Russia.

    Owing to a variety of factors, including the academic freedom and expanding budget expenditure in scientific R&D endeavours as well as placing a strong focus on meritocracy, the US managed to establish its relentless dominance in terms of winning more and more Nobels, as of 1930s and onwards:

US Dominance as of 1930s

    Linked to Finding #2, the proportion of US-born award winners till 2000 was observed to be in a gradual uptrend, peaking at slightly higher than the 0.4 ratio, before dipping by nearly 25% during early 2000s:

Trend of US-born Laureates per Decade

    Statistically speaking, the Peace category has so far experienced the widest age range of Nobel Prize winners, alongside with achieving the highest dominance of a female-male ratio by 17.1% benchmarked against the other female Nobel winners in other categories:

Peace Winners per Age, Gender and Decade

On the other hand, the Economics category has experienced the oldest age range of Nobel Prize winners, along with having one of the lowest female-male ratios.

For instance, once again statistically speaking, except for the French-American economist, Esther Duflo, there is no scientists/academics up to date who are younger than 50 years old and have yet been awarded a Nobel in this field.

Economy Winners per Age, Gender and Decade

    Surrounding the Second World War, most Nobel Prizes were awarded respectively in the fields of Medicine, Chemistry and Physics. I argue that the underlying reason could be that war efforts did inherently demand and drive most research and innovation toward these three areas, considering the war economics.

Dist of NP Categories during the World War II

In addition, it was also identified that the archrival heads of the World War II, the US and Germany (Nazi Germany at the time), won the most Nobel Prizes during this era:

Dist of NP Winners' Birth Countries during the World War II
Limitations

    The presumption is that the dataset made available by DataCamp encompasses all Nobel Prize winners up to date.
    Country analysis per Nobel laureate was based upon each winner's birth country instead of the organisation country that they had worked under/for.
