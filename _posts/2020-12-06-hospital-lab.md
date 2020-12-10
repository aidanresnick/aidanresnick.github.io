---
layout: post
title: Hospital Lab
subtitle: Which New York county has the most hospital beds per person?
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Art of Data]
---

# Code

    import requests
    import csv

    base_url = "https://hm-cs.herokuapp.com"
    end_url = base_url + "/hospital"
    key = "ArtOfDataKEY123"
    
    #Go through each of the rows of the API
    x=0
    printResponse = True
    while printResponse is True:
        payload = {
            'key' : key,
            'id' : x
        }
        response = requests.get(end_url, params=payload)
        if response.status_code == requests.codes.ok:
            printResponse = True
            x+=1
        else:
            printResponse = False
    
    #Sum the values in a list
    def sum(list):
        sum = 0
        for i in range (0, len(list)):
            sum += list[i]
        return sum

    #Initiate a dictionary for each of the counties
    counties = {}
    #Open the csv file and go through the data
    with open('hospital_lab.csv', 'r') as f:
        data = csv.DictReader(f)
        for row in data:
            #Add each county to counties
            current_county = row['county']
            if current_county not in counties:
                counties[current_county] = []
            #Add standardized number of beds to 
            counties[current_county].append(float(row['beds']))
    
    #Sum the standardized number of beds in each county
    for i in counties:
        total = sum(counties[i])
        #Add the sum into counties
        counties[i].append(total)

    print(counties)


# Working with the Data

In this lab, I worked with initially raw data to draw a conclusion about a data set. Specifically, I was given the web API, which contained information about the number of hospital beds per person in New York counties, even though the information was initially very difficult to interpret. The first thing I did was figuring the URL. More specifically, however, I realized that by changing the id at the end of the url, it changed the row number in the data set. Once I wrote the code to go through the API data, I piped it so it could turn into a CSV.

Looking through the data set by changing the ID in the URL provided me with crucial insight into how the data was structured. I saw that there were several New York counties listed under "county" and their corresponding beds per a certain number of people. However, this number of people was not constant for every row in the data set. Thus, I needed to standardize it. To standardize it, I first thought to create a "standardize" method that could standardize the values in any list so, in this case, the data would measure hospital beds per 1,000 people for every county. However, after numerous attempts to create "if statements" that would standardize each row of the data, I decided that it would be most efficient for me to standardize manually. This was the best approach for me in this case, but I am fortunate that there were only 135 rows in the data set. In the future, I will work to figure out how to standardize this data set and other data sets in the future. Once I had the standardized data in the CSV file, I was ready to read through the data and ultimately to figure out which New York county has the most hospital beds per person!

# Process

Similar to my process in obtaining and cleaning the data, my process going through the data was primarily efficient, but there are definitely ways to improve.

# Final Answer