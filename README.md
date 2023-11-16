## Sentiment Analysis of Amazon Reviews (NLP/Classification)

---

This project utilizes the ```VADER (NLTK)``` and ```RoBERTa (HuggingFace)``` sentiment analysis models to read and categorize Amazon customer reviews as positive, negative, or neutral. These sentiments are then compared with the star rating each review received, acting as a sort of "global truth value", to determine effectiveness of each model's sentiment analysis

### The Dataset

The [Kaggle dataset](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews) used for this project consists of ~500K food reviews submitted by customers on Amazon. This dataset is provided by the Stanford Network Analysis Project (SNAP). For the sake of computation time, this project was carried out utilizing the first 500 non-null values from the Kaggle dataset.

### The Findings

---

#### VADER Model
Figure 1 shows the confidence the VADER model has for its determined 'compound score' for each review when compared to the star rating each Amazon review received. 
![image](fig-images/Vader%20-%20compound%20vs%20score.png)

This shows that the confidence of the model wavers far less for the positive reviews than it does the negative reviews. This trend continues when viewing the positive, neutral, and negative-scored sentiments individually, as shown in Figure 2
![image](fig-images/Vader%20-%20each%20vs%20score.png)

---

#### RoBERTa Model

The RoBERTa model is a pre-trained neural network model provided by HuggingFace that is capable of more advanced sentiment analysis due to its ability to recognize context within a piece of text. As such, RoBERTa has slightly more evidence for each entry in which to base its reviews off of.

Figure 3 below shows the pair plot between the VADER and RoBERTa models:
![image](fig-images/Vader%20-%20Roberta%20vs%20vader.png)

This figure displays the increased confidence of the RoBERTa model in the form of sharper peaks along the diagonal. The diagonal entries along the pair plot are kernal density estimates (KDEs) for each metric's performance.

### Conclusion

Sentiment analysis, in this format, isn't perfect. Even when utilizing the more advanced RoBERTa model, there were still instances where a review was marked as having negative sentiment while having received a 5 star review, and vice versa. However, this is to be expected in order to avoid over-fitting. Ultimately, having the abiliity to employ multiple models for the same job allows for fewer instances of false positives.
