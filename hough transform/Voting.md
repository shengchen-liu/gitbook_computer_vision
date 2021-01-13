# Voting

It is computationally infeasible to simply try every possible line given a set of edge pixels, in stead, we need to let the data tell us something.  **Voting** is a general technique where we let the features (edge pixels) vote for all the models with which the are compatible.

1. Cycle through features, each casting votes for model parameters.
2. Look for model parameters that receive a lot of votes.

## Voting - Why it works

1. Noise & clutter features will cast votes too, but typically their votes should be inconsistent with the majority of “good” features.
2. Ok if some features not observed, as model can span multiple fragments.