# 6. Building a Robust Activation Monitor

**Mentor:** Davide Baldelli

## Question

Link one experiment you have run (repo, notebook, or a writing sample) and describe one design decision you made in it that you would now change, and why. (150 words)

## Answer

https://arxiv.org/abs/2610.22333v1

In this paper we tried to understand eval awareness in indic language settings.
we appended a set of cues with different level of evaluation framing to see if we can clearly attribute the change in refusal on harmful prompts between the cues based on how we made then. for example, in a cue we added monitoring only cue and in another we added cue that this response will be noted for safety evaluations.
now we tried to separate the cues such that they will separate monitoring from evaluation but what i would do now is to make a more granular and controlled approach in constricting the cues with proper justification on why we used the exact words of the cue and try to avoid confounds more carefully that what we currently did. Each cue may have other factors than just the one which we are considering and without proper justification and understanding on why our method is good to separate eval awareness , the claim is thin. maybe with saes if we had checked what feature the cue have or something like that, then i think that would be a better approach.
