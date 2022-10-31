# Newsletter curator

## Webscrapes from 10 different article sites:
This includes the title, description, date, link, and category. Because of how the websites were built differently, I used rss feeds, used json for thhe dynamic websites, and did a general webscrape with requests for the other sites. 

## Data Collection and Cleaning
I used Deepnote integration and had separate notebooks for each article and had it sceduled for 3 times a week. Then merged every dataframe into one big dataset called 'combined.csv'. Before merging datasets, each data is cleaned in their individual notebooks. All dates were converted into datetime. Missing descriptions were replaced with 'No Description', nans in the category columns were filled. 
After merging, the dataframe is also cleaned to drop duplicates, drop excess columns that were created when merged.

## Old Dataset and New Dataset
When I though I had a good amount of articles to train (804 articles) I manually inserted 1's an 0's into a target column of that dataset which shows which articles I would want to send out to people and which ones I wouldn't and named that dataset 'combined_csv'.

The dataset 'combined_csv' will become my old dataset, and then the newly merged dataset would just be called 'combined'. Then I loop through the files and get the recent file which would contain old and new articles. Then I would get the length of the old dataset and slice the newly combined dataset to get a dataframe called 'new_articles'. Then I save the new_article to a csv, concat the dataframe to the old dataset for when the next new articles merge it would become the old dataset.

## Prediction
I used the manually inserted file to train my model, and everytime 'new_articles.csv' is stored it will be predicted using the saved model I trained with LogisticRegression which had an accuracy of 83%
