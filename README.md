# Text-Mining
  We use opinions of 7 different websites to predict negative or possitive return of Apple Stock price(0/1).
  
  Time: 10/08/2014 - 10/08/2015 <br />
  [Training Data](https://github.com/Alexzhibin/Text-Mining/blob/master/train_trend_1.csv): 70% <br />
  [Testing Data](https://github.com/Alexzhibin/Text-Mining/blob/master/test_trend_1.csv): 30%<br />
  <br />
  Company: Apple Company<br />
  <br />
  Y: 
    If the return is possitive, then Y=1.If the return is negative, then Y=0. <br />
    The return means the stock price of day2-stock price in day1.
  <br />
  [Y_test](https://github.com/Alexzhibin/Text-Mining/blob/master/y_trend_1.csv)
  Y_train : article['trend'] or training_y['trend']
  <br />
  X: X will be processed with 3 different methods in the following. 


# Cleaning data
  The [KaggleWord2VecUtility.py](https://github.com/Alexzhibin/Text-Mining/blob/master/KaggleWord2VecUtility.py)will clean the data. 
  (1)Remove HTML. (2)Remove non-letters. (3)lower case and split them. (4)remove stop words. (5)PorterStemmer. 
  
  
#1. TF-IDF 
  (1)Conver the words to vectors.(word count) The maximum 5000 words.
  (2)TF-IDF will make 20000 features based on 5000 words and n-gram range would be (1 ~ 3).
  (3)Reduce the dimensions to 10000 depending on the chi-squre test. 
  (4)Algorithm and Results(Accuracy of All): 
    a. NB  testing       7000 features            10000 features
                            55.7%                     55.84%
       NB  training      7000 features            10000 features
                            97.7%                     96.19%
    
    b.SGD  testing       7000 features            10000 features
                            57.14%                    57.89%
          training       7000 features            10000 features 
                            99.15%                    92.13%
    
    c.RandomForest  testing     10000 features       10000 features
                                   55.75%                 99.87%
                                   
    
#2. [Vectoring Average](https://github.com/Alexzhibin/Text-Mining/blob/master/Get_averge_Word2vec.ipynb)(Word2Vec)
  (1)Conver the words to vectors using the Word2Vec algorithm, which is developed by Google. The more words trained, the higher accuracy the model is.
  (2)Train the model (1000 features, min 50 words, context = 10)
  (3)Get the average of vectors of each opinion. The vectors will be the similarities of words in each opinion.
  (4)After the average, the data set will 1000 features 
  (5)data frame(8090,1000) 
  (6)Algorithm and Results(Accuracy of All):
   a. RandomForest  testing      1000 features   52.93%
                    training     1000 features   99.86%
                    
#3. [Kmeans](https://github.com/Alexzhibin/Text-Mining/blob/master/KMeans-Word2vec.ipynb)(Word2Vec)
  (1)Conver the words to vectors using the Word2Vec algorithm, which is developed by Google. The more words trained, the higher accuracy the model is.
  (2)Train the model (800 features, min 50 words, context = 10)
  (3)Kmeans. Cluster 5 words in average in per cluster. (1509 clusters)
  (4)Map the centeroid, which means mark each word an index of centeroid.
  (5)data frame(8090, 1509)
  (6)Algorithm and Results(Accuracy of All):
   a. RandomForest     testing      50.42% 
                       training     99.86%
    
    
    
    
  
