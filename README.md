# DogRateData
This project shows the efforts and steps done to wrangle a given DogRate dataset.

## Wrangling and Analyze Data
### Data Gathering
In the cell below, I gathered **all** three pieces of data for this project and load them in the notebook. 
**Note:** the methods required to gather each data were different.
1. I downloaded the WeRateDogs Twitter archive data (twitter_archive_enhanced.csv)
2. Use the Requests library to download the tweet image prediction (image_predictions.tsv)

##### Read the content of tweet-json.txt into a dataframe
* The url below has the tweet info, I downloaded the content into tweet-json.txt in a folder named tweety
* In the folder created, I picked the text file and read the content, then created a dictionary that contains all lines in the file, and read the content into a dataframe

### Assessing Data
In this section, the following quality and tidyness issues were detected and documented. Using both visual assessment and
programmatic assessement to assess the data.
#### Quality issues
##### df_twitter_archive table:

1.Missing data on `in_reply_to_status_id`, `in_reply_to_user_id`, `retweeted_status_user_id`, `retweeted_status_timestamp`, drop these columns as they have very little non null values.

2.`expanded_urls`has incomplete data of 2297 out of 2367

3.We only want original tweets, not retweeted data. This table has retweeted data i.e data with `retweeted_status_id` not null.

4.`timestamp` column is of type object instead of type datetime


##### df_image_prediction table:

5.The prediction columns `p1`, `p2`, `p3` values are separated by underscore instead of space. Eg `Old_English_sheepdog` should be `Old English sheepdog` 

6.Inconsistent case for `p1`, `p2` and `p3` columns.

7.Missing records 2075 instead of 2356

##### df_tweet_data table:
8.We do not need tweets from August 1, 2017. Data from this date should be excluded from analysis



### Report
From the analysis made, we asked the following questions which are also answered via visualization using the matplotlib library.

**Questions**
1. Which of the dog stages is highly rated? 
From the analysis below, we pick the most common dog stages and plotted it against its count. The most common dog stage found in the data is pupper. It is the most rated dog stage as well.
2. Which dog stage has the most retweet and favourite count?
From the analysis we see that `Puppo` dog stage has more likes in the tweet data while `Doggo` dog stage has more retweets
3. Does the retweets and favorite count influnce the dog rating? 
From the analysis done, yes, retweets and favorites count influence dog ratings.

The plots are as shown on wrangle_act.ipynb file.
