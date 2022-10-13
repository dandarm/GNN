arxiv  2106.00761

Link prediction is one ofthe central problems in graph mining. However, recent studies highlight the importance ofhigher-ordernetwork analysis,
We first show that existing link prediction schemes fail to effectively predict motifs
GNNs ensure highest accuracy of predicting motifs

Importantly, the advantages of our approach over schemes based on uncorrelated link prediction increase with the increasing motif size and complexity

ofhigher-order graph organization [9], finding and analyzing small recurring subgraphs called motifs, graph patterns (eg. 𝑘-cliques, 𝑘-stars, 𝑘-clique-stars, 𝑘-cores)

Motifs are central to many graph mining problems in computational biology, chemistry, and a plethora of other fields [11, 13, 14, 30, 33, 48, 51]

general motifprediction, i.e., analyzing whether specified complex structures may appear in the data. As with link prediction, it would enable predicting the evolution of data, but also finding missing structures in the available data

A score function that assesses the chances for a given motif to appear and consider the combinatorially increased complexity of the problem (compared to link prediction)

a motif may be formed by an arbitrary set 𝑉𝑀 of vertices, and potential edges between these vertices can be large, i.e., 𝑂(|𝑉𝑀 |2).
This leads to novel issues, not present in link prediction

Extending the state of the art SEAL link prediction framework.
For a given motif 𝑀, we train our architecture on what is the “right motif surroundings” (i.e., nearby vertices and edges) that could result in the appearance of𝑀. Then, for a given set ofvertices 𝑉𝑀, the architecture infers the chances for 𝑀 to appear
The key challenge is to be able to capture the richness of different motifs and their surroundings

negative samples, i.e., subgraphs that resemble the searched motifs but that are not identical to them.  close surroundings” (i.e., nearby vertices and edges, 1–2 hops away

we observe that the larger the motifto predict becomes (larger 𝑘), the more advantages our architecture delivers. This is because larger motifs provide more room for correlations between their associated edges.  Finally, SEAM also successfully predicts more arbitrary communities or clusters 

(1) identifying and formulating the motifprediction problem and the associated score functions, (2) showing how to solve this problem with heuristics and graph neural networks, and(3) illustrating thatgraph neural networks can solve this problem more effectively than heuristics



### motif prediction and score function

Link prediction is a “binary” problem: for a given pair of unconnected vertices, there can only be one link appearing. In motif prediction, the situation is more complex. There are many possible motifs to appear between given vertices 𝑣1, ..., 𝑣𝑘
there are 2(𝑘 2) − 1 motifs (with between 1 and 2 �𝑘 edges) (counting also isomorphic motifs on different vertex ordering)

There May Be Existing Edges
There May Be “Deal-Breaker” Edges :  the appearance edges which would make the appearance of a given motif unlikely or even impossible

Type of motiv edges:  motif edges are a union oftwo types of motif edges: edges that do not exist in 𝐺 nad edges that already exist

there may be edges between vertices in 𝑉𝑀 which do not belong to 𝑀

𝐸𝑀,D,N are dealbreaker edges that do not exist in 𝐺: if a given deal-breaker edge does not exist, but it does have a large chance of appearing – the motif score should become lower

-> A score for each possible motif to asses which is likely to occur.  we assume that a motif score should be high if the scores of participating edges are also high. we harness existing link prediction scores for edges from 𝐸𝑀.
But simply extending link prediction fails to account for possible correlations between edges forming the motif.

In the case where there a no deal breaker edges:  the score
of a given specific motif 𝑀 be the product of the scores of the associated edges ((𝑒) is any link prediction score which outputs into [0, 1] (e.g., Jaccard)) 
To incorporate deal-breaker edges, we generalize the motif score defined previously as 𝑠∗
⊥(𝑀) = Î 𝑒 ∈𝐸𝑀 𝑠 (𝑒)· Î 𝑒 ∈𝐸𝑀,D (1 − 𝑠 (𝑒)),

Thus, whenever 𝑒 is a deal-breaker, using 1 − 𝑠 (𝑒) has the desired diminishing effect on the final motif score

is how to aggregate the link predictions taking into account the rich structural properties of motifs. Intuitively, using a plain product of scores implicitly assumes the independence of participating scores.. 
To capture such positive correlations, we propose heuristics based on the convex linear combination oflink scores.

-> our motif prediction scores based on the convex linear combination of link scores are always at least as large as the independent products of link scores
 **The difference (𝐶 −𝑃) is due to link correlations**
 similarly for negative correlations on deal-broker edges
 quindi in formule: $s(M) = \langle w,s(e)\rangle$    

we assign a unit score for each existing edge 𝑒 ∈ 𝐸𝑀,E.
we set a score for each Non-existing edge 𝑒(𝑢,𝑣) as (jaccard similarity)
the weights are uniform

for the negative correlations, the sign is negative, and for edges $\in Deal breaker$ the value is $0$ 

final prediction score: formula (2)


### SEAM GNN ARCHITECTURE
that one could use neural networks to learn a heuristic for motif prediction.
a GNN may be able to learn link correlations better than a simple hand-designed heuristic

