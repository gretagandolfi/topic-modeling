# topic-modeling
_Computational Skills for Text Analysis_ project

The repository contains the Jupyter Python Notebook with the code and its description. 


Topic Modeling is a statistical modeling used to extract the hidden topics or structures from large corpora. Why are the topics hidden? Because they are not clearly visible or clearly stated by the author(s) of the corpus. Topic modeling is a unsupervised tecnique.
There are some algorithms that can be used for topic modeling: LDA, PLDA, LSI. Here I used LDA (Latent Dirichlet allocation), that is a very popular algorithm and has an implementation in Gensim Python library.
How does LDA work?

input: corpus with N documents and K topics.

training:
it goes through each document and randomly assigns each word in the document to one of K topics. This random assignment gives random topic representations of all documents and word distributions of all the topics.
- For each document d, compute P( topic t | document d ) := proportion of words in document d that are assigned to topic t
- For each topic t, P( word w | topic t ) := proportion of assignments to topic t that come from word w (across all documents)
- For each word w, reassign topic t’, where it chooses topic t’ with probability P( topic t’ | word w ) = P( topic t’ | document d ) * P( word w | topic t’ )

output: prediction on the probability that topic t’ generated word w and the final values of P( word w | topic t ) and P( topic t | document d).

The general structure of my project follows these passages:
- text processing
- lda training
- evaluation and visualization of outcomes

The performance of the topic modeling technique relies on:
- the corpus analyzed
- its processing
- the algorithm
- its parameters

I started from two texts:
- Infinite Jest(1996): an encyclopedic novel by David Foster Wallace.
- Brown corpus(1960): a corpus of 500 samples of English-language text, compiled by Henry Kučera and W. Nelson Francis form works published in the USA in 1961.

More precisely,
- Text processing

I cleaned them trough tokenization, lemmatization and filtering.

I divided the texts into documents.
 - LDA training

I prepared dictionaries and bag of words per document needed as input by the algorithm.

I trained the algorithm, printing the outputs.
- Visualization and Evaluation of outputs and model

I tried to visualize the results with pyLDAvis and to evaluate them computing the coherence of the model.
As I stated above*, the performance of LDA is influenced by the input (the corpus and how it is processed) and by the parameters of the algorithm. For these reasons, I tried apply some modifications at the level of:

- text cleaning:

I pos-tagged the texts,

I create two new corpora composed only by common nouns, and by common nouns and adjectives,

I filtered words according to their length.
parameters tuning: I tried to see how the coherence and the perplexity of the models are related to:

the number of topics,

the number of passes.

I selected the modifications that gave the best results (in terms of coherence of results for every corpus), and I applied them. Then, I tried to evaluate the new models and to visualize their outputs, in order to see whether the improvements could be visible or not.
