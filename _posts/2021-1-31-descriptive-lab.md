---
layout: post
title: Descriptive Lab
subtitle: Country Vaccinations Analysis
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Art of Data]
---

# Data

In this lab, I worked with the country vaccinations dataset, which outlined the number of vaccinations, the proportion of people vaccianted, and the type of vaccine in each country. In a time when COVID-19 wreaks havoc across the globe, understanding quantitative information surrounding the COVID-19 vaccinations is more important than ever before. Let's dive into the data to draw conclusions about current vaccinations.

# Code

    import pandas as pd
    import matplotlib.pyplot as plt
    import seaborn as sns

    cv_path = "../sandbox/country_vaccinations.csv"
    country_vaccinations_df = pd.read_csv(cv_path)

    cv_path = country_vaccinations_df

    #Group by country to find total values for each country
    cv_path.groupby(['country']).sum()
    graph1 = sns.countplot(x="country", data=cv_path)
    plt.xticks(rotation=90)
    plt.show()
    graph2 = ax = sns.barplot(x="country", y="people_fully_vaccinated_per_hundred", data=cv_path)
    plt.xticks(rotation=90)
    plt.show()

    #Group by date to find total values for each date
    cv_path.groupby(['date']).sum()
    graph3 = sns.lineplot(data=cv_path, x="date", y="people_fully_vaccinated")
    plt.xticks(rotation=90)
    plt.show()

    #Group by vaccine to find total values for each vaccine
    cv_path.groupby(['vaccines']).sum()
    graph4 = sns.countplot(x="vaccines", data=cv_path)
    plt.xticks(rotation=90)
    plt.show()

# Methods

In my analysis, I looked at five different variables: country, date, people_fully_vaccianted_per_hundred, people_fully_vaccinated, and vaccine. There were several different conclusions to draw, so I had to determine the most important information in this dataset. I set out to answer three questions... Which countries have implemented the vaccine most effectively? What is the trend of the number of vaccines used each day? What is the most common type of vaccine used? I decided to use a variety of visualizations to answer these questions.

# Conclusions