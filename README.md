# FLOW ANALYSIS

Quick analysis of the Flow Studios podcasts to assess engagement, and an attempt to create a Random Forests or Neural Networks model to predict engagement data based on certain attributes.

The .csv files are the data I fetched from the YouTube API in the previous project. Here, you will only find the charts with a brief explanation; the analysis was done in the YouTube video.

## Data Extraction

Through the YouTube API, I obtained the total views, subscribers, and videos produced by each channel. Shortly after, I was able to retrieve the ID of each video produced by the analyzed channels. Using this ID, I consolidated data on views, likes, comments, duration, title, and publication date for each video, resulting in a large DataFrame with individual data for each video from the 3 analyzed channels.

## Initial Analysis

Number of publications made, divided by type (Short = <60s, Video = <50min, the rest are categorized as Live)

![1](https://i.imgur.com/ASbzsS8.png)

Total views, with and without the Flow podcast

![2](https://i.imgur.com/Fj1YJKM.png)

![5](https://i.imgur.com/5PeFyyI.png)

Total views without division by publication type, excluding Flow

![6](https://i.imgur.com/11odhH7.png)

Views divided by the amount of content published in seconds

![3](https://i.imgur.com/p815R4I.png)

![4](https://i.imgur.com/Em2pr3L.png)

I created an engagement measure per second to combine likes, comments, views, and video duration. Following the formula (Views + 1.5 * Likes + 2 * Comments) / Duration in seconds

![7](https://i.imgur.com/93ERiRA.png)

Engagement per second for live streams only

![8](https://i.imgur.com/pToWDgP.png)

## Prediction of views, likes, comments, engagement per second

It was not possible to create a well-performing model to predict these measures based on the variables explored here, such as the type of Flow Studios podcast the publication belongs to, the type of publication (Live, Video, or Short), the publication date, and duration. I tested data normalizations, different subsets of the database, Neural Networks models, and Random Forests, but was unable to achieve good performance. The model could only predict one of the desired variables when another variable that should have been predicted was included (e.g., predicting the number of views with the previous variables + the number of likes or comments for that publication; with this modification, performance improved significantly, but it didn't make sense to have this kind of information to use the model to predict the engagement result of a video in advance).
