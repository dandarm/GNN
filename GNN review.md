# Zhou

Esempi di sistemi su rete e aree di ricerca
social science (social networks (Wu et al., 2020), natural science (physical systems (Sanchez et al., 2018; Battaglia et al., 2016) and protein-protein interaction networks (Fout et al., 2017)), knowledge graphs (Hamaguchi et al., 2017) and many other research areas (Khalil et al., 2017)

##### principali branche
- Geometric deep learning, (Bronstein et al., 2017)
- graph representation learning (Cui et al., 2018a; Hamilton et al., 2017b; Zhang et al., 2018a; Cai et al., 2018; Goyal and Ferrara, 2018)
	- DeepWalk (Perozzi et al., 2014)
	- node2vec (Grover and Leskovec, 2016)
	
	Svantaggi: 
		- no parameters are shared
		- lack the ability of generalization
	
Zhang et al. (2019a) propose another comprehensive overview of graph convolutional networks.  Papers by Zhang et al. (2018b), Wu et al. (2019a), Chami et al. (2020)
are the most up-to-date survey papers on GNNs

- Node-level
- Edge-level
- Graph-level

- Propagation Module 
	- Convolution 
		- (spatial approach)
			- GraphSAGE (Hamilton et al., 2017a) uniformly samples a ﬁxed-size set of neighbors to aggregate information. GraphSAGE suggests three aggregators: mean aggregator, LSTM aggregator, and pooling aggregator
			- Neural FPs uses different weight matrices for nodes with different degrees
			- GAT. The graph attention network (Velickovic et al., 2018)
			- GaAN. The gated attention network  (Zhang et al., 2018c)
			- Gilmer et al. (2017) propose the **message passing neural network** (**MPNN**), which uses message passing functions to unify several variants.
			   The model contains two phases: a message passing phase and a readout phase. 
			   In the message passing phase, the model ﬁrst uses the message function $M_t$ to aggregate the “message” $m^t_v$ from neighbors and then uses the update function $U_t$ to update the hidden state $h^t_v$
			   The readout phase computes a feature vector of the whole graph using the readout function $R$
			- Battaglia et al. (2018) propose the **graph network (GN)**. It deﬁnes a more general framework for learning node-level, edge-level and graph-level representations
		- spectral approach
				- in almost all of the spectral approaches mentioned above, the learned ﬁlters depend on graph structure. That is to say, the ﬁlters cannot be applied to a graph with a different structure
	- Recurrent
		- The major difference between recurrent operators and convolution operators is that layers in convolution operators use different weights while layers in recurrent operators share same weights
		- (Scarselli et al., 2009; Gori et al., 2005), extended existing neural networks to process more graph types
	- skip connection

- Sampling Module
- Pooling Module
