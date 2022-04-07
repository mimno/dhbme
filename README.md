# Supporting materials for DH Beyond Modern English presentation

## embedding_neighbors.tsv

The closest 20 words for the 1000 most frequent terms. Embedding models can be variable.I trained four embedding models with different random seeds, and I'm searching each of them for the query word to get each model's top 20 words. I then search each model for the union of those sets and sort by the mean cosine similarity. The closest word to a query word is itself, I've left these in as a confidence check.

These similarities ignore word frequency, so the closest vector to a given vector may be an unusual or infrequent word.

## similar_topics.txt

I trained a 500-topic model on the EEBO documents. For each topic I'm removing vowels, apostrophes, and double letters and then looking for pairs of topics that have similar letter sequences after this transformation. The topics are in order by ID number, this is purely an artifact of the training process and has no significance. For each topic I'm returning the five closest topics.

## s_th.tsv

This file contains instances of pairs of words ending in -s or -th. The -eth ending can become -s or -es, I've chosen whichever is more frequent. I have not filtered these words in any other way, some of them are plural nouns.

## cluster_words.txt

I trained a 500-cluster model on one of the word embedding models. This clustering looks a lot like a topic model, but is more influenced by syntactic similarity, and each word can only occur in one cluster. The clusters are in descending order by number of total words, and within each cluster words are in descending order by frequency.

## word_clusters.txt

Using the same hashing function as with the topics, I'm finding sets of words that hash to the same pseudo-root. Note that these are *not* necessarily related words! I'm then checking which of the 500 embedding clusters each word appeared in, words in the same cluster show up in brackets.
