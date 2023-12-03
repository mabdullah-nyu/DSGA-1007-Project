**Motivation:**
NYC is one of the primary food bastions of the world, yet not impermeable to online critique. In this way, food rating aggregators like Yelp, manage to guide diners in a fairly unbiased manner, capturing mass* sentiment for various restaurants. 

Our group was interested in the potential differential in Michelin vs non-Michelin across various Yelp attributes. 

What features best distinguish a Michelin? 

**Methodology**

- Data sets: Restaurant Yelp data ($$$, hours of operation, cuisine etc.), Reviews data: top 50 reviews for each restaurant, primary key: restaurant alias 
- Considerations: We only pull data for MANHATTAN specifically,  aggregating across ~14K restaurants. Due to mass, we also only pull 50 reviews per restaurant, instead of all the reviews. 

For this project, we follow the below phasing/framework: 


1. Obtain: Scrape the API for restaurant + review datasets. 
2. Scrub: Preprocess our data & feature engineering — changing to appropriate datatypes, removing unnecesary data/columns, and reformatting data.
3. EDA:  Deep dive through visualizations to better understand our data. 
4. Model: Build a classification model, __________, & TD-IDF analysis for further meaning. 
5. Interpret: Our story! 


**File Summary**
- restaurants.json: Basic restaurant Yelp data for Manhattan properties—contains attributes like business alias/id, price, cuisine, longitude, & latitude i.a.
- michelin restaurants aliases.ipynb: List of 2023 Manhattan Michelin Yelp aliases/ids — so we can subset our data & compare Michelin vs non-Michelin places accordingly.
- scrape.ipynb: Script to scrape restaurant Yelp data for Manhattan properties—contains up to 50 most recent reviews per property. For each review, we also pull reviewer staus (Yelp Elite/not), photo upload counts, & other "status" metrics that can help ascertain reviewer "credibility".
- reviews: Results of scrape.ipynb. Folder containing alphabetized review data; must do methodology as one review file would be >100MB.

