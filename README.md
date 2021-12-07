# centroid-based-ATS-with-ELMo
This code tests the performance of ELMo and Word2Vec embeddings in a centroid-based automatic text summarizer presented in the paper ["Centroid-Based Text Summarization through Compositionality of Word Embeddings"](https://aclanthology.org/W17-1003.pdf) by Rossiello et al.

Results on CNN new dataset

| Models | ROUGE-1   | ROUGE-2 | ROUGE-L |
| -------| --------- | ------- | ------- |
| ELMo   | 0.3785    | 0.1122  | 0.2432  |
|**Word2Vec**| **0.3872**    | **0.1177**  | **0.2515** |

^Precision scores for the summarizers that used ELMo and Word2Vec embeddings

**Package Requirments:** gensim, rouge, tensorflow2.6.0, tensorflow_hub, nltk, sklearn
## Data preparation with CNN dataset

1. Download dataset from [here](https://drive.google.com/uc?export=download&id=0BwmD_VLjROrfTHk4NFg2SndKcjQ)
2. Unzip the file
3. Put all `.story` files in a directory called `./data`
4. `python3 load_dat.py`

## Download the pretrained ELMo model

`cd ~/tfhub/elmo3`

`model_link='https://tfhub.dev/google/elmo/3`

`model_link=$model_link'?tf-hub-format=compressed'`

`wget $model_link -O model`

`tar xvzf model`

`rm model`

## Run the code in the `generate_summaries.ipynb` file

Generated summaries are stored in a file called `summaries.txt`. This file stores the reference summaries and generated ELMo and Word2Vec summaries. Each document's summaries are separated by `\n@@@\n`. The summaries for a document are separated by `\n&&&&\n` with the first summary being the refernce summary, the second summary being the Word2Vec summary, and the third summary being the ELMo summary. 
