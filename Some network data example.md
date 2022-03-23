(https://arxiv.org/pdf/cond-mat/0106096.pdf)
https://ucilnica.fri.uni-lj.si/pluginfile.php/1147/course/section/4652/book_chapter_4.pdf

As a physicst I need to know the observables with which I am working on. 
They are not physical quantities, and they are not typical data I used to work with as a Machine Learning engineer such as speech utterances, images, or text data.
Networks describe several objects, and every network has property such as degree distribution, clustering coefficient, and many other...

- World-Wide Web
	Is a directed network of webpages and URLs, which size goes over tenth billions of nodes (pages) according to search engines crawlers (https://www.worldwidewebsize.com/), that build a map of the World Wide Web. 
	In 1998 there were reasons to believe that the WWW could be well approximated by a random network.  Indeed, in a random network highly connected nodes, or hubs, are effectively forbidden. In contrast it has numerous small-degree nodes and a few hubs.  **hubs are not unique to the Web, but we encounter them in most real networks**.
	We therefore explore the degree distribution of real networks, which allows us to uncover and characterize **scale-free network** (power law distribution)
	The ww shows power law degree distribution, small world property
- Internet
	Is the network of physical connection between computer devices, power law degree distribution and small world
- Movie actor collaboration network
	The Internet Movie Database contains all movies and their casts since the 1890’s. 
	Nodes are the actors, and two nodes have a common edge if the corresponding actors have acted in a movie together,  power law degree distribution
- Science collaboration graph
	The nodes are the scientists and two nodes are connected if the two scientists have written an article together, power law degree distribution
- The web of human sexual contacts
	Study of the spread of sexual diseases, in a web of 2800 individuals, power law degree distribution
- Cellular networks
	the metabolism of 43 organisms representing all three domains of life, reconstructing them in networks in which the nodes are the substrates (such as ATP, ADP, $H_2O$) and the edges represent the predominantly directed chemical reactions in which these substrates can participate. All organisms networks have shown power law degree distribution.
	Another important network characterizing the cell describes protein-protein interactions, where the nodes are proteins and they are connected if it has been experimentally demonstrated that they bind together. also power law degree distribution.
- Protein folding
	During folding a protein takes up consecutive conformations. Representing with a node each distinct state, two conformations are linked if they can be obtained from each other by an elementary move. Some network have small world property, while degree distribution observed is consitent with a gaussian
- Ecological networks
	The food web is an undirected network where the nodes are species and the edges represent predator-prey relationships between them. The greatest size is only $N=186$ nodes but there are hint for the existence of hubs, that is a feature of scale-free networks.
- Long distance Phone-call network
	In this network the nodes are phone numbers and every completed phone call is an edge, directed from the caller to the receiver. Power law distribution
-  Citation networks
	A rather complex network is formed by the citation patterns of scientific publications, the nodes standing for published articles and a directed edge representing a reference to a previously published article.  The probability that a paper is cited k times follows a power-law with exponent $γ_{cite} = 3$, indicating that the incoming degree distribution of the citation network follows a power-law. (also the outcoming citation)
- Networks in linguistics
	A network where words are nodes and links appear wherever two words appear next or one word apart from each other in sentences, and exhibit two regimes power law degree distribution.
	Another network of words connected if they are synonyms show higher clustering coefficient and single exponent power law.
	These results indicate that in many respects the language also forms a complex network with organizing principles not so different from the other examples.
- Power grid networks and neural networks also have a power law distribution


[[Organization Network]]
[[NFT trade network]]

(applications)
[[Weather network data]]

- (and all other examples from stanford datasets and so on.. .[[Datasets]])

 - It is a fact that no matter what network property we are interested in, from communities to spreading processes, the network’s degree distribution remains the most important feature to check.
- In summary, the scale-free name captures the lack of an internal scale, a consequence of the fact that nodes with widely different degrees coexist in the same network. 
- This feature distinguishes scale-free networks from lattices, in which all nodes have exactly the same degree (σ = 0), or from random networks, whose degrees vary in a narrow range (σ = ⟨k⟩1/2). **This divergence is the origin of some of the most intriguing properties of scale-free networks, from their robustness to random failures to the anomalous spread of viruses.** 


![[Schermata da 2022-02-22 18-18-20.png]]
- The diversity of the systems that share the scale-free property is remarkable. It is this diversity that prompts us to call the scale-free property a universal network characteristic.