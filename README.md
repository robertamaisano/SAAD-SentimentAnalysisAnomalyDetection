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
  
* `AnomalyDetection` folder contains two Python notebook one with DBSCAN clustering and the second one with LSTM-AE model with the predicted anomalies together with the evaluation metrics through RangeBasedConfusionMatrix class for unbalanced Dataset
  
* `Dataset` folder contains data extarcted from Sahel Region from 1-Jun-2020 to 31-Aug-2020 translated in English language and the folder 'English_contractions' with the english contractions dataset used in Preprocessing.
  
Sentiment140 dataset can be downloaded from http://cs.stanford.edu/people/alecmgo/trainingandtestdata.zip

## Dataset
  
  Dataset used is contained into folder `Dataset`, if you want to use different Dataset you can collect tweets through Twint python project:
  
  for Example:
  ```
  import twint
  import nest_asyncio
  import pandas as pd

  nest_asyncio.apply()
  c = twint.Config()
  c.Since = 'start_date'
  c.Until = 'end_date'
  c.Hide_output = False
  c.Geo = 'Latitude, Longitude, range_in_km'
  c.Store_csv = True
  c.Output = 'file_to_save.csv'
  import pandas as pd
  c.Pandas = True
  twint.run.Search(c)
  ```
  
  ### Data Translation
  
  In order to translate in English language collected tweets:
  ```
  from google_trans_new import google_translator
  for i in range(len(df)): 
    df['tweet'][i]=translator.translate(df['tweet'][i])
  ```
