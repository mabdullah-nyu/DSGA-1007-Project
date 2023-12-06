**Motivation:**
NYC is one of the primary food bastions of the world, yet not impermeable to online critique. In this way, food rating aggregators like Yelp manage to guide diners in a fairly unbiased manner, capturing mass sentiment for various restaurants. 

Our group was interested in the potential delta in Michelin vs non-Michelin restaurants across various Yelp attributes; Michelin has a highly furtive rating process and the criteria to succeed isn't always clear.  

Essentially, what features is a Michelin likely to over-index across? What words are most mentioned in a Michelin review v.s. not? From this, can we identify some non-Michelins that are most similar to Michelins (based on reviews)? 

More here: https://docs.google.com/presentation/d/1afD-9xyWKtQFVYMLrtO4hDgY-wIxS76vucMuQQThPaE/edit?usp=sharing

**Methodology**

We use 2 original data sets—Yelp restaurant data ($$$, hours of operation, cuisine etc.) and restaurant reviews data (top 50 recent reviews for each restaurant). 

Some considerations: Scale and API rate limiting was a big factor in our project design. We set the following constraints, only pulling data for Manhattan proper. This still queries 10K+ restaurants, so we additionally limited reviews to <= 50 reviews (vs pulling all). Accordingly, many of the fetched reviews are recent, so we also subset Michelins vs non-Michelins across Michelin 2023* restaurants specifically. 

For this project, we implemented the below phasing/framework: 

1. Obtain: Scrape the API for restaurant + review datasets. 
2. Scrub: Preprocess our data & feature engineering — changing to appropriate datatypes, removing unnecessary data/columns, and reformatting data.
3. EDA:  Deep dive through visualizations to better understand our data. 
4. Model: Build a classification model, NLP analysis, & TF-IDF analysis for further insights. 
5. Interpret: Our story! 


**File Summary**

*Pre-work*:
- scrape.ipynb: Script to scrape restaurant Yelp data for Manhattan properties—contains up to 50 most recent reviews per property. For each review, we also pull reviewer status (Yelp Elite/not), photo upload counts, & other "status" metrics that can help ascertain reviewer "credibility". We also established a dictionary of 2023 Manhattan Michelin aliases/ids — so we can subset our data by Michelin vs non-Michelin.
- data_processing.ipynb: Taking the data we got from scrape.ipynb and flattening it into reusable CSVs. 

*Data*:
- restaurants.json: Basic restaurant Yelp data for Manhattan properties—contains attributes like business alias/id, price, cuisine, longitude, & latitude i.a. 
	-restaurant_details.csv: restaurants.json CSV via data_processing.ipynb.
- reviews: Results of scrape.ipynb. Folder containing alphabetized review data; must do methodology as one review file would be >100MB.
	-restaurant_reviews: all reviews in reviews folder aggregated into a CSV via data_processing.ipynb. This file is too big to upload to Github so please download it by running data_processing.ipynb.

*Analysis*:  
- EDA_numerical.ipynb
- classification.ipynb
- NLP_analysis.ipynb: Script to apply the VADER framework to review text, returning sentiment scores/classes for review data. Word and bi-gram frequencies are compared across Michelin/non-Michelin restaurants, both in general and on positive/negative review sentiment subsets. Significance test infer effects of word and bi-gram frequencies between Michelin/non-Michelin restaurants, both in general and in positive sentiment cases. Word clouds, bar charts, boxplots, and histograms are used to test, evaluate, and justify our results.
- tfidf_model.ipynb 	     
