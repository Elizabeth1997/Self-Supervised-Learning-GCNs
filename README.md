# Self-Supervised-Learning-GCNs
Thanks  [Typora](https://typora.io/) for providing a good experience of editing markdown file!

### Relevant work about self-supervised learning of GCNs

For each work I read already, I leave some short comments as summary. If you find something incorrect, welcome to let me know. (keep updating!)

- Deep Graph Infomax [[paper](https://arxiv.org/pdf/1809.10341.pdf)] [[code](https://github.com/PetarV-/DGI)] (ICLR 2019)

  1. maximize the mutual information beween patch and global representation
  2. binary classification task: positive sampling and negative sampling. positive: ***H' = f(A, X)***, global vector ***v*** could be obtained by mean pooling, ***W*** is learnt for measuring the similarity of the representation of each node ***h'*** and  ***v** ,* labeled by **1** (real); negative: ***H' = f'(A, X')**,* get ***X'*** by suffling ***X** ,* labeled by **0** (fake).

  









