## WeRateDogs wrangle_report

Many people are running social media accounts for their cute dogs. However, most of them usually aren’t running their social media accounts very well due to lacking the knowledge of what the audiences like and what factor drives their favorite and retweet counts.

![IMG_0503 2](https://user-images.githubusercontent.com/72320718/185775523-f49640dd-bc94-436f-9ac4-ec8fae6328c6.jpg)


This report describes the wrangling processes done for the WeRateDogs project, the datasets were cleaned and made ready for analysis.
Data Wrangling: It refers to a variety of processes designed to transform raw data into more readily used formats. The exact methods differ from project to project depending on the data you're leveraging and the goal you're trying to achieve.
Data Wrangling consists of :

1. Data Gathering

2. Data Assessing

3. Data Cleaning
### Data Gathering

It is the systematic process of gathering observations or measurements in research. It can be qualitative or quantitative.
Steps

- I imported all the python libraries that are necessary for this project.
- I used pandas to read twitter_archive_enhance.csv file into a dataframe called twitter_arch
- I made use of Requests library to download the tweet image_prediction.tsv file and load into a dataframe called image_pred
- I used pandas to read the tweet_Json.txt file line by line into a dataframe with tweet_id, retweet_count and favorite_count
### Data Assessing

It is the process of evaluating (statistically or other methods) data in order to determine whether they meet the quality required for projects  and are of the right type and quantity to be able to actually support their intended use.
I made use of both visual assessment and programmatic assessement to assess the data for quality and tidiness issue. I carefully looked through the 3 datasets and documented issues to be resolved.I made use of pandas methods such as info(), describe() and others to programmatically assess the datasets. The quality and tidyness issues found are:
#### QUALITY ISSUES
        * twitter-archive
            1. timestamp column is an object(i.e string) instead of datetime format. 

            2. In several columns null objects are represented as 'None' instead of NaN. 

            3. Dog Name column have invalid names i.e 'None', 'such', 'the 'a', 'an' etc. 

            4. Some rows have several identical values in the expanded_url column. 

            5. These columns type (in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id,                                       retweeted_status_user_id and tweet_id) is float instead of string (to prevent operations happening on                  them).

        ** image_pred.tsv
            1. Tweet_id fields in the three datasets are stored as int values and should be strings. 

            2. Missing values from images dataset (2075 rows instead of 2356). (This was resolved at the end of the                  data wrangling)

            3. Some tweet_ids have the same jpg_url.
        
        *** twitter_json
            1. Create_date column is an object instead of datetime. 
  

#### TIDINESS ISSUES

        * twitter-archive.csv
            1. Dog stages (doggo, floofer, pupper, puppo) are spread in different columns. 

            2. We are only interested in “original tweets”, no “retweets”; the retweet data is in columns like retweeted_status_id, retweeted_status_user_id and retweeted_status_timestamp. 

            3. Reply tweets are not “original tweets” either; this data is stored in the columns in_reply_to_status_id and in_reply_to_user_id. 

        ** image-pred.tsv
            1. Breed Predictions, Confidence intervals and Dog tests are spread in three columns. 

        *** twitter_json
            1. Create_date exists already in twitter-archive-enhanced.tsv. 

            2. All columns can be merged into 1 using tweet_id. 
### Data Cleaning


It is the process of detecting and correcting (or removing) corrupt or inaccurate records from a dataset.
All the issues documented while assessing were cleaned using the define, code and test steps. I made clean copies for each dataframe before cleaning. At the end, all the dataframes were merged into one and further cleaned. the final dataframe was saved as a csv. I didn't spot all the quality and tidiness assessments at the assessing data section, so I was iterating and revisiting assessing to add these assessments to my notes.
### Conclusion


Data Wrangling is a very important part of any data project. Data wrangling is important because it saves costs, improves business intelligence, and enhances business insights.
### References

- Youtube [video](https://youtu.be/_vRHGRWi9_U) to know the difference between doggo, floofer, pupper and puppo as stages of dogs

- Doggo having nightmares youtube [video](https://youtu.be/WdIfjzreRnM) to know the difference between doggo, floofer, pupper and puppo as stages of dogs

- I had to refernce stackoverflow for some help whenever I was stuck. For the wordcloud, I referenced  www.analyticsvidhya.com/blog/2021/08/creating-customized-word-cloud-in-python/
