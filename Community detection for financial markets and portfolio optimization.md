### Introduction


One of the most important properties of complex systems is community structure. Real-world complex systems are organized in a modular way, with clusters of units sharing similar dynamics or functionality. 
In financial market systems is present an emergent, intermediate level of structure standing in between the microscopic dynamics of individual financial entities and the macroscopic dynamics of the market as a whole. This is a mesoscopic scale that corresponds to sets of stocks that share similar price dynamics, that is a set of modules whose dynamical activity is more correlated internally than with that of other modules.
The presence of a mesoscopic structure might be revealed in an entirely data-driven approach, looking for a modular and possibly hierarchical organisation of the empirical correlation matrix between financial time series.


Over the past years, scientists have deployed and developed many time series techniques to retrieve qualitative information regarding the hierarchy and structure offinancial markets [1–4].  A promising approach is that of employing community detection techniques, developed in network theory [5, 6], on empirical correlation matrices resulted from multiple stock time series.
However, the methods are originally constructed to detect dense clusters of nodes within graphs (networks), and are not suitable when replacing the network data with correlation matrices, because that procedure tends to be intrinsically biased due to its inconsistency with the null hypotheses underlying the existing algorithms. 
Recently, a novel method was proposed, which has been specifically designed to detect communities from correlation matrices of multiple time series [7].  This method is based on Random Matrix Theory, which identifies the optimal hierarchical decomposition of the system into internally correlated and mutually anti-correlated communities. 
This technique allow for the discover of the intermediate, mesoscopic, market structure that turns out to be the most stable over time and provides important practical insights from a portfolio management perspective, analysing the stock cluster that emerge after filtering.


### Random Matrix Theory
The following approach from (7) is considered.
Let's consider a system of N time series over T time steps:  $$X_i \equiv \{x_i(1), x_i(2), ..., x_i(T)\},\qquad i = 1 ... N$$
In the case of financial markets, $i$ is one particular stock and $x_i(t)$ is the log-return of stock $i$:
$$
r_i(t) \equiv log \begin{bmatrix} \frac{P_i(t+1)}{P_i(t)}\end{bmatrix}
$$
For each stock in the system we use the time series of it’s log-returns for the analysis.\\

The vast majority of the available techniques aimed at quantifying the level of mutual dependency within such a set of multiple time series exploit the information encoded in the $N×N$ crosscorrelation matrix. The cross-correlation matrix $C$ measures the mutual dependencies among N time series on a scale between −1 and 1. The ij-th entry of $C$ is defined as the Pearson correlation coefficient:

\begin{equation}$$
C_{ij} \equiv Corr[X_i,X_j] \equiv \frac{Cov[X_i,X_j]}{\sqrt{Var[X_i]\cdot Var[X_j]}}

$$\end{equation}
where

$$
Cov[X_i,X_j] \equiv \overline{X_i X_j} - \overline{X_i} \cdot \overline{X_j}
$$

$$
Cov[X_i,X_i] = \overline{X_i^2} \cdot \overline{X_j}^2 \equiv Var[X_i]
$$

with
$$
\begin{aligned}
\overline{X_i} \equiv \frac{1}{T} \sum_{t=1}^{T} x_i(t)\\
\overline{X_i^2} \equiv \frac{1}{T} \sum_{t=1}^{T} x_i^2(t)\\
\overline{X_i X_j} \equiv \frac{1}{T} \sum_{t=1}^{T} x_i(t) x_j(t)
\end{aligned}
$$
It is commonly assumed that each time series $X_i$ has been standardized, that is being subtracted its mean and divided by its standard deviation: $(X_i - \overline{X_i}) / \sigma_i$ . After standardization the following apply:
$$
\begin{aligned}
\overline{X_i} = 0 \\
Var[X_i] = \overline{X_i^2} = 1\\
C_{ij} = Cov[X_i, X_j] = \overline{X_iX_j}
\end{aligned}
$$
and this result is consistent with \ref{covariance_matrix_simple}.

Assuming the above, it is possibile to apply the random matrix theory (RMT) [7, 17, 18], which is widely used in order to identify the non-random properties of empirical correlation matrices.

A correlation matrix constructed from $N$ completely random time series of duration $T$ has (in the limits $N → +∞$ and $T → +∞$ with $1 < T/N < +∞$) a very specific distribution of its eigenvalues, known as the Marcenko-Pastur or SenguptaMitra distribution [27, 28]:
\begin{equation} $$
\begin{align}
ρ(λ) = \frac{T}{N} \sqrt{\frac{(λ+ − λ)(λ − λ−)}{2πλ}} \;
\qquad if \;\;\;\; λ+ ≤ λ ≤ λ− \\
ρ(λ) = 0 \qquad else
\end{align}
$$\end{equation}

with:

\begin{equation} 
$$
\lambda_{\pm} = \begin{bmatrix} 1 \pm \sqrt{\frac{N}{T}}  \end{bmatrix}^2
$$\end{equation}

The eigenvalues between the range $[\lambda_-, \lambda_+]$ can be considered due to random noise.
Any other eigenvalues larger than the maximum $\lambda_+$ predicted by the Marcenko-Pastur distribution represent meaningful structure in the data  [6–8]
As also observed in a multitude of previous studies [4, 5], a typical feature of the spectrum of empirical correlation matrices is that the largest observed eigenvalue $λ_m$ is much larger than all other eigenvalues (figure), and the corresponding eigencomponent is the so-called _market mode_, a common factor influencing all stocks of the given market, accounting for most of the observed correlation among the stocks.

The empirical correlation matrix $C$ can thus be decomposed as the sum of the following matrices, being associated to the eigencomponents due to noise, the market, and the _group_ mode, the remaining component:

\begin{equation}
$$C = C^{(r)} + C^{(m)} + C^{(g)}$$
\end{equation}
where:

\begin{equation}
$$
\begin{aligned}
C^{(r)} \equiv \sum_{i: \; \lambda_i \; \leq \;\lambda_+} \lambda_i \ket{v_i}\bra{v_i} \\ \\

C^{(m)} \equiv \lambda_m \ket{v_m}\bra{v_m} \\ \\
C^{(g)} \equiv \sum_{i: \; \lambda_+ \lt \; \lambda_i \; \lt \;\lambda_m} \lambda_i \ket{v_i}\bra{v_i} 
\end{aligned}
$$
\end{equation}

The correlations in $C^{(g)}$  act at the level of sub-groups of stocks within a market. Broadly speaking, these groups are expected to reflect some sectorial or sub-sectorial classification of stocks according to their industrial category, however the overlap between nominal asset classes and groups of empirically correlated stocks is only partial [6–8].

### Community detection
In network analysis, community detection is the process of identifying relatively dense clusters of nodes. For an overview of researches in the area of community detection over the last decade see[10].
In [7,8,9] the focus is on using the method of modularity optimization [36] which is one of the most popular methods identifying non-overlapping communities. This method has the advantage, over other existing techniques, of being based on a null model, acting as a community-free benchmark to which the real network is compared. \\

In a network of $N$ nodes, it can be defined a number of different possibile partitions of the network, assigning to each node a partition membership label. The vector $\vec{\sigma}$ encode the membership partition number for each node $i$.
Modularity $Q(\vec{\sigma})$ as a measure of the effectiveness of a particular partition $\vec{\sigma}$ in identifying densely connected groups of nodes. The process of modularity optimization seeks to find the optimal partition that maximizes the value of $Q(\vec{\sigma})$, by varying the communities to which the different nodes of the network belong.

\begin{equation}$$
Q(\vec{\sigma}) = \frac{1}{A_{tot}} \sum_{i,j} \begin{bmatrix} A_{ij}
- \langle A_{ij} \rangle \end{bmatrix} \; \delta(\sigma_i, \sigma_j)
$$\end{equation}

where the $\delta$ function allow the contribution to the sum only for nodes within the same community, and  $A_{ij}$  is the adjacency matrix. The term $\langle A_{ij} \rangle$ represents the null model for the network, that is the expectation of $A_{ij}$ under a null hypothesis, that when true guarantees that no higher-order patterns (inclulding communities) are present.

The most popular null model for a binary network, known as the Configuration Model, is one where the expected value of the degree $k_i$ (the number of links belonging to node $i$) is equal to the value $\sum^N_{j=1} A_{ij}$ observed in the real network, and where the topology is otherwise completely random.

The average value given by this model is approximated by the expression:
\begin{equation} \label{null_model_network}$$
\langle A_{ij} \rangle = \frac{k_i k_j}{2 m}
$$\end{equation}

only when the heterogeneity of the degrees is weak [38, 39] ($m$ is the total number of links in the network), which gives an estimate of the probability that nodes i and j are connected, under the null hypothesis that the observed network’s structure is completely explained on the basis of the different degrees of vertices.
This expression holds for both undirected networks, where $A_{ij}$ has elements equal to either 0 or 1, and for weighted networks.

##### Resolution limit
It should be noted that the modularity function defined in eq. (Q di sigma) cannot prove wether found modules are indeed composed of submodules, that is it cannot resolve communities below a typical scale depending on the number of links and the module degrees [41].
It has been proposed [42] a way to change the resolution of the community detection by introducing an extra resolution parameter $φ > 0$ in the null model, replacing eq. Aij medio with

$$
\langle A_{ij} \rangle = \phi \frac{k_i k_j}{2 m}
$$
This _multi-resolution_ method can resolve smaller subcommunities, which are nested inside larger communities. However the introduction of the ad-hoc parameter $\phi$ can be avoided with a different approach theoretically consistent with the propoerties of correlation matrices. 

##### Inconsistency of modularity for cross correlation matrices
Identifying the correlation-based problem of finding the mesoscopic structure with the network-based community detection task it is not harmless, since treating the empirical correlation matrix $C$ as the adjacency matrix of a weighted network has a fundamental flaw.\\

Given the time series of the total increments $X_{tot} = \{x_{tot}(1), x_{tot}(2),..., x_{tot}(T)\}$ , $x_{tot}(t) = \sum_{j=1}^N x_j(t)$,  and  
\begin{equation} \label{degree_corr_matrix}
$k_i = \sum_{j=1}^N C_{ij} = Cov[X_i, X_{tot}]$
\end{equation}

\begin{equation}$$
\langle C_{ij}\rangle _{naive} = \frac{k_i k_j}{2 m} = Corr[X_i,X_{tot}] \cdot \; Corr[X_j, X_{tot}]
$$\end{equation}

When used within the modularity function, the above null model will not necessarily give more importance to pairs of strongly correlated time series, but rather to pairs of time series whose ‘direct’ correlation $C_{ij}$ is larger than the product of the correlations of each time series with the ‘common signal’ $X_{tot}$.
The null model in equation \ref{null_model_network} is meant to represent networks with given degrees $k_i$, matrices with given column and row sums, having the meaning of an important structural constraint. But in contrast sums over rows or columns of correlation matrices do not represent any meaningful constraint, as in \ref{degree_corr_matrix}.
Moreover the eigenvalue spectrum of $\langle C_{ij}\rangle _{naive}$ has high degeneracy, opposite to the eigenvalues distribution of any realistic correlation matrices.

As a benchmark to prove these inconsistency, let introduce N time series divided in $c$ communities specified by a 'true' partition $\vec{\sigma}^*$. Assume that each community A is made of $n_A$ standardized time series that are perfectly correlated with each other and completely uncorrelated to the time series in other communities. It can be shown [7.] that $\langle C_{ij}\rangle _{naive}$ is larger for pairs of time series belonging to larger communities. 
For the largest community, the expected internal correlation is always larger than the correlation among any pair of communities, so $C_{ij} - \langle C_{ij}\rangle _{naive}$  is very low and this community is paradoxically difficult to detect. \\

It is therefore clear that the correlation matrix cannot be used for ordinary network-based community detection, thus the need for more adequate null model.

### Finite time series with market mode
Redefining the modularity optimization with the following equation gives a null model consistent with the properties of correlation matrices:
begin{equation}$$
\begin{aligned}
Q(\vec{\sigma}) = \frac{1}{C_{norm}} \sum_{i,j} \begin{bmatrix} C_{ij}
- C_{ij}^{(r)} - C_{ij}^{(m)}  \end{bmatrix} \; \delta(\sigma_i, \sigma_j)\\
= \frac{1}{C_{norm}} \sum_{i,j} C_{ij}^{(g)}\; \delta(\sigma_i, \sigma_j)

\end{aligned}
$$\end{equation}

with   $C_{norm} = \sum_{i,j} C_{ij} = Var[X_{tot}]$,  the variance of the total increment $X_{tot}$ is a natural measure of the volatility of the system over the considered time window, which in the case of financial time series is an important property of the market.

The above definition has to be considered and incorporated into community detection algorithms that seek to maximize the modularity, such as the Potts method or the Louvain method.\\

The problem of multiresolution has been addressed by running the community detection algorithm recursively inside each of the communities, so that to resolve subcommunities within communities. Iterating this procedure identifies a hierarchical community structure, if present. Within each community, the procedure stops automatically when it resolves no further subcommunities.

##### Results
Metto un paio di figure di torte, fig 8 e fig 13



applying these modified methods to real financial markets, leads to the results shown in fig??.

finisco con [[tiziano dic 2021 mesoscopic structure portfolio optimization]]
 



1. Sinha S, Chatterjee A, Chakraborti A, Chakrabarti BK. Econophysics: An Introduction. Wiley-VCH, Weinheim; 2010.
2. Bouchaud JP, Potters M. Theory of Financial Risk and Derivative Pricing. Cambridge University Press, 2nd ed; 2003.
3. Mantegna RN, Stanley HE. Introduction to Econophysics: Correlations and Complexity in Finance. Cambridge University Press; 1999.
4. Mantegna RN. Hierarchical Structure in Financial Markets. Eur Phys J B. 1999; 11, 193. doi: 10.1007/ s100510050929
5. Fortunato S. Community detection in graphs. Phys Rep. 2010; 486, 75. doi: 10.1016/j.physrep.2009. 11.002
6. Newman MEJ. Networks, an Introduction. Oxford University Press; 2010. 
7. MacMahon M, Garlaschelli D. Community detection for correlation matrices. Phys Rev X. 2015; 5, 021006.
8. : I. Anagnostou, T. Squartini, D. Kandhai & D. Garlaschelli (2021) Uncovering the mesoscale structure of the credit default swap market to improve portfolio risk modelling, Quantitative Finance, 21:9, 1501-1518, DOI: 10.1080/14697688.2021.1890807
9. Almog A, Besamusca F, MacMahon M, Garlaschelli D (2015) Mesoscopic Community Structure of Financial Markets Revealed by Price and Sign Fluctuations. PLoS ONE 10(7): e0133679. https://doi.org/10.1371/journal.pone.0133679

[7] M. Potters, J.P. Bouchaud and L. Laloux, Financial Applications of Random Matrix Theory: Old Laces and New Pieces, Acta Physica Polonica B, 36, 2767 (2005).
[17] E.P. Wigner, Characteristic Vectors of Bordered Matrices With Infinite Dimensions, The Annals of Mathematics, 62, 548 (1955).
[18] M.L. Mehta, Random Matrices, (Elsevier 2004)

[27] V. Plerou, P. Gopikrishnan, B. Rosenow, L.A.N. Amaral and H.E. Stanley, Universal and Nonuniversal Properties of Cross Correlations in Financial Time Series, Phys. Rev. Lett., 83, 1471 (1999).
[28] L. Laloux, P. Cizeau, J.P. Bouchaud and M. Potters, Noise Dressing of Financial Correlation Matrices, Phys. Rev. Lett., 83, 1467 (1999).

[6] A. Utsugi, K. Ino and M. Oshikawa, Random Matrix Theory Analysis of Cross Correlations in Financial Markets, Phys. Rev. E, 70, 026110 (2004).
[8] V. Plerou, P. Gopikrishnan, B. Rosenow, L.A.N. Amaral, T. Guhr and H.E. Stanley, Random Matrix Approach to Cross Correlations in Financial Data, Phys. Rev. E, 65, 066126 (2002).

[4] S. Sinha, A. Chatterjee, A. Chakraborti, and B.K. Chakrabarti, Econophysics (Wiley-VCH. 2011).
[5] J.P. Bouchaud and M.Potters, Theory of Financial Risk and Derivative Pricing (Cambridge University Press 2003), 2nd ed.
[10] S. Fortunato, Community Detection in Graphs, Physics Reports , 3-5, 75 (2010).
[36] M.E.J. Newman and M. Girvan, Finding and Evaluating Community Structure in Networks, Phys. Rev. E, 69,026113 (2004).

[38] D. Garlaschelli and M.I. Loffredo, Maximum Likelihood: Extracting Unbiased Information From Complex Networks, Phys. Rev. E, 78(1), 015101 (2008).
[39] T. Squartini and D. Garlaschelli, Analytical MaximumLikelihood Method to Detect Patterns in Real Networks, New Journal of Physics, 13(8), 083001 (2011).
[41] S. Fortunato and M. Barthelemy, Resolution Limit in Community Detection, Proc. Natl. Acad. Sci. USA, 104, 36 (2007).
[42] J. Reichardt and S. Bornholdt, Detecting Fuzzy Community Structures in Complex Networks with a Potts Model, Phys. Rev. Lett., 93, 218701 (2004).