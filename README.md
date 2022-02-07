# Double-Stack BERT

## What's Double-Stack BERT?
Double-Stack BERT is a method used to extract document embeddings for documents that has narrative properties such as book synopsis. It's called a double-stack BERT because it used two different BERT-based models to gain said output. Double-Stack BERT is made to create document embeddings by these high-level steps:
1. Splitting a document into its sentences
2. Exctracting each of the sentence's embedding using SBERT [(Reimers & Gurevych)](https://arxiv.org/abs/1908.10084)
3. Treating each sentence as a token, making a document a sequence of tokens
4. Using these sequences as input for an untrained RoBERTa model
5. Extracting the last input layer of RoBERTa to use as a document vector (that has the information of inter-sentence relation)
6. Contatenating the document vector and the content vector exctracted by using the previous SBERT


## Why Double-Stack BERT?
BERT [(Devlin et al, 2019)](https://arxiv.org/abs/1810.04805) (Bidirectional Encoder Representation from Transformer)is a revolutinary language model that changed the whole NLP world.
> "BERT is designed to pre-train deep bidirectional representations from unlabeled text by jointly conditioning on both left and right context in all layers. As a result, the pre-trained BERT model can be fine-tuned with just one additional output layer to create state-of-the-art models for a wide range of tasks, such as question answering and language inference, without substantial task-specific architecture modifications."

By having this bidirectionality, BERT can learn words by its context. Using that intuitive, Double-Stack BERT tried to learn sentences by its context in a text by turning the sentences into tokens.

## What do you use Double-Stack BERT for?
You use it for document embedding! From conducted experiments*, it has shown that adding the document vector that contains inter-sentence relation improves its performance. It's especially great for longer documents and for documents that has its own narative (ex. book synopsis, news article, etc)

*Thesis and experiment results are available soon
