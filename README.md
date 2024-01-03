# DP-sentiment


In this research, the main *idea* was in following: 
- to analyze data from social media(e.g. Twitter) in Polish that would be related to the coronavirus 
- Compare results with statistics data for the: Deaths,Recovered,In_the_hospital,In_quarantine,Under_medical_supervision
- Make a conclusion

For our study we decided to choose next *models*: 

**twitter_sentiment_pl_base**[6]

Model is based on HerBERT (Polish version of BERT) since it receives state-of-the-art results in the area of text classification. 
It was trained on the translated version of TweetEval by Barbieri et al., 2020 for 10 epochs on single RTX3090 gpu
The model will give you a three labels: positive, negative and neutral.

**twitter-xlm-roberta-base-sentiment-finetunned**[7]

This is a multilingual XLM-Roberta model sequence classifier fine tuned and based on the Cardiff NLP Group sentiment classification model. This model supports Polish.

For an *inference* we used a dataset[1] of media releases (Twitter, News and Comments, Youtube, Facebook) from Poland related to COVID-19 for open research. It presents data for the following period:  15/01/2020-31/07/2020.

As a *dataset with statistics data* we used 2020 Poland coronavirus data (COVID-19 / 2019-nCoV)[2].

Now a little bit about results obtained. 

**twitter_sentiment_pl_base**:


|   | Recovered  | Deaths | Under medical supervision | Confirmed |In quarantine | In the hospital |
|:------------- |:---------------:| -------------:| :---------------: | :---------------: | :---------------: | :---------------: |
|neg %         | -0.48         | -0.50        | 0.25 | -0.49 | 0.002 | -0.21 |
| neg count        | -0.62          | -0.74        | 0.46 | -0.73 | -0.36 | -0.58 |

sliding window smooth:


|   | Recovered  | Deaths | Under medical supervision | Confirmed |In quarantine | In the hospital |
|:------------- |:---------------:| -------------:| :---------------: | :---------------: | :---------------: | :---------------: |
|neg %         | -0.948         | -0.966        | 0.276 | -0.961 | -0.37 | -0.641 |
| neg count        | -0.76          | -0.85        | 0.46 | -0.85 | -0.45 | -0.67 |



**twitter-xlm-roberta-base-sentiment-finetunned**


|   | Recovered  | Deaths | Under medical supervision | Confirmed |In quarantine | In the hospital |
|:------------- |:---------------:| -------------:| :---------------: | :---------------: | :---------------: | :---------------: |
|neg %         | -0.169         | -0.191        | 0.071 | -0.193 | -0.117 | -0.12 |
| neg count        | -0.45          | -0.549        | 0.221 | -0.55 | -0.426 | -0.525 |

sliding window smooth:


|   | Recovered  | Deaths | Under medical supervision | Confirmed |In quarantine | In the hospital |
|:------------- |:---------------:| -------------:| :---------------: | :---------------: | :---------------: | :---------------: |
|neg %         | -0.527         | -0.652        | 0.432 | -0.640 | -0.380 | -0.574 |
| neg count        | -0.672          | -0.779        | 0.349 | -0.783 | -0.538 | -0.696 |


**Conclusion**:

The research conducted has provided valuable insights into the sentiment of social media discourse in Poland regarding the COVID-19 pandemic. By utilizing advanced natural language processing models, specifically tailored for the Polish language, we were able to assess the emotional tone of public conversations on platforms like Twitter and compare these findings with official statistics concerning the pandemic's impact in Poland.

Both models employed, twitter_sentiment_pl_base and twitter-xlm-roberta-base-sentiment-finetunned, demonstrated their effectiveness in classifying sentiments into positive, negative, and neutral categories. The analysis of the data revealed a correlation between the sentiment expressed on social media and the various indicators of the pandemic's severity, such as the number of recovered patients, deaths, confirmed cases, and individuals under medical supervision or in quarantine.

The negative sentiment percentages and counts generally showed an inverse relationship with the number of recovered patients , the number of deaths and confirmed cases.  And a direct relationship with the number of patients under medical supervision.  

**References**:

[1] https://zenodo.org/records/4319813 
[2] https://kandi.openweaver.com/python/dtandev/coronavirus 
[3] https://arxiv.org/abs/2204.12928
[4] https://arxiv.org/abs/2204.10185
[5] https://blog.singularitynet.io/aigents-sentiment-detection-personal-and-social-relevant-news-be989d73b381
[6] bardsai/twitter-sentiment-pl-base · Hugging Face
[7] cardiffnlp/twitter-xlm-roberta-base-sentiment · Hugging Face 
