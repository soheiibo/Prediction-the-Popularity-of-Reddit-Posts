# Prediction-the-Popularity-of-Reddit-Posts

### Link to Deployed Application : https://reddit-post-score.herokuapp.com/

# About the Project:
This project is about predicting the overall score a Reddit post will get. Score is the result of upvotes and downvotes for a particular post. Its was identified as a regression problem. The dataset was created using web scarpping with the help of praw library. The features exracted are:

Title - title of the post
Gilded - rewarding a Reddit gold to the post
Over_18 - True if the post has adult content else False
Ups - no of upvotes for the post
Downs - no of downvotes for the post
Num_of_comments - no of comments for the post
Upvote_ratio - upvote ratio of the post
Score - total score (upvotes - downvotes)
Extra features were added with the help of Sentiment analysis for the title of the post using vaderSentiment analyzer. We get 4 columns neg, neu, pos and compound. These features tell how negative or positive the statement is. These columns were combined to one column, Predited_value, using the compound score. Positive sentiment: (compound score >= 0.05), neutral sentiment: (compound score > -0.05) and (compound score < 0.05), negative sentiment: (compound score <= -0.05).

Text preprocessing was done for the title of the post by removing punctuations, stop words, and performing stemming and lemmatization. To convert the title to numeric form, Glove embedding with 100 dimensions was used. This gives a numeric vector for all the unique words in the text. To get one vector representation for each title, weighted average of word vectors method was used. The mean of all word vectors is taken to form one vector which represents the title which has 100 dimensions. One hot encoding for the Predicted_value and Over_18 columns was performed.

As it is a regression problem, regression models like Linear regression, Decision tree regressor, Random forest regressor, KNN regressor, Lasso, Ridge, ElasticNet and XGBoost regressor were used. These models were trained with 60% train data and prediction on 40% test data. The performance of these models was measured based on test accuracy. Out of all these models, XGBoost regressor and Random forest regressor performed well with around 50% accuracy on test dataset.

The application was deployed on Heroku. The deployed application was tested with different Reddit post URLs. As the accuracy of the model is around 50%, the predictions were a little different from expected. In future work, more data can be used to train the model to get good accuracy.
