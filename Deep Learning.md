# Deep Learning

### Transformer

- Milestone: **Attention is all you need**, NIPS, 2017. 
- Review: **Transformers in Time Series: A Survey**, arXiv, 2022.
- Advantages: 
  - utilize the positional encoding added in the input embeddings to model the sequence information
  - self-attention module: a fully connected layer with the weights that are dynamically generated based on the pairwise similarity of input patterns. It shares the same maximum path length as fully connected layers, but with much less number of parameters, making it suitable for modeling long-term dependencies.
- Drawbacks:
  - computational bottleneck for long sequences:  a time and memory complexity of O(L^2) (L is the input time series length)
- Modifications:
  - learnable positional encoding: **A transformer-based framework for multivariate time series representation learning**, KDD, 2021
  - LogTrans: **Enhancing the locality and breaking the memory bottleneck of transformer on time series forecasting**, NIPS, 2019
    - propose convolutional self-attention by employing causal convolutions to generate queries and keys in the self-attention layer.
    - explicitly introduce a sparsity bias into the attention mechanism to reduce computational complexity
    - complexity: Time O(L log L), Memory O(L^2)

  - Informer: **Informer: Beyond efficient transformer for long sequence time series forecasting**, AAAI, 2021
    - encode timestamps
    - explore the low-rank property of self-attention matrix to speed up the computation
    - design a generative style decoder to produce long term forecasting directly and thus avoids accumulative error in using one forward step prediction for long term forecasting.
    - complexity: Time O(L log L), Memory O(L log L)
  - Auoformer: **Autoformer: Decomposition transformers with auto-correlation for long-term series forecasting**, NIPS, 2021
    - encode timestamps
    - devise a simple seasonal trend decomposition architecture with an auto-correlation mechanism working as an attention module. 
    - measure the time-delay similarity between inputs signal and aggregate the top-k similar sub-series to produce the output with a reduced complexity of O(Llog L).
- Applications: 
  - NLP: **Bert: Pre-training of deep bidirectional transformers for language understanding**, arXiv, 2018
  - CV: **An image is worth 16x16 words: Transformers for image recognition at scale**, arXiv, 2020. 
  - speech processing: **Speech-transformer: a no-recurrence sequence-to-sequence model for speech recognition**, ICASSP, 2018.



