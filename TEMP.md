(https://distill.pub/2021/gnn-intro/)

- node feature: a vector for each node
- graph connectivity: 
	- adjacency matrix, but for many nodes it can be very sparse and innefficient. There are many adjacency matrix for the same connectivity, leading potentially to different results in a neural network.
	- adjacency lists (es: [[1,0], [2,0], [4,3],...])

GNN: **an optimizable transformation on all attributes of the graph that preserves graph symmetries (permutation invariances).**

the “message passing neural network” framework proposed by Gilmer et al. **Neural Message Passing for Quantum Chemistry** 2017
using the Graph Nets architecture schematics introduced by Battaglia et al.
**Relational inductive biases, deep learning, and graph networks**  2018.

This GNN uses a separate multilayer perceptron (MLP) (or your favorite differentiable model) on each component of a graph; we call this a GNN layer. For each node vector, we apply the MLP and get back a learned node-vector. We do the same for each edge, learning a per-edge embedding, and also for the global-context vector, learning a single embedding for the entire graph


----

Relational data representing relationships between entities is ubiquitous on the Web (e.g., online social networks) and in the physical world (e.g., in protein interaction networks). Such data can be represented as a _graph_ with _nodes_ (e.g., users, proteins), and _edges_ connecting them (e.g., [friendship relations](https://ai.googleblog.com/2016/09/research-from-vldb-2016-improved-friend.html), protein interactions). Given the widespread prevalence of graphs, [graph analysis](https://ai.google/research/teams/algorithms-optimization/graph-mining/) plays a fundamental role in machine learning, with applications in [clustering](https://ai.googleblog.com/2018/03/balanced-partitioning-and-hierarchical.html), [link prediction](https://ai.googleblog.com/2016/09/research-from-vldb-2016-improved-friend.html), [privacy](https://ai.googleblog.com/2015/08/kdd-2015-best-research-paper-award.html), and [others](https://ai.googleblog.com/2017/08/google-at-kdd17-graph-mining-and-beyond.html). To apply machine learning methods to graphs (e.g., predicting new friendships, or discovering unknown protein interactions) one needs to _learn_ a representation of the graph that is amenable to be used in ML algorithms_._


# Why networks?
Networks are a general language for describing and modeling complex systems


Come possiamo creare un vettore di embedding per raprresentare un nodo?
esempio del zachary's karate club network (deepwalk perozzi)

### non c'è un ordine tra i nodi

### qual'è la definizione di similarità tra i nodi?

simplest encoding: lookup embedding table
	-node2vec, deepwalk, LINE

-> i nodi per essere simili devono  essere connessi? devono condividere un vicinato? o avere simili ruoli strutturali?

JHamilton 2017 representation learning on graphs:
- adiacency based similarity: 	similarity is the edge weight between u and v in the original network
- multi-hop similarity  (k-hop cioè primi k vicini), train embedding to predicty k-hop neighbours  CAo 2015
- neighbours overlap similarity  HOPE (Yan 2016)

issues: O(V^2)

-> randomwalk apporaches

fin qui è tutto unsupervised

goyal and ferrara 2017 survey


grafi che variano nel tempo

---


