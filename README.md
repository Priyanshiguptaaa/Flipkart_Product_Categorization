# Flipkart_Product_Categorization

## Table of Contents

1. [About](#about)
2. [Installation](#installation)
3. [Data Aquisition](#data-aquisition)
4. [Data Exploration & Cleaning](#data-exploration-and-cleaning)
5. [Data Visualzation](#data-visualization)
6. [Approaches](#approaches)
7. [Build on Google Colab](#build-on-google-colab)
8. [Models Summary](#models-summary)
9. [Conclusions](#conclusions)
10. [Future Scope](#future-scope)
11. [Publication References](#publication-references)

## About

This repository illustrates the task of Category Prediction of an E-Commerce Website data (Flipkart), classification of the description of products into the primary categry of their category tree, and getting the notebook documenting the path to an optimal model pipeline

## Installation

 Clone the repo

```bash
git clone https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/-.git
cd Flipkart_Product_Categorization/
```

** Note: The Code is Implemented in Google Colaboratory that lets us build the project without installing it locally. Installation of some libraries may take some time depending on your internet connection and system properties. You can download the Colab Notebook as a Jupyter Notebook and Run it Locally or on the Google Colab Platform as well

## Data Aquisition

You can download the E-Commerce Dataset sample from here

https://docs.google.com/spreadsheets/d/1pLv0fNE4WHokpJHUIs-FTVnmI9STgog05e658qEON0I/edit#gid=1396401268

## Data Exploration and Cleaning

- The dataset has 2 NA values in the Description which were Dropped
- The Product Category Tree has 337 Rows of Data that does not have a Primary Category Specified, thus they were categorised as "Others" to avoid loss of Data

The following steps are performed:

1.   Tokenization: Split the text into sentences and the sentences into words. 
2.   Lowercase the words and remove punctuation.
3.   Words that have fewer than 3 characters are removed.
4.   All stopwords are removed.
5.   Words are lemmatized — words in third person are changed to first person and verbs in past and future tenses are changed into present.
6.   Words are stemmed — words are reduced to their root form.

**Note: Alternate approach to cleaning can be using BeautifulSoup and Selenium to scrape the product category from the website using the Product URL 


## Data Visualization

#### The Value Counts after cleaning the Primary Categories
![after_cleaning_categories](https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/blob/main/visualizations/after_cleaning_categories.png)

#### Visualising the Length of Description in a Box Plot to get inference on Variation from the Mean
![](https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/blob/main/visualizations/boxplot_descriptionlength.png)


## Approaches

#### Features Used

| Feature Name       | Type            | Description                           |
| ---                | ---             | ---                                   | 
| Description            | STR             | The description of the Product  (Primary Feature)      |
| Product_Category_Tree           | STR            | Used to Extract the Primary Category        |

#### Techniques - 

1. [Topic Modelling (Gensim's Latent Dirichlet Allocation Multicore algorithm )](https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/tree/main/LDA_Multicore_TopicModelling)

Topic modeling is a type of statistical modeling for discovering the abstract “topics” that occur in a collection of documents. Latent Dirichlet Allocation (LDA) is an example of topic model and is used to classify text in a document to a particular topic. It builds a topic per document model and words per topic model, modeled as Dirichlet distributions.

2. [Seq2Seq + Attention + Teacher Forcing Neural Machine Transaltion ( 1 Attention Layer )](https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/tree/main/Seq2Seq_Attention_Machine_Translation)

For product categorization task, the conventional methods are based on machine learning classification algorithms, but this paper : - 
("Don’t Classify, Translate: Multi-Level E-Commerce Product Categorization Via Machine Translation". Maggie Yundi Li, Liling Tan, Stanley Kok. 2018. https://arxiv.org/pdf/1812.05774.pdf ) has proposed a new paradigm based on machine translation and it has shown that this approach achieves better predictiion accuracy than the classification system. Here we have implemented the proposed model.

#### Classification Report

![classification_report](https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/blob/main/results/Classificationreport_seq2seq.png)


## Build on Google Colab

To get started, upload and open the notebooks in playground mode and run the cells(You must be logged in with your google account and provide additional authorization). If you want to run locally, a requirements.txt file is provided

```bash
git clone https://github.com/Priyanshiguptaaa/Flipkart_Product_Categorization/-.git
cd Flipkart_Product_Categorization/
pip install -r requirements.txt
```

## Models Summary

| Model Name       | Accuracy           |       
| ---                | ---             |  
| Seq2Seq + Attention + Teacher Forcing       | 81%    |       

## Conclusions

- There are 337 rows in the Category tree that do not have a Primary Category in the dataset. 
- The dataset is not huge so BERT is not used for machine learning classification
- RNNs are a good conceptual fit with NLP, but according to research, methods using attention have been achieving state of the art results on NLP.
- Based on the previous research done on this task, Machine Translation has been proposed to improve the accuracy and perform better than machine learning classification algorithms. Here we have implemented the same and the Sequence2Sequence Attention model has shown to have 81% accuracy. 
- The accuracy can be icreased by further experimenting with more Attention Layers and changing the parameters.  


## Future Scope

1. Running LDA using TFIDF
2. 3-5 Attention Layers in Seq2Seq Translation
3. 3-5 Attention Layers with Cross Entropy Validation in Seq2Seq Machine Transaltion
4. Training the Transformer Model for Machine Translation
5. Ensembling the best Seq2Seq Attention model explored with the Transformer model
6. More research is needed on the various strenghts of RNNs, CNNs, and transformers/attention and ensembling the approaches to combine the best of each.


## Publication References

[1] "Unconstrained Product Categorization with Sequence-to-Sequence Models". Maggie Yundi Li, Liling Tan, Stanley Kok, Ewa Szymanska. 2018. https://www.comp.nus.edu.sg/~skok/papers/ecomdc18.pdf

[2] "Don’t Classify, Translate: Multi-Level E-Commerce Product Categorization Via Machine Translation". Maggie Yundi Li, Liling Tan, Stanley Kok. 2018. https://arxiv.org/pdf/1812.05774.pdf

[3] "Effective Approaches to Attention-based Neural Machine Translation". Minh-Thang Luong, Hieu Pham, Christopher D. Manning. 2017. https://arxiv.org/abs/1508.04025

[4] "Sequence to Sequence Learning with Neural Networks". Ilya Sutskever, Oriol Vinyals, Quoc V. Le. 2014. https://arxiv.org/abs/1409.3215

[5] "Neural Machine Translation by Jointly Learning to Align and Translate". Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio. 2016. https://arxiv.org/abs/1409.0473

[6] "Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation". Kyunghyun Cho, Bart van Merrienboer, Caglar Gulcehre, Dzmitry Bahdanau, Fethi Bougares, Holger Schwenk, Yoshua Bengio. 2014. https://arxiv.org/abs/1406.1078

[7] "A Neural Conversational Model". Oriol Vinyals, Quoc Le. 2015. https://arxiv.org/abs/1506.05869

[8] "Language Modelling for Handling Out-of-Vocabulary Words in Natural Language Processing". Shabeel Meemulla Kandi. 2018. https://www.researchgate.net/publication/335757797_Language_Modelling_for_Handling_Out-of-Vocabulary_Words_in_Natural_Language_Processing

[9] "Attention Is All You Need". Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin. 2017. https://arxiv.org/abs/1706.03762

[10] "Pay Less Attention with Lightweight and Dynamic Convolutions". Felix Wu, Angela Fan, Alexei Baevski, Yann N. Dauphin, Michael Auli. 2019. https://arxiv.org/abs/1901.10430

