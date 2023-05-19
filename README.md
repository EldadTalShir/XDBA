# XDBA - eXplainable Deep Behavior Analysis
This repository contains the code and datasets for the implementation of the method proposed in **Interpretable Prediction from Behavioral Data Using Convolutional Neural Networks**, authored by Eldad Tal-Shir, Alex Mintz and Michael Cohen.

The code is currently available as a Jupyter Notebook ([XDBA.ipynb](https://github.com/EldadTalShir/XDBA/blob/main/XDBA.ipynb)), with example usage replicating the analysis depicted in the manuscript (data folder contains the main dataset ([dataset.csv](https://github.com/EldadTalShir/XDBA/blob/main/data/dataset.csv)) and supplementary dataset ([featureframe.csv](https://github.com/EldadTalShir/XDBA/blob/main/data/featureframe.csv)) used in the paper). To render the notebook in full, paste the notebook's URL in [nbviewer](https://nbviewer.jupyter.org/).

## Method
XDBA preprocesses individual-level behavioral data by transforming it into computer-vision compatible visualizations, and interprets predictions on these data by extending gradient-based, propagation-based and permutation-based interpretability approaches to these data.

_Preprocessing:_ XDBA performs dimensionality reduction and clustering to associate each unique behavior with a Cartesian coordinate (and a cluster-based RGB code) (using the supplementary dataset, which contains a set of the unique behaviors exhibited across all individuals and these behaviors' embeddings/metafeatures/encodings). These coordinates are then used to visualize each individual's behaviors (from the main dataset) either as a sequence of images (sequential implementation) or as a single visualization (stationary implementation; where behaviors' opacities reflect the differences in the number of times the individual exhibited them). Data is used as input to a convolutional model (ConvLSTM in the sequential implementation).

_Interpretation:_ In the stationary implementation, local explanations are extracted using HiResCAM (and partitioning the resultant space among the K behaviors the individual exhibited) and global explanations are extracted through feature permutations (where the opacity of the permuted behavior is shuffled and its effect on class-specific accuracy computed). In the sequential implementation, local explanations are extracted using layerwise-relevance propagation, and global explanations are extracted using HiResCAM (as the convolutional backbone becomes a global feature extractor).

![XDBA Flowchart](https://github.com/EldadTalShir/XDBA/blob/main/misc/XDBA_flowchart.png?raw=true "Title")

## Citation
Eldad Tal-Shir, Alex Mintz, Michael Cohen
_Interpretable Prediction from Behavioral Data Using Convolutional Neural Networks_.
