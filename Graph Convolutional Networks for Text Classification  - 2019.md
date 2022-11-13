[4725-Article Text-7764-1-10-20190707.pdf]

[[NLP]]
[[withcode]]  (https://github.com/yao8839836/text_gcn) 

We construct a single large graph from an entire corpus, which contains words and documents as nodes. The edge between two word nodes is built by word co-occurrence information and the edge between a word node and document node is built using word frequency and word’s document frequency. We then turn text classification problem into a node classification problem.

this is the first study to model a whole corpus as a heterogeneous graph and learn word and document embeddings with graph neural networks jointly

GCN was also explored in several NLP tasks such as semantic role labeling (Marcheggiani and Titov 2017), relation classification (Li, Jin, and Luo 2018) and machine translation (Bastings et al. 2017), where GCN is used to encode syntactic structure of sentences. Some recent studies explored graph neural networks for text classification (Henaff, Bruna, and LeCun 2015; Defferrard, Bresson, and Vandergheynst 2016; Kipf and Welling 2017; Peng et al. 2018; Zhang, Liu, and Song 2018). 
However, they either viewed a document or a sentence as a graph of word nodes

In contrast, when constructing the corpus graph, we regard the documents and words as nodes (hence heterogeneous graph) and do not require inter-document relations.

The number of nodes in the text graph |V| is the number of documents (corpus size) plus the number of unique words (vocabulary size) in a corpus.


we feed the graph into a simple two layer GCN as in (Kipf andWelling 2017), the second layer node (word/document) embeddings have the same size as the labels set and are fed into a softmax classifier
 A two-layer GCN can allow message passing among
nodes that are at maximum two steps away. Thus although there is no direct document-document edges in the graph, the two-layer GCN allows the information exchange between pairs of documents