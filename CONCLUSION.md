I built different models and I tried to improve them modify some of the parameters inside. And I used different targets to see how the models worked. These are the models:

- NLP: 

  - CountVectorizer:
    - I used stip_accents to Remove accents and perform other character normalization.
    - I used 'stop_words' inside the CountVectorizer because I wanted to eliminate most of the common words like 'and', 'the', 'of',..... that they were not relevant for determining wine language.
    - the ngram_range is (1,1) because I only want to extract 1 word.
  - TfidVectorizer:
    - CountVectorizer just counts the word frequencies. The TFIDFVectorizer count the word frequencies and compute the Inverse Document Frequency values, that measure how much information the word provide (whether the term is common or rare in all the documents).
    - I am going to define the same parameters that I used with CountVectorize but I am a going to include also sublinear_tf to scale tf and max_features = 2000 in some of the models that only is going to consider the top 2000 max_features ordered by term frequency across the corpus. 

- Logistic Regression:

  - I am using Lasso ‘l1’ and  Ridge regulation ‘l2’'

  - saga' this parameter handle with Lasso regulation and it's faster than 'liblinear'.

  - 'lbfgs' handle with Ridge regulation

  - 'ovr' in multiclass in the first performance. I changed it to 'Multinomial' in the second performance but the accuracy was higher in the first.

  - 'random_state' I am going to use the default because I am using 'saga' as a solver.

  - n_jobs, we are defining 2 the number of jobs to run in parallel for both fit and predicT.

    

- Random Forests Classifier: 

  I am going to use Random Forests Classifier because is one of the most widespread classifiers and it has the power to handle a large data set with higher dimensionality. Random forests is considered as a highly accurate and robust method because of the number of decision trees participating in the process. It does not suffer from the overfitting problem. The main reason is that it takes the average of all the predictions, which cancels out the biases.

  The Random Forest Classifier parameters

  - n_estimators represents the number of trees in the forest. Usually the higher the number of trees the better to learn the data. However, adding a lot of trees can slow down the training process considerably, therefore I find the sweet spot in 200.
  - n_jobs, we are defining 2 the number of jobs to run in parallel for both fit and predict.
  - Max_dept represents the depth of each tree in the forest. The deeper the tree, the more splits it has and it captures more information about the data. I defined 10 in the last random forest and its the worst performer in all the models that I have created.

  The difference between performs our model with TfidVectorizer or CountVectorizer, does not differ so much. TfidVectorizer performs a little bit better than CountVectorizer.

  Logistic Regression performs better than Random Forest Classifier in this data set, with higher accuracy. Both of them have better scores than the baseline.

- Naive Bayes: 

  Naive Bayes is a classification algorithm relying on Bayes' rule. As in all other classification models, one is interested in determining the probability of having a certain class label when a certain combination of feature values is obtained.

  I am going to use MultinomialNB and BernoullinNB. Both of them are suitable for discrete data. The difference is that while MultinomialNB works with occurrence counts, BernoulliNB is designed for binary/boolean features.

  The best accuracy I got in MultinomialNB with CountVectorizer.

- Cross Validation:

  The Cross validation is going to evaluate the quality of the model. It’s going to fit the model and compute the score 5 consecutive times with different splits every time.

  In all the models that I trained and tested in all the datasets the score was always better than the baseline and in some cases the difference was huge. CountVectorizer and Logistic Regression with Lasso regularization and ‘saga’ as a solver was the best model in most off all the datasets and with all the targets . Only in the data set that I created by joining the two data sets works better with all the targets in the Ridge regularization.

I only calculate de Cross Validation Score in the models that obtained better results with each target. The value was similar than the accuracy score.

The table above shows the best accuracy l that I get training the models with the all targets:

Conclusions:

- The best model has to be selected.
- When the number of classes in the targets were reduced the model performed betterThe results don’t show a huge difference between the datasets.
- The data supports the initial hypothesis.

Improvements:

- Principal component analysis (PCA) in CountVectorizer.
- Define other models.Worked with other features.
- GridSearch (I build the model but I could not perform. It took so much time.

Learn:

- Organize the ideas of what data you want to use before you start running models. 
- Be careful to define the target. 
- Run a model cost a lot of time and it’s essential to define the model carefully before start running it. 

