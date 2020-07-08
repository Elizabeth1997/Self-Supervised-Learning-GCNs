# Self-Supervised-Learning-GCNs
Thanks  [Typora](https://typora.io/) for providing a good experience of editing markdown file!

### Relevant work in 2019 and 2020 about self-supervised learning of GCNs

For each work I read already, I leave some short comments as summary. If you find something incorrect, welcome to let me know. (keep updating!)

- [1] **Deep Graph Infomax (DGI)** [[paper](https://arxiv.org/pdf/1809.10341.pdf)] [[code](https://github.com/PetarV-/DGI)] (ICLR 2019)

  1. maximize the mutual information beween patch and global representation
  2. binary classification task: positive sampling and negative sampling. positive: ***H' = f(A, X)***, global vector ***v*** could be obtained by mean pooling, ***W*** is learnt for measuring the similarity of the representation of each node ***h'*** and  ***v** ,* labeled by **1** (real); negative: ***H' = f'(A, X')**,* get ***X'*** by suffling ***X** ,* labeled by **0** (fake).

- [2] **Self-supervised Learning on Graphs: Deep Insights and New Directions (SelfTask-GNN)** [[paper](https://arxiv.org/pdf/2006.10141.pdf)] [[code](https://github.com/ChandlerBang/SelfTask-GNN)]

  Basic pretext tasks

  1. **structure information** 

     - local structure information
       - **Node property**
         - regression task: predict the degree of each node
       - **Edge mask**
         - binary classification task: similar to random remove edges (RRL) and do link prediction in [[3](https://arxiv.org/pdf/2003.01604.pdf)]
     - global structure information
       - **Pairwise distance**
         - similar to global context prediction in [[4](https://arxiv.org/pdf/2003.01604.pdf)]
         - sample a certain number of nodes during each epoch; use distance categoroies designed according to shortest path between two nodes as the prediction target  (there are other ways to measure pairwise distance)
         - multi-class prediction task
       - **Distance2Cluster**
         - partition the graph into *k* clusters using METIS algorithm
         - represent each cluster using the node with the highest degree
         - form the target by calculating *k* distances of each node to each cluster
         - regression task

  2. **attribute information**

     - Attribute mask
       - similar to node feature masking (RCF) in [[3](https://arxiv.org/pdf/2003.01604.pdf)]
       - randomly mask out node features (set equal to zero); reconstruct original node features
       - regression task
     - PairwiseAttrSim
       - make sure the learnt representations of two nodes that have similar attributes originally are close as well
       - use *cosine* to measure the attributes similarity
       - top-k and bottom-k similarity
       - regression task

     Two ways to do SSL

     1. two stages: pretraining & finetuning (P&F)
     2. joint training (incoroprate SSL to downstream task, e.g. node property classification), outperforms

     **Advanced Pretext Tasks**: leverage the task specific information of unlabeled nodes

     **SelfTask**

     - ContextLabel: label distribution based on KNN
     - EnsembleLabel: plus correction phase, produce corrected labels

- [3] **Self-supervised Training of Graph Convolutional Networks** [[paper](https://arxiv.org/pdf/2006.02380.pdf)]

  Two pretext tasks proposed

  1. Randomly Removing Links (RRL), randomly remove some edges and then do link prediction
  2. Randomly Covering Features (RCF), randomly mask out some features and then be trained to do link prediction

- [4] **Self-Supervised Graph Representation Learning via Global Context Prediction** [[paper](https://arxiv.org/pdf/2003.01604.pdf)]

  Regression task: predict the count of hops between two nodes

- [5] **Multi-Stage Self-Supervised Learning for Graph Convolutional Networks on Graphs with Few Labeled Nodes** [[paper](https://zhouchenlin.github.io/Publications/2020-AAAI-M3S.pdf)]

  1. use few labeled data to train the model
  2. get the updated node features
  3. apply  k-means clustering
  4. classes alignmnet: assign each cluster to a specific class
  5. select **t** nodes from each class with the highest confidence, label them with corresponding classes they belong to
  6. add these newly labeled nodes to the training data
  7. repeat 1-6 steps several times
  8.  obtain the final accuracy









