# Sentiment Classifier

1. make_features.ipynb
    - Processes/forms features for Movie Reviews data:
        - Sentiment aware tokenization
        - Negation --> tf-idf matrix
        - Pos:Neg words ratio
        - Length of review
        - number of Noun phrases
     - Forms & exports feature dataframe & exports 
        
    - input: 
        - Movie reviews dataset ==> src/Data/review_polarity/txt_sentoken
                - Source: Pang, B., Lee, L., & Vaithyanathan, S. (2002). Thumbs up? Sentiment classification using machine learning techniques. arXiv                                       preprint cs/0205070.
        - sentiment lexicon ==> src/Data/sentiment_lexicon.csv 
                - Combination of NRC Emotion Lexicon, NRC Emotion Affect Intensity Lexicon, and the Opinion Lexicon (NLTK)
                - Sources: Crowdsourcing a Word-Emotion Association Lexicon, Saif Mohammad and Peter Turney, Computational Intelligence, 29 (3), 436-465,                                   2013
                           Word Affect Intensities. Saif M. Mohammad. In Proceedings of the 11th Edition of the Language Resources and Evaluation                                           Conference (LREC-2018), May 2018, Miyazaki, Japan.
                           Hu and Liu, KDD-2004
                
    - output: 
        - feature dataframe ==> src/Data/data.csv 
    **NOTE: I do not recommend running this file as it takes a while to run, and instead I recommend using the pre-existing data.csv file 

2. make_features_extracredit.ipynb
    - Processes/forms features for Chambana Yelp Restaurant Reviews data:
            - Sentiment aware tokenization
            - Negation --> tf-idf matrix
            - Pos:Neg words ratio
            - Length of review
            - # of Noun phrases
         - Forms & exports feature dataframe & exports 

        - input: 
            - Yelp reviews dataset ==> src/Data/ExtraCredit/Yelp/all_reviews.txt
            - sentiment lexicon ==> src/Data/sentiment_lexicon.csv 
        - output: 
            - feature dataframe ==> src/Data/ExtraCredit/data_extracredit.csv 
        **NOTE: I do not recommend running this file as it takes a while to run, and instead I recommend using the pre-existing data.csv file 
        
        
3. model.ipynb
    - Runs baseline system & improved systems on 4 classifiers: Naive Bayes
                                                               Decision Tree
                                                               Linear SVM
                                                               Random Forest
        - reports F1, Precision, and Recall metrics
        
        - baseline system: Negation (TF-IDF matrix)
        - Improved systems (incremental approach):
            - Negation + Pos:Neg ratio
            - Negation + Pos:Neg ratio + Noun Phrases
            - Negation + Pos:Neg ratio + Noun Phrases + Length 
        - input:
            - Feature dataset ==> src/Data/data.csv

               
4. model_extracredit.ipynb
    - Runs baseline system & improved systems on 4 classifiers: Naive Bayes
                                                               Decision Tree
                                                               Linear SVM
                                                               Random Forest
        - reports F1, Precision, and Recall metrics
        
        - baseline system: Negation (TF-IDF matrix)
        - Improved systems (incremental approach):
            - Negation + Pos:Neg ratio
            - Negation + Pos:Neg ratio + Noun Phrases
            - Negation + Pos:Neg ratio + Noun Phrases + Length 
        - input:
            - Feature dataset ==> src/Data/ExtraCredit/data_extracredit.csv  


5. sentiment_lex.ipynb
    - Combines multiple sentiment lexicons into a dataframe; positive review = 1
                                                             negative review = 0
    - resulting dataframe is used in make_features.ipynb & make_features_extracredit.ipynb                                 
        - input: 
            - NRC-Emotion-Lexicon-v0.92\NRC-Emotion-Lexicon-Wordlevel-v0.92.txt
            - NRC-Sentiment-Emotion-Lexicons\NRC-AffectIntensity-Lexicon.txt
        - output:
            - src/Data/sentiment_lexicon.csv 
    **NOTE: I do not recommend running this and instead I recommend using the preexisting csv 
            
        

6. HappyFunTokenizer.py
    - sentiment aware tokenizer w/ negation from Christopher Potts, https://pypi.org/project/happiestfuntokenizing/
    - called in make_features.ipynb & make_features_extracredit.ipynb  
