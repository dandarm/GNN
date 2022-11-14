[1809.10341.pdf]
[[NOTEVOLI]]


Velickovic et al.

general approach for learning node representations within graph-structured data in an unsupervised manner
The learnt patch representations summarize subgraphs centered around nodes of interest, and can thus be reused for downstream node-wise learning tasks.

it is unclear whether randomwalk objectives actually provide any useful signal, as these encoders already enforce an inductive bias that neighboring nodes have similar representations.

an alternative objective for unsupervised graph learning that is based upon mutual information

DIM relies heavily on convolutional neural network structure in the context of image data, and to our knowledge, no work has applied mutual information maximization to graph-structured inputs. Here, we adapt ideas from DIM to the graph domain,

