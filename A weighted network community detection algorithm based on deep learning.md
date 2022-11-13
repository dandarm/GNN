[[Papers]]
[[Communitydetection]]
[community_Detection_weighted.pdf]
[[autoencoder]]

community detection methods are mostly focused on the investigation at unweighted networks.
[]()

the weighted adjacency matrix of the network can be used as the similarity matrix of the network

only considers the similarity among the nodes and their neighbors and does not consider the similarity among their neighbors and their second-order neighbors.

Therefore, this paper uses a similarity matrix that considers the similarity among the nodes in a network and the corresponding second-order neighbors

![[Screenshot_20220930-133511_Xodo Docs 1.jpg]]

W u v represents the weight of the edge that directly connects node u and node v, and the term on the right is the sum of the weights of the paths of node u and node v through the common neighbors. α + β= 1.

Definition 3 (similarity matrix X): Given a network graph G = (V, E, W ) , X ij = Sim v i , v j 

q ij = w ij − w i w j / 2 W

Autoencoedr

We take a vector x i ∈ R n ∗1 in the similarity matrix X = { x 1 , x 2 , . . . , x n } obtained as discussed in section III as an input to the autoencoder



for obtaining three similarity matrices of the second-order neighbors of the weighted network, the modularity matrix, and the adjacency matrix of the unweighted second-order neighbors in the weighted network. The second part includes the feature extraction module, which uses three similarity matrices as the training set and the similarity matrix of the second-order neighbors in the weighted network as the test set to obtain a low-dimensional feature matrix of the network topology. The third part involves using the K-means clustering method to cluster the low-dimensional feature matrix and obtain community detection results.