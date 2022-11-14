[2102.107575v5.pdf]

[[Survey]]
DIG library  https://github.com/divelab/DIG/



CONSTRASTIVE LEARNING
Given training graphs, contrastive learning aims to learn one or more encoders such that representations of similar graph instances agree with each other, and that representations, of dissimilar graph instances disagree with each other

Two views generated from the same instance are usually considered as a positive pair and two views generated from different instances are considered as a negative pair


PREDICTIVE LEARNING
predictive learning methods train the graph encoder f together with a prediction head g under the supervision of informative labels self-generated for free.

we summarize predictive learning frameworks for graphs into
(1) graph reconstruction that learns to reconstruct certain parts of given graphs, 
(2) invariance regularization that aims to directly learn robust and informative representations, 
(3) graph property prediction that learns to model non-trivial properties of given graphs, 
(4) multi-stage self-training with pseudo-labels.


self-supervised learning applied to graph data is still an emerging field and has significant challenges to be addressed