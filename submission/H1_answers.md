# Task 1

The point of the `"invalid_pickup_dense_penalty"` ($s_{f}$ for 'score of failing') is to penalize the agent for picking up the wrong object.

The agent can get a score of at most 3*0.5 = 1.5 = $s_{t}$ (for 'total score') during the game if it achieves all objectives.

As a rough estimate (i.e. not thinking too hard about discount factors), the score of the dense penalty can be set so that a perfect game results in a score of zero:

$$
0 \approx  s_{t} - s_{f} \times n_{f} 
$$

where $n_f$ is the number of failed actions per run.

So the score can be set in terms of how many failed actions are reasonable for the model to make:

$$
s_{f} \approx \frac{s_t}{n_f}.
$$

When the failure score is initially set to $s_f = 0.2$, it means $n_f = 7.5$. So the agent only has a few shots at getting its actions right before its penalty is too high to get a positive score.

Let's say the agent should be allowed to make 100 (or 1000) failed actions per run. Then the failure score should be set to $s_f = 0.015$ (or $s_f = 0.0015$).

Check to see if learning proceeds any faster for those much-reduced failure scores.