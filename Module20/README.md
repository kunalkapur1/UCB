**Summary and next steps**

For this initial experiment, I started with 70 raw logs, and after applying some rudimentary text replacement/cleanup, quickly narrowed down to 15 unique (tokenized_sorted_log) patterns.
For the baseline, applying TfidfVectorizer and Cosine similarity, with DBSCAN yielded 14 log clusters.

For next steps, I will apply other ML models to try to further reduce the number of clusters, identify outliers, and visualize the data better. Also, gradually grow the volume of logs to better analyze each model's performance.

Algorithms to evaluate (planned/wip):
* TF-IDF + K-Means
* Sentence Embeddings + HDBSCAN
* TF-IDF + Isolation Forest
* TF-IDF + Naive Bayes

Link to Jupyter Notebook: https://github.com/kunalkapur1/UCB/blob/main/Module20/AIOps-LogAnalysis.ipynb
