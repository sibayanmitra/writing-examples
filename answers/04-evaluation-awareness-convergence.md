# 4. Evaluation Awareness Convergence

**Mentor:** Netzer Epstein

## Q1. (~250 words) Propose a way to measure evaluation awareness that is DIFFERENT from the instruments this project already covers. Sketch how it would work: what signal you'd read, how you'd turn it into a per-transcript score, and how you'd validate that it's actually tracking eval awareness rather than something correlated with it.

we can use a set of cues based on evaluation realism on the same base item. the cues will be carefully constructed to study the eval awareness phenomena better with changing small factors one at a time, although they will not be a good way to test the eval awareness in deployment but they can help in understanding what text and its representation is actually contributing to the change in behavior during eval awareness.
I actually did something like this in a paper I was working on which extends the eval awareness phenomena to multilingual settings.
the setup basically is that we made a set of cues, that we appended before each prompt, gradually increasing the signal that this is a evaluation. the prompts were taken from a harmful dataset of and we used llm judges to get the models refusal percentage on the harmful prompts and expected to see more and more refusal as the evaluation framing increases.
the base item had nothing appended to it .  then we had the neutral item which had logging for monitoring written. after that we had an explicit evaluation written and after that we had explicit monitoring for safety evaluation and alignment.
now after appending each clue and getting the refusal percentage on 100 harmful prompts we can have an idea, that which kind of indication raised the refusal behavior by how many percentage points. We used refusal rate difference between evaluation framed cue and monitoring cues on the same base item to get a score of  effect of eval awareness per base prompt.
as control we used benign prompts and added the set of cues one by one to see if refusal increases selectively for harmful prompts and found that in 2/4 models it is selective. this makes sure that it is evaluation awareness and not related emotional things like caution that is actually increasing the refusal
while steering we used random magnitude matched vectors as control.

## Q2. (~150 words) Pick two of the suggested instruments and give one concrete transcript or scenario where you'd expect them to DISAGREE about how "eval-aware" the model is. Say why.

we also tried to steer the models with the evaluation direction (mean activations from evaluation cue - mean activation from the monitoring cue) and got results in Hermes llama 8b and 70b models as well as Aya expanse 8b . although we did not get the steering result strongly on llama 8b instruct and other models like Quen 2.5 7b and 14b instruct and did not get resulting change in behavior. although when we tried to see if the evaluation direction exists in the residual stream, we found it with high auroc.
also in a experiment we saw a divergence between the verbalized eval awareness ( i.e. number of times it hints in its cot that its being evaluated) and change in behavior due to eval awareness. i think the main thing that makes the methods diverge is that different things decide whether the model will change its behavior and whether eval awareness exists in its residual stream. the answer or change of behavior is dependent much more on post training than the internal representations are dependent on post training. thus, even if we find the existence of eval awareness it is not garneted that it will move the needle at the time of inference.

## Q3. (Optional) Link one short writing or code sample.

below I am attaching the abstract of the current paper i am working on, other people are also working on it with me. the draft is not final, and the values needs to go through audit before we can confidently claim all of it.

> Large language models often act more cautiously when they sense they are being tested. This makes them look safer during a safety evaluation than they are in everyday use, in a phenomenon called evaluation awareness. A model that senses itself being evaluated will respond cautiously, leading to an increased refusal rate compared to what it will actually exhibit in real use. Existing work has focused on analysis of this behavior in English, so it is unknown whether it exists in other languages and scripts. Indic languages are used by more than a billion people, yet the phenomenon remains almost entirely unstudied in them. We study evaluation awareness in five Indic languages alongside English. We conducted a controlled behavioral study using a set of system prompts. This set of cues varies whether the model is told its responses are being monitored and whether that monitoring is framed as a safety evaluation. We find that evaluation awareness appears in all six languages, including the lowest-resource ones. For Qwen3-32B, this rises from +22 points in English to +27 in Telugu and +39 in Tamil. These findings suggest that safety evaluations conducted in lower-resource languages face the same risk as those conducted in English.

for full paper
https://arxiv.org/abs/2610.22333v1
