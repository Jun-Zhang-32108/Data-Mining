<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# Data-Mining
Data Mining Project

Author: Jun Zhang \<jun.1.zhang@aalto.fi>, Zhiheng Qian \<zhiheng.qian@aalto.fi>

The objective of this project is to design and implement a algorithm to partition a graph into communities. We use pre-processed graphs from the [Stanford Network Analysis Project](http://snap.stanford.edu/data/index.html). The preprocessed datasets are in the folder "\graph_processed". Given an undirected graph $G = (V, E)$ and an integer $k > 1$, we need to partition the set of vertices $V$ into $k$ communities $(V_1,...,V_k)$, so that$\cup_{i=1}^{k}V_i = V$ and $V_i \cap V_j = \emptyset$ for all $i\neq j$. We want the communities $V_1, . . . , V_k$ to be as much separated from each other as possible. We also want that the communities have roughly equal size. Thus, we will evaluate the goodness of a partition $V_1,...,V_k$ using the objective function
$$\phi (V_1,...,V_k)=\sum_{i=1}^{k} \frac{|E(V_i,\overline{V_i})|}{|V_i|}$$
where for $S, T \subseteq V$ with $S \cap T = \phi$ we define $E(S, T)$ to be the set of edges of $G$ with one endpoint in $S$ and the other endpoint in $T$, i.e., $E(S,T) = {(u,v) \in E | u \in S\; and\; v \in T}$, and we also define $\overline{V_i} = V \backslash V_i$ .

The baseline algorithm is spectral clustering with RatioCut. We also explored a couple of ways to optimize the general spectral clustering and do some comparisons. To see the complete comparsons in detail, please refer to the file "DataMining_Project.pdf". 

To run the program, please use the following command:
        
        python3 graph_partition.py [filename]

If you want to save the eigenvectors, please add the parameter '--save', i.e:
        
        python3 graph_partition.py [filename] --save

The result will be save in the folder "\result". Some useful statistics will be saved in the foler "\stat". Notice that some datasets such as *soc-Epinions1*, *web-NotreDame*, *roadNet-CA* are too big to be ran on the PC. In that case, please use powerful server instead. 
