# Reddit Politics

Kate Caldwell
27 May 2022

### What's Included? 

There are seven notebooks included in this repository. One notebook includes data exploration, which is titled *Exploring Conservatives vs. Liberal Reddit Posts*, and the other six each include a different strategy to train the model. Some models are trained on only the title data, which include: 

- *Classify Reddit Post Titles w/ a Dense Net*
- *Classify Reddit Post Titles w/ RNN* 
- *Classify Reddit Post Titles w/ Feature Extraction*
- *Classify Reddit Post Titles w/ Fine Tuning*

In addition, two notebooks are trained on title + text data:
- *Classify Reddit Posts w/ Feature Extraction*
- *Classify Reddit Posts w/ Feature Extraction*

### The Data

I experimented with data recently published on Kaggle — *Liberals vs Conservatives on Reddit* ([found here](https://www.kaggle.com/datasets/neelgajare/liberals-vs-conservatives-on-reddit-13000-posts)). There are a total of 12,854 lines of data, which include 8319 ‘Liberal’ posts and 4535 ‘Conservative’ posts. Only 2428 lines of data include the post text. Of these, 1471 are labeled ‘Liberal’ and 957 are labeled ‘Conservative’.

### The Experiments

To establish a baseline, I trained a simple dense net (one hidden layer). I also tried a recurrant neural net to see if it would improve performance. Because the labeled data included more titles than title + text of Reddit posts, I used transfer learning to to train a models on both titles only and titles + text. Using pre-trained language models downloaded from HuggingFace, I tred feature extraction and fine tuning to classify the posts. I experimented with a number of pre-trained models, but saw little improvement between the different models available for download, in most cases opting to stick with the default "DistilBERT."

### Results 

In every case that transformers were used for transfer leanring, the performance of the classifier improved. In addition, best results were achieved with use of the post title + text (despite the smaller sample size). Because the samples were unevenly represented in the data, I used an F1 score to evaluate my models. 

| Model      | F1 Score |
| ----------- | ----------- |
| Dense Network      | .31       |
| RNN   | .52        |
| Title-only Feature Extraction   | .77        |
| Title-only Fine Tuning   | .77        |
| Title and Text Feature Extraction | .76        |
| Title and Text Fine Tuning   | .8        |

### How to Run these Notebooks

Each notebook can be run independantly. They can be easily run in Kaggle (linked at the head of each notebook). Alternatively, you can download the data from Kaggle ([found here](https://www.kaggle.com/datasets/neelgajare/liberals-vs-conservatives-on-reddit-13000-posts)), change the 'load_data' function to point to the downloaded csv, and run the notebooks on your local machine. After running, results and a confusion matrix will be displayed toward the bottom of the notebook. 
