**Motivation:**
NYC is one of the primary food bastions of the world, yet not impermeable to online critique. In this way, food rating aggregators like Yelp, manage to guide diners in a fairly unbiased manner, capturing mass* sentiment for various restaurants. 

Our group was interested in the potential delta in Michelin vs non-Michelin across various Yelp attributes. What features is a Michelin likely to over-index across? What words are most mentioned in a Michelin review vs not? Which non-Michelins are most similar to a Michelin (based on reviews)? 

More here: https://docs.google.com/presentation/d/1afD-9xyWKtQFVYMLrtO4hDgY-wIxS76vucMuQQThPaE/edit?usp=sharing

**Methodology**

We use 2 original data sets—restaurant Yelp data ($$$, hours of operation, cuisine etc.) and each restaurant reviews data (top 50 reviews for each restaurant). Some considerations: Scale and API rate limiting was a big factor in our project design. We set the following constraints, only pulling data for Manhattan proper places (not incl. Queens for example e.g.). Since Manhattan proper still queries 10K+ restaurants, we also limited reviews to <= 50 review (vs pulling all of them). Accordingly, many of the fetched reviews are recent, so we also subset Michelins vs non-Michelins across Michelin 2023* restaurants in Manhattan.

For this project, we implemented the below phasing/framework: 

1. Obtain: Scrape the API for restaurant + review datasets. 
2. Scrub: Preprocess our data & feature engineering — changing to appropriate datatypes, removing unnecessary data/columns, and reformatting data.
3. EDA:  Deep dive through visualizations to better understand our data. 
4. Model: Build a classification model, NLP analysis, & TD-IDF analysis for further insights. 
5. Interpret: Our story! 


**File Summary**

*Pre-work*:
- scrape.ipynb: Script to scrape restaurant Yelp data for Manhattan properties—contains up to 50 most recent reviews per property. For each review, we also pull reviewer status (Yelp Elite/not), photo upload counts, & other "status" metrics that can help ascertain reviewer "credibility". Establishes a subset 2023 Manhattan Michelin Yelp aliases/ids — so we can subset our data & compare Michelin vs non-Michelin places accordingly.
- data_processing.ipynb: Taking the data we got from scrape.ipynb and flattening it into reusable CSVs. 

*Data*:
- restaurants.json: Basic restaurant Yelp data for Manhattan properties—contains attributes like business alias/id, price, cuisine, longitude, & latitude i.a. 
	-restaurant_details.csv: restaurants.json CSV via data_processing.ipynb.
- reviews: Results of scrape.ipynb. Folder containing alphabetized review data; must do methodology as one review file would be >100MB.
	-restaurant_reviews: all reviews in reviews folder aggregated into a CSV via data_processing.ipynb. This file is too big to upload to Github so PLEASE download it by running data_processing.ipynb.

*Analysis*:  
- EDA_numerical.ipynb
- classification.ipynb
- tfidf_model.ipynb 	     
