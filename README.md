# SAD-SentimentAnomalyDetection
Anomaly Detection with Sentiment Analysis on Twitter Data ad evaluation metrics

Contents:

* `ModelForTransfer` folder contains the Sentiment-BiLSTM Model trained on Sentiment140 Dataset with 85% of accuracy and Word2Vec 100dim trained model
* `Sentiment_TextBlob` folder contains a Python notebook with an exploratory Analysis and Sentiment Analysis with TextBlob library
* `Preprocessing` folder contains a Python notebook with 7 steps NLP preprocessing of tweets Dataset

  The **Preprocessing steps taken are**:

    1.**Lower Casing**: Each text is converted to lowercase.
    
    2.**Replacing URLs**: Links starting with 'http' or 'https' or 'www' are replaced by '<url>'.
  
    3.**Replacing Usernames**: Replace @Usernames with word '<user>'. [eg: '@Kaggle' to '<user>'].
  
    4.**Replacing Consecutive letters**: 3 or more consecutive letters are replaced by 2 letters. [eg: 'Heyyyy' to 'Heyy']
  
    5.**Replacing Emojis**: Replace emojis by using a regex expression. [eg: ':)' to '<smile>']
  
    6.**Replacing Contractions**: Replacing contractions with their meanings. [eg: "can't" to 'can not']
  
    7.**Removing Non-Alphabets**: Replacing characters except Digits, Alphabets and pre-defined Symbols with a space.

* `SentimentModel` folder contains a Python notebook with the Sentiment Model prediction on collected data and the subfolder `Grouping`to group sentiment prediction data by hour
  
* `AnomalyDetection` folder contains two Python notebook one with DBSCAN clustering and the second one with LSTM-AE model
