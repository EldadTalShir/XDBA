# FAQ
## Reproducibility
Seed management has been introduced in version 1.0 of XDBA wherever possible.
However, use of different platforms and/or processing units than those used in our analysis may obtain different results (see PyTorch's documentation on [reproducibility](https://pytorch.org/docs/stable/notes/randomness.html)).
Still, most failed reproductions of XDBA's example code result from different dimensionality-reduction outputs, which affect the visualization of the data (and therefore training of the model(s)).
To overcome this, load the data_coordinates.pkl file for the implementation whose run/model you are unable to reproduce ([available here](https://github.com/EldadTalShir/XDBA/tree/main/misc)) by adding the following code to the 'preprocessing.project' function immediately after the 'explainer_dependencies' folder is created:
```Python
with open('PATH_TO_DATA_COORDINATES_FILE','rb') as dest:
  item_loci = pickle.load(dest)
```
Then re-run the implementation.

## Zero Behaviors
XDBA has been developed to predict from individual-level behavioral data.
Therefore, the method may not work for entries where no behaviors are exhibited (i.e., their behavioral vectors are empty).
We recommend dropping these observations, but you may try appending a 'zero_behaviors' item to their empty behavior tuples (make sure to embed/encode this non-behavior as well).
