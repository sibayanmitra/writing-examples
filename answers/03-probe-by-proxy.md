# 3. Probe by Proxy

**Mentor:** Matt Levinson

## Question

Review https://arxiv.org/abs/2502.03407. Design an experiment to test whether deception can be detected via an activation probe on activations from an open-weight proxy model. Include discussion of how/why your design would eliminate or reduce confounding. Don't go silly, but bias towards using more compute and robustly answering the question versus being parsimonious.

## Answer

So first you would train the probe, we need specific and wide-ranging data on deception.
We can generate many types of deception-based paragraphs by some model and also generate similar paragraphs but without deception. we can use multiple types of models for both kind of generation to remove any bias due to a certain model's pattern. We can use the testing pattern of apollo and test of something slightly out of distribution to see it the probe really generalizes.
Then we have the activation from both the cases and subtract the mean and get a vector. now we can compare token wise cosign similarity with this vector to get a deception similarity. this is the difference of means probe as much as I know.
we can also use a logistic regression probe.   If the paragraphs are, say 1000 tokens, we can start taking the activations from 50 tokens onwards to remove the setup part where the deception is still not developed, like anthropic did in their emotions paper, but that's not a must in my opinion.
we can probe starting from say, layer 14 to end of a 80-layer model to not get into the surface features.

now for the baseline
1. we can have a llm as a judge with the same proxy model or other stronger models.
2. saving the activations scores for the tokens and ablate the highest weighted ones with similar in distribution tokens swap or mean ablation to see if it's just word dependent
3. we can also use a open model at first and use another open model proxy on its cot, and compare the probes success on the open models cot with respect to the proxies cot to have an idea of the differences and upper limits.

controls:
1. we can also change the labels of the probes training data as a control.
2. we can read a bit or literature to understand the geometric representation of deception and use similar but different things like lie, or violence, conspiracy or similar and check how good our probe works on them when we train it on deception specifically.
3. we can orthogonalize our deception direction from the similar directions and then see what happens.

this is all i can come up till now, will be happy to work.
below is a sample of a paper that is still in progress
https://arxiv.org/abs/2610.22333v1
