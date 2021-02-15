# Prediction

Given: $$P(X_{t-1} | y_0, ..., y_{t-1})$$

Guess: $$P(X_t | y_0, .., y_{t-1})$$

To solve that, we apply the law of total probability and marginalization.
$$
P(X_t | y_0, .., y_{t-1}) \\
= \int P(X_t, X_{t-1} | y_0,..., y_{t-1})dX_{t-1} \\
= \int P(X_t| X_{t-1} | y_0,..., y_{t-1}) P(X_{t-1}|y_0, ..., y_{t-1})dX_{t-1} \\
= \int P(X_t | X_{t-1}) P(X_{t-1}|y_0, ..., y_{t-1})dX_{t-1}
$$
To explain it, the likelihood of being at a particular spot ($$X_t$$) depends on the probability of being at that spot given that we were at some previous spot weighted by the probability of that previous spot actually happening (our corrected estimate for $$X_{t-1}$$).  Summing over all of the possible "previous spots" (the integral over $$X_{t-1}$$) gives us the marginalized distribution of $$X_t$$