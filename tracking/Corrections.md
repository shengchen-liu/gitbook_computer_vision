# Corrections

Given a predicted value $$P(X_t|y_0, ..., y_{t-1})$$ and the current observation $$y_t$$, we want to compute $$P(X_t | y_0, ..., y_{t-1}, y_t)$$
$$
P(X_t | y_0, ..., y_{t-1}, y_t) \\
= \frac{P(y_t | X_t,y_0, ..., y_{t-1}) \cdot P(X_t | y_0, ..., y_{t-1})}{P(y_t|y_0, ..., y_{t-1})} \\
= \frac{P(y_t | X_t) \cdot P(X_t | y_0, ..., y_{t-1})}{P(y_t|y_0, ..., y_{t-1})} \\
= \frac{P(y_t | X_t) \cdot P(X_t | y_0, ..., y_{t-1})}{\int P(y_t|X_t)P(X_t | y_0, ..., y_{t-1})dX_t}
$$
As we'll see, the dominator is just a normalized factor that ensures the probabilities sum to 1, so we'll never need to worry about it explicitly.