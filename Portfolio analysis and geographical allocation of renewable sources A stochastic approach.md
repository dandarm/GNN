[[Papers]]
[2019 - ENPOL - Portfolio Allocation.pdf]
[[energysource]]
[[Portfolio optimization]]


### Introduction

The exploitation of planetary resources as infinite source, regardless of the environmental impact, should be heavily reconsidered. For this reason Green and Sustainable Economy is gaining importance as a concrete economic development model.
The European Union has implemented, in accordance with the post-Kyoto protocol, the package “Climate-Energy 20-20-20” which has three main objectives:  20% emissions reduction compared to 1990 levels;  reaching the renewable share of 20% compared to the gross final consumption; improving energy end-use efficiency of 20% (Cucchiella et al., 2017). 
The implementation of such incentive policies favoured in the last years the spread of renewable energy sources (mainly wind and photo voltaic), considered almost inexhaustible while ensuring a drastically reduced environmental impact when compared to traditional sources.

With regards to the impact of renewable energy sources on the
power grid, production from intermittent renewable sources brings with it challenges in terms of matching demand and supply on a real time basis (Brouwer et al., 2014)

The limited programmability of solar and wind generation capacity has partly offsetting the environmental and economic advantage of such renewable sources (Facchini, 2017)
Battery storage is often cited as a definite solution to this problem but it is still expensive and hardly scalable (Weitemeyer et al., 2015)

A viable approach would be to find an optimal spatio-temporal allocation of renewable energy production sites, in order to reduce characteristic fluctuations of renewable energy power. Limiting the fluctuations would be beneficial in reducing the impact on the grid and on the storage systems.

With regards to the optimal management of renewable sources, in
recent years Portfolio Theories have found a set of interesting applications. Portfolio Theory is nowadays a widely accepted method for the selection of efficient energy generation portfolios (Bhattacharya and Kojima, 2012; Kruyt et al., 2009; DeLlano-Paz et al. 2017), and there are already example of application of such methods also to the Italian electricity market (Cucchiella et al., 2017). 


By analyzing the impact of the sources' production fluctuations and temporal correlation patterns, it is shown that geographical allocation of different types of renewal energy sources can reduce the energy needs for balancing the power system. (Scala et al. 2019)
In that work a new model is proposed to investigate the power output of renewable energy sources by means of Gaussian fluctuations with tunable correlations, analyzing the impact of production fluctuations via Modern Portfolio Theory (MPT) analysis introduced by Markowitz (1959). 
Moreover a new framework is discussed, for the optimization of real non-Gaussian portfolio of renewable energy sources (both wind and solar) showing that and efficient configuration of renewable power plants is easily achievable through MPT.

That work is a starting point for this thesis, and here will be proposed an advanced tool for Portfolio Optimization Theory, drawing from Machine Learning techniques, and studying the performance of advanced models like GNN for this task.



### Actual Portfolio Optimization model

Financial Portfolio Optimization is a theory developed back to 1959 by Markowitz, based on the principle of asset diversification. The diversification of financial assets can lower the overall risk compared to the risk of the individual assets.
There is a systematic risk common to all the assets in the market which is not avoidable, and a unsystematic risk removable via diversification. 

Each financial asset is composed by three elements: (1) the expected return of the asset, (2) the risk of the asset (i.e. the standard deviation of the expected returns due to market fluctuations, also called volatility of the asset) and (3) the correlation between the assets composing the portfolio.
The risk is minimized according to a specific return as objective and an optimal portfolio is formed by assets negatively correlated. The objective target is not necessarily to maximize return, but also taking into account the risk associated with investments and the realization of portfolios that decrease the risk, maintaining the value of return.

We introduce an optimal portfolio for renewable energy sources by
considering the need to allocate a set of N renewable electric power plants on $i =1…N$ sites, let $w_i$ be the power generation size and $W_{i}$ the maximum possible power generation size on the i-th site.  To describe the sites’ energy production, we will assume that their unit production is described by a random variable $p_{i}$, with expected value $E(p_{i})=e_{i}$, and fluctuations characterized by their standard deviation $σ_{i}$, where $σ^2_i = E[(p_i - e_i)^2]$. 
The energy output will be $p_i w_i$ , and $\vec{w}$ is therefore the energy generating portfolio.

Notice that in the language of Portfolio Theories $σ_i$ is also called the risk associated with the i-th source. In our case, since we are considering electric generation, the produced power must exactly match the demand and that any fluctuation needs to be balanced by the grid and by the balancing market. Hence, also within this framework, variance is strictly related to the risk of diminished revenues or even economic losses because of fees paid in the balancing market.

Since we are dealing with renewable energy, similar weather conditions influences their production and their fluctuations if they are spatially close. 
This correlation is described by the covariance matrix $\symbfup{\sigma}$   
$$ \sigma_{ij} = E[(p_i - e_i)(p_j - e_j)]$$
The total production from renewable source will be a random variable  $P_R = ∑ w_i p_i$ with expected value $E_R$ and variance $\sigma_R$:

$$E_R = \Sigma_i w_i e_i$$
$$\sigma_R^2 = \Sigma_i \Sigma_j w_i w_j \sigma_{ij} $$
So we can consider the expected return $E_R$ as the production that one can obtain from the $N$ generators, and the volatility as the power fluctuations that the generators produce.
A portfolio can be considered optimal either when for a given level of generation it achieves the minimum value of the fluctuations, or when for a given level of risk (i.e. given the size of the fluctuations) it achieves the maximum level of generation.

The plants allocation will be naturally limited by a finite budget B, constraining the total investment cost to be $0 ≤ ∑ f_i(w_i) ≤ B$, where $f_i$ is the cost function associated to the i-th plant.

### Results for gaussian power plants
In the case of $N_s$ solar plants and $N_w$ wind plants, respectively with average production and risk $e_i^s, \sigma_i^s$ and $e_i^w, \sigma_i^w$ , with 
$$\vec{e} = \begin{pmatrix} 
\vec{e}^s \\
\vec{e}^w
 \end{pmatrix} 
 \qquad        
\vec{w} = \begin{pmatrix} 
\vec{w}^s \\
\vec{w}^w
 \end{pmatrix}
$$ and defining the correlation among solar and wind plants with $\rho_{ij}^{ss}, \rho_{ij}^{ww}$, and the cross correlations $\rho_{ij}^{sw}$ , the covariance matrix reads:
$$
C = 
\begin{bmatrix}
C^{SS} C^{SW} \\
C^{WS} C^{WW} 
\end{bmatrix}, \qquad
  C^{ww}_{ij} = \sigma_i^w \rho_{ij}^{ww}\sigma_j^w,\qquad C^{ss}_{ij} = \sigma_i^s \rho_{ij}^{ss}\sigma_j^s, \qquad C^{ws}_{ij} = \sigma_i^w \rho_{ij}^{ws}\sigma_j^s
$$
the total portfolio output is $E_R = \vec{w}\cdot \vec{e}$ , and the risk $\sigma_R = \vec{w}\cdot(C\vec{w})$
For simplicity, consider the case where $\rho^{ww} = \rho^{ss} = 0$ and $\rho_ij^{ws} = \rho \; \forall \; i,j$ 
the cross correlation becomes the outer product of risks times the constant value:  $C^{ws} = -\rho \; \vec{\sigma^w} \otimes \vec{\sigma^s}$  

Following the parameters in (Mureddu et al., 2015), and taking for instance a number of power plants $N_S = N_W = 5$ , the efficient portfolio boundaries for different $\rho$ values are shown in Fig.3.  It can be noticed that is possible to reach low risk value $\sigma_R$ even for $\rho > -1$ , and decreasing the correlation always decrease the risk of any portfolio, this also indicates that for an accurate choice of the correlation patterns the same amount of energy ER can be produced with less fluctuations.

### Results for renewable power plants
In this case study based on real solar and wind time series data (Mureddu et al., 2015), in Fig4 the portfolio boundaries are shown, in case of totally uncorrelated energy productions, which indicates a lower bound when taking into account wind plants, and an increased energy output that takes in account only solar plants, so that intermediate portfolio are a combination of solar and wind plants.

In general, we can expect that solar and wind power have negative correlations; however, we have checked that if we introduce synthetic negative correlations, the efficient frontier remains almost unchanged. This is due to the fact that without reallocation, wind farms are too small and do not produce fluctuations large enough to compensate solar energy's ones.

It is possible to conclude that the anti-correlation (often present among the fluctuations of different renewables) can be a suitable criterion for the optimal spacial and temporal allocation of renewable energy production in order to reduce the impact of fluctuations on the size of the electric power balancing market.




Ref.
Cucchiella, F., Gastaldi, M., Trosini, M., 2017. Investments and cleaner energy production: a portfolio analysis in the Italian electricity market. J. Clean. Prod. 142, 121–132.

Brouwer, Anne Sjoerd, Van Den Broek, Machteld, Seebregts, Ad, Faaij, André, 2014. Impacts of large-scale intermittent renewable energy sources on electricity systems, and how these can be modeled. Renew. Sustain. Energy Rev. 33, 443–466 (May 2014)

Facchini, Angelo, 2017. Distributed energy resources: planning for the future. Nat. Energy 2 (July), 17129.

Weitemeyer, Stefan, Kleinhans, David, Vogt, Thomas, Agert, Carsten, 2015. Integration of Sources in future power systems: the role of storage. Renew. Energy.

Bhattacharya, Anindya, Kojima, Satoshi, 2012. Power sector investment risk and renewable energy: a Japanese case study using portfolio risk optimization method. Energy Policy 40, 69–80

Kruyt, Bert, Van Vuuren, D.P., De Vries, H.J.M., Groenenberg, H., 2009. Indicators for energy security. Energy Policy 37, 2166–2181.

DeLlano-Paz, Fernando, Calvo-Silvosa, Anxo, Antelo, Susana Iglesias, Soares, Isabel. Energy planning and modern portfolio theory: a review. Renew. Sustain. Energy Rev. 77, 636–651 (March 2016).

Antonio Scala, Angelo Facchini, Umberto Perna, Riccardo Basosia, 2019. Portfolio analysis and geographical allocation of renewable sources: A stochastic approach

Markowitz, Harry M., 1959. Portfolio Selection: Efficient Diversification of Investments. Yale University Press, New York

Mureddu, Mario, Facchini, Angelo, Scala, Antonio, Caldarelli, Guido, Damiano, Alfonso, 2018. A complex network approach for the estimation of the energy demand of electric mobility. Sci. Rep. 8 (1) (268-).