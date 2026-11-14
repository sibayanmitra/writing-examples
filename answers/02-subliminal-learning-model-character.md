# 2. Subliminal Learning or Model Character Entanglements?

**Mentors:** Tagade, Mahbub, Zhou, Feng

## Q1. Do you consider post-training to suppress/hide the default model character or create it? (Max 200 words)

In my opinion post training suppress default the model behavior which is mostly created during pretraining. The thing that I feel is during pretraining the model does learn multiple probable behavior/personas and the circuits for those are made during pretraining itself and the model have a general idea of what to do when according to the distribution of the pretraining data. Now in post training the specific answer formats as well as personas are imposed on the model, and the weights change accordingly but that is not as robust as the pretraining one. I feel, If the personas were created during the post training, they are supposed to be more separate as entities and the common directions should not change similar behaviors. The emergent misalignment will also be less possible if the personas were made during the highly controlled post training and not the pretraining phase as that is the place where there is a blur between good and bad and those traits are deep rooted in the weights and when one is pulled the other similar ones comes along with it. I feel if we post trained the model to be bad by default there would be some phenomena called emergent alignment, i.e. when you train the model on a narrow good task it will do more good in other tasks, but as the model is trained to do good by default and be a good assistant as we know from the assistant axis paper, there is a ceiling on how much goodness we can extract from it.

## Q2. Do you expect verbalized evaluations (as captured by TruthfulQA etc.) to accurately predict agentic misalignment? Provide a succinct first-principles reason. (Max 200 words)

No, I do not expect verbalized evaluations to accurately predict agentic misalignment. the fact that the eval awareness phenomena exist is itself an hindrance for the verbalized evaluations. If the model is intelligent and knows it is being evaluated then that does not have any obligation to be aligned except following the safety tuning which can break. the main problem that i feel with verbalized evaluations is that their is no clear conflict of interest where most humans as well as models tend to be misaligned or tell lies. I derive this understanding from the alignment faking paper where they carefully construct the situation to be such that the model is forced to or pushed toward misalignment. without that kind of pressure its too naive to trust what the model says.

a link to one of my ongoing works
https://arxiv.org/abs/2610.22333v1
