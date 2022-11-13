[0486.pdf]

[[Communitydetection]]

We introduced a community-centric dual decoder to reconstruct network structures and node attributes separately in an unsupervised fashion,
showing the effectiveness of the novel decoding mechanism for generating links and attributes together over the commonly used methods for reconstructing links alone.

Community detection is in essence an unsupervised learning problem. 
Real-world networks are typically unique – the training data from one network can be hardly used adequately for another network


Conclusions:
This is the first approach extending GCN effectively to unsupervised community detection.  Using the Autoencoder framework, we focused on community identification rather than network embedding in the encoder; and used the most suitable mechanisms to reconstruct links and attributes separately.

Even though the new approach was designed for community detection, the underlying idea may be readily extended to GCN-based network embedding