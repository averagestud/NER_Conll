# NER_Conll
Named_Entity_Recognition on Conll-2003 dataset

This project was performed as CSOC'23 selections project.
In this project using Bert_base_uncased model I have performed a very basic Sequence labelling part of Named Entity Recognition.

#What is Named Entity Recognition?
Named Entity Recognition (NER) is a natural language processing task that involves identifying and categorizing named entities (such as names of people, organizations, locations, dates, and more) 
within a text. NER algorithms analyze the context and linguistic features of words in a text to determine whether they represent entities and assign them to predefined categories, 
like "Person," "Organization," or "Location." NER is crucial for information extraction, text analysis, and various applications like chatbots, search engines, and language understanding systems.
It helps in extracting structured information from unstructured text data.
*Note: Not a single line in the above paragraph was written by me.ChatGPT generated it. Who would know NLP techniques better than a model designed to perform those tasks :)

The first step of any project is the part where the dataset has been loaded and we can see that it containd it in a dict format of train, val and test data and each of which contains 'pos_tags(Part of Speech),
'chunk_tags', 'id', 'tokens' and finally 'ner_tags'(the part that is focused on this project).
First we tokenize the sentence using the BertFastTokenizer and this has the attribute is_fast=True.
We won't be able to see any difference in the tokenizing of one sentence and vwe would only be able to recognise the difference when we use it for large corpus of texts.
The image below has been taken from HuggingFace official website of Fast Tokenizer.
![image](https://github.com/averagestud/NER_Conll/assets/128608033/05b93a9e-d9e8-49de-ba28-e2b85552f146)

After tokenizing the sentences we see that the tokens start with token_id=101 and token_id=103.
Actually these tokens are not for any official word but they are for Snentence start and sentence end (in other terms CLS and SEP).
So we need to cut these tokens out so that Named Entity Recogniser model does not consider them to be a part of the sentence.
After this we directly use the AutoModelForTokenClassification from the pretrained bert_base_uncased model and we use this model to perform the task of Named Entity Recogniser.


The last and final step is to train the model on our dataset, conll-2003 and evaluate how well the model performed.
![image](https://github.com/averagestud/NER_Conll/assets/128608033/5eb7d300-234e-44e2-ba0e-37348697b09e)
Since I was not using any GPU I had to restrict myself to only 3 epochs and the model performed very well even in just 3 epochs since the model is very well trained on a large corpus of data already.
Also, there were 14000 training data in the conll-2003 dataset which helped in increasing the accuracy,F1,Precision of the model.
