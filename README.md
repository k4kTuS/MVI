# Extraction of Skills and Benefits from Job Postings Descriptions
This is a semestral project for a FIT CTU course on Computational Intelligence Methods. Initial topic research is summarized in `milestone.pdf` and the final project report in `report.pdf`.

## Assignment description
Given a dataset of job postings (eg. https://www.kaggle.com/datasets/promptcloud/indeed-job-posting-dataset), your task is to efficiently extract relevant skills and benefits mentioned in the descriptions. In the world of rapid job matches, processing speed is paramount, so your solution should be optimized for performance. Do not use ChatGPT API.

**Skills and Benefits Extraction:**

Develop or employ a method to extract skills from the job descriptions. This could be based on NLP techniques (eg. BERT embeddings).
Similarly, extract benefits from the job descriptions.
Ensure that the extracted skills and benefits are not overlapping.

**Performance Optimization:**

Profile your initial extraction method to identify any bottlenecks.
Apply optimization techniques to enhance processing speed. This can involve algorithmic optimizations, parallel processing, or using more efficient data structures.
Benchmark the optimized method against the initial one to quantify the improvement.

**Validation:**

Randomly select a subset of job postings and manually annotate the skills and benefits.
Compare the manual annotations with the extracted data to calculate precision, recall, and F1-score.

## Data description
#### Job postings dataset:
* Available at [Kaggle](https://www.kaggle.com/datasets/promptcloud/indeed-job-posting-dataset)
* Contains scraped job ads with some additional information. I only utilized the raw scraped description texts
* For preprocessing, I removed HTML tags, split the descriptions into sentences using `nltk` library, further split the sentences by newlines (I wanted to preserve information partition from bullet points etc.) and removed some special characters that I found irrelevant. This created a list of sentences that were then used as inputs

#### Job postings labelled subset
* Filepath: `data/df_sample_labeled.csv`
* I manually labelled a small subset of data, using ESCO skill indexes, that I used to validate my approach

#### ESCO skills ontology
* Filepath: `data/skills_en.csv`
* Also available for download from [ESCO website](https://esco.ec.europa.eu/en/use-esco/download)
* I created embeddings for all of the skills and then used them to extract skills within job ads by calculating vector similarity between sentences and skills in the ontology

## Run instructions
The whole implementation is in an `.ipynb` file. The code was run on Kaggle platform so that I could utilize their GPU resources, multiple CPUs, recently increased RAM size and convenient way to directly include the dataset as it is also at Kaggle.

If you want to run the code on your machine, download the `.ipynb` file from this repository together with `data/skills_en.csv` and then download the job ads dataset from [Kaggle](https://www.kaggle.com/datasets/promptcloud/indeed-job-posting-dataset). The notebook contains further comments and descriptions of code.

You can also access my [Kaggle Notebook](https://www.kaggle.com/code/matusbotek/job-ads-skill-extraction) and clone it to run the code with Kaggle's resources.

## Acknowledgement
This publication uses the ESCO classification of the European Commission.

