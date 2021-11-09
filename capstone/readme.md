## Problem Statement

Wine tasting notes are often viewed as an invaluable part of the wine purchasing decision. Wine tasting notes by professionals, such as Wine Spectator and Wine Advocate, are often printed and used by commercial retailers as an immutable guide to wines sold.

However, objectivity in these notes can often be difficult due to expression of only 1/3 of nose receptor phenotypes in humans, leading to vast differences in tasting experience. Furthermore, tasting events often contain 100s, or 1000s, or wines, which can cause fatigue in even the most experienced of tasters.

Finally, tasting is often confounded by the lack of a common language, and indeed, a common cultural background against which to compare aromas and smells.

The WSET has produced a tasting rubric, in an attempt to create a common wine vocabulary, quantifying not just aroma but body and taste, as well.

In 2002, A.C. Noble created a wine wheel during her time at UC DAVIS. This wine wheel was revolutionary, not because it created a common language, but because it came with instructions to create a reproducible standard for each aromatic note from common supermarket ingredients.

My project will examine 10,000s of tastings notes created to determine if it is able to create passable wine notes based on an initial seed and whether a deep-learning model can be trained to generate appropriate looking wine-tasting notes.

## Notebooks

* Data Scraping
* Data Cleaning & EDA
* Model 1 - Basic model with 2 LSTM layers trained on 2200 rows
* Model 2 - Model with 3 layers of LSTMs, Dropouts and Normalisation trained on 2200 rows
* Model 3 - Model 2 trained on the whole data set (48,000 rows)
* Model 4 - Encoder Block Model trained on the whole data set
* Model 5 - Pre-trained DistilGPT2 Model

## Dataset

* [`wine_df_small.csv`](./wine_df_small.csv): Cleaned 2200 Rows of tasting notes from the Wine Spectator Website
* [`wine_df_full.csv`](./wine_df_full.csv): Entire data set of tasting notes
* [`wine_df_cleaned.csv`](./wine_df_cleaned.csv): Cleaned data set of tasting notes. ~ 48,000 rows.
* [`test_table.csv`](./train.csv): Wine tasting notes split into 2 columns with the initial 15 words and the rest of the note as a ground truth for comparison

### Data Dictionary



## Conclusion

### Analysis
The best model performance was seen in the simplest model, with the smallest data set, and in the Pre-trained DistilGPT2 model.

One reason for the occurrence of the first is that the model was trained solely on the Wine Spectator dataset, which has a fairly similar way of writing notes, which may mean that the model is over trained on the data set and would likely not perform well on wines whose descriptions are outside the dataset.

The DistilGPT2 model performed very well, producing sentences that were coherent, as well as punctuation that made sense. However, on various seed words, the model did show a tendency to start writing gibberish as the sentence got longer.

### Possible Further Steps

One thing that might be possible is that the DistilGPT2 model needs to train on longer texts, as we limited the data set to 75 words to make sure that it would produce succinct paragraphs. However, this might mean that there is a lack of longer sentences that provide the model with sufficient context to produce longer sentences.

Another step to take the project in, is to introduce controllable language generation. Ideally, the model would product wine notes that are appropriate to wines from each region, as well as appropriate to the age of the wine. Introducing special weightings to the location and age may be one way of proceeding with this addition.

Lastly, it would be good to introduce a way for the system to handle unknown elements as well. This would be doubly important with regards to the previous point. It would allow it to look up words it has not encountered yet and find the nearest equivalent and then substitute that in place.
