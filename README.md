# iTunes-SQL-Machine-Learning
## Using MySQL to perform ML prediction of song rating on my iTunes Music Library

The purpose of this project is to produce a trained model that can predict a song rating for the tracks in my iTunes music library. 

The main steps are: 
1. Upload iTunes Music Library into an SQL database.
  * This process is outlined in the "iTunesSQL" document.
2. Use a set of already rated tracks to train and test 6 different models
3. Use the best model on my full iTunes library to rate my unrated songs.

I wanted to explore how well the models would predict rating based purely on a ratio of (Play_Count÷Skip_Count), so I generated a test dataset with ratings based on this ration plus some noise.

To generate the test dataset:
1. I uploaded a sample of about 300 songs.
2. I filled in missing Play_Count and Skip_Count with random integers.
3. To unrated songs, I assigned a Rating value based on 3 different ranges of the ratio Play_Count/Skip_Count.

Assignment of ratings based mainly on ratio of Play_Count / Skip_Count:
  To introduce some variability, I assigned the Ratings
   1. For Ratio <=0.5, Rating= [random sequence of 0 and 40]
   2. For 0.5 < Ratio < 2.0, Rating= [random sequence of 40 and 80]
   3. For Ratio >=2.0 , Rating= [random sequence of 80 and 120]
    
To train the models: 
1. I randomly split the test dataset into 80% training set and 20% validation set.
2. I provided the models with Play_Count, Ratio, Total_Time (song duration), and Rating.
3. Set up a 10-fold cross validation test harness.
4. Studied the confusion matrix and classification report. 

The trained model then be used on my full iTunes Library!
