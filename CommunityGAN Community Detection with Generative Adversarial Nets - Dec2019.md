[1901.06631v3.pdf]
[[Communitydetection]]
[[GAN]]



that jointly solves overlapping community detection and graph representation learning
unlike the embedding of conventional graph representation learning algorithms where the vector entry values have no specific meanings, the embedding of CommunityGAN indicates the membership strength of vertices to communities.

However, there still exists many limitations for the application
of such embedding in overlapping community detection problems because of the dense overlapping of communities
To detect communities, a straightforward way is to run some clustering algorithms in the vector space. However, in some real-world datasets, one vertex may belong to tens of communities simultaneously [29, 30], while most clustering algorithms cannot handle such dense overlapping. some researchers try to perform the community detection and network embedding simultaneously in a unified framework [3, 27] but still fail to solve the dense overlapping problem.

Moreover, in recent years, motifs have been proved as essential
features in community detection tasks [11].

