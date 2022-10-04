\section{Network reconstruction for socio-economic resilience}

Economic system resilience needs improvements, after a series of events like the global financial crisis and Covid-19 pandemic that shown the vulnerabilities of the economic system.\\

The key to increase system resilience is in the knowledge of economic network of interdependencies, and the understanding of shock dynamics. In order to improve that, a complete economic network data is needed, \textbf{but privacy concerns limit access to those data}, which is therefore not fully available and incomplete, \textbf{hence the need for network reconstruction methods}.\\

Already existing statistical methods for network reconstruction need knowledge of network general properties and constraints, based on human understanding of data. A new set of methods borrowed from \textbf{Machine Learning} techniques can in principle learn these network properties and the most useful features from data, so to obtain better reconstruction accuracy.\\

These ML models are \textbf{Graph Neural Networks (GNNs)}, which are capable of learning a compressed powerful representation of input network data, but as other ML models are inherently black-boxes.\\

In this project we will develop \textbf{a new generation of reconstruction techniques that combine the strengths of both the statistical and ML approaches} to network reconstruction, that is interpretability and performance. \\

A focus will be also in building innovative ML architectures and generative models for network data.


\subsection{Network reconstruction}
Statistical physics methods are widely used in networks description when the only known variables are macroscopic ones, in particular Shannon entropy maximization uses available constraints to generate a probabilistic description. 
This method induces a class of probabilistic models called Exponential Random Graphs (ERGs), widely used as state of the art for accurate financial networks reconstruction, while reconstruction of supply chain networks is harder due to its nature and structure. 
This approach prevents one from making assumptions that are not supported by empirical information and that would bias the entire estimation procedure.\\

\subsection{Graph Neural Networks for reconstruction}
GNN will be applied for learning the connectivity structure of input graphs and compress this information along with nodes features in the embedding space, which is typical a lower dimensional space respect to the input feature space. 
Node features can represent non-topological metadata (such as the equity of a bank or the revenue and technological sector of a firm) as well as local network statistics (a node degree, its clustering, motifs, and so on).\\

Combining Statistical Physics methods with GNN learning approaches will likely increase the accuracy on network reconstruction.

