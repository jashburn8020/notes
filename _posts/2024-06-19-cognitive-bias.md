---
layout: post
title: Cognitive Bias - Introduction
categories: psychology bias
published: true
plantuml: true
---
This is the first of a series of posts on _cognitive bias_. This post presents an overview. Subsequent posts will examine specific biases.

<plantuml data-caption="Cognitive biases overview" data-alt="Cognitive biases overview, biases in terms of addressing problems, and debiasing">
@startmindmap

<style>
mindmapDiagram {
  node {
      BackgroundColor white
      MaximumWidth 250
      FontName Quicksand
      Margin 5
  }
}
</style>

* Cognitive bias
  * Biases in terms of addressing problems
    * Too much information
    * Not enough meaning
    * Need to act fast
    * What should we remember
  * Debiasing
    * Incentives
    * Nudging
      * Default option
      * Social-proof
      * Salience of the desired option
    * Training
      * Recognition-primed decision
      * Interactive computer games
      * Reference class forecasting

@endmindmap
</plantuml>

_Note: The information on this page is mainly summarised from the references listed below._

## Cognitive Bias

* **Cognitive bias**: A systematic pattern of deviation from norm or rationality in judgment.
  * Individuals create their own "subjective reality" from their perception of the input.
  * May dictate their behaviour, may sometimes lead to perceptual distortion, inaccurate judgment, illogical interpretation, and irrationality.
* Some cognitive biases are adaptive.
  * May lead to more effective actions in a given context.
  * Enables faster decisions when timeliness is more valuable than accuracy.
* Other cognitive biases are a "by-product" of human processing limitations, resulting from:
  * a lack of appropriate mental mechanisms,
  * the impact of an individual's constitution and biological state, or
  * a limited capacity for information processing.
* Introduced by Amos Tversky and Daniel Kahneman in 1972.
  * Tversky and Kahneman explained human differences in judgment and decision-making in terms of _heuristics_.
* **Heuristics** involve mental shortcuts which provide swift estimates about the possibility of uncertain occurrences.
  * Simple for the brain to compute but sometimes introduce severe and systematic errors.

## List of Biases

* Biases in this section are categorised in terms of the general problems that they attempt to address. (Benson, 2016)
  * This categorisation is mainly for ease of remembering.
  * See also: [Cognitive Bias Codex](https://upload.wikimedia.org/wikipedia/commons/1/18/Cognitive_Bias_Codex_-_180%2B_biases%2C_designed_by_John_Manoogian_III_%28jm3%29.jpg)

**Problem 1: Too much information**

* So we skim and filter information and decide which few things are actually important.
  * But some of the information we filtered out is actually useful and important.

| Addressing the problem | Biases |
| --- | --- |
|  We notice things that are already primed in memory or repeated often | Availability heuristic, Attentional bias, Illusory truth effect, Mere exposure effect, Context effect, Cue-dependent forgetting, Mood-congruent memory bias, Frequency illusion, Baader-Meinhof Phenomenon, Empathy gap |
|  Bizarre, funny, visually-striking, or anthropomorphic things stick out more | Bizarreness effect, Humor effect, Von Restorff effect, Negativity bias, Publication bias, Omission bias |
|  We notice when something has changed | Anchoring, Contrast effect, Focusing effect, Framing effect, Weber–Fechner law, Distinction bias |
|  We are drawn to details that confirm our own existing beliefs | Confirmation bias, Congruence bias, Post-purchase rationalization, Choice-supportive bias, Selective perception, Observer-expectancy effect, Experimenter’s bias, Observer effect, Expectation bias, Ostrich effect, Subjective validation, Continued influence effect, Semmelweis reflex, Bucket error, Law of narrative gravity |
|  We notice flaws in others more easily than flaws in ourselves | Bias blind spot, Naïve cynicism, Naïve realism |

**Problem 2: Not enough meaning**

* So we need to fill in the gaps and map it all to our existing mental models.
  * But we sometimes imagine and make assumptions on the details, and construct meaning and stories that are not really there.

| Addressing the problem | Biases |
| --- | --- |
| We find stories and patterns even in sparse data | Confabulation, Clustering illusion, Insensitivity to sample size, Neglect of probability, Anecdotal fallacy, Illusion of validity, Masked man fallacy, Recency illusion, Gambler’s fallacy, Hot-hand fallacy, Illusory correlation, Pareidolia, Anthropomorphism |
| We fill in characteristics from stereotypes, generalities, and prior histories | Group attribution error, Ultimate attribution error, Stereotyping, Essentialism, Functional fixedness, Moral credential effect, Just-world hypothesis, Argument from fallacy, Authority bias, Automation bias, Bandwagon effect, Placebo effect |
| We can better imagine things and people we're familiar with or fond of than otherwise | Halo effect, In-group bias, Out-group homogeneity bias, Cross-race effect, Cheerleader effect, Well-traveled road effect, Not invented here, Reactive devaluation, Positivity effect |
| We simplify probabilities and numbers to make them easier to think about | Mental accounting, Normalcy bias, Appeal to probability fallacy, Base rate fallacy, Murphy’s law, Hofstadter’s law, Subadditivity effect, Survivorship bias, Zero sum bias, Denomination effect, Magic number 7±2, Swimmer’s body illusion, Money illusion, Conservatism |
| We think we know what others are thinking | Curse of knowledge, Illusion of transparency, Spotlight effect, Streetlight effect, Illusion of external agency, Illusion of asymmetric insight, Extrinsic incentive error |
| We project our current mindset and assumptions onto the past and future | Hindsight bias, Outcome bias, Moral luck, Declinism, Telescoping effect, Rosy retrospection, Impact bias, Pessimism bias, Planning fallacy, Time-saving bias, Pro-innovation bias, Projection bias, Restraint bias, Self-consistency bias |

**Problem 3: Need to act fast**

* So our brains make split-second decisions.
  * But some of the quick reactions and decisions we jump to are unfair, self-serving, and counter-productive.

| Addressing the problem | Biases |
| --- | --- |
| To act, we need to be confident in our ability to make an impact and to feel like what we do is important | Overconfidence effect, Egocentric bias, Optimism bias, Social desirability bias, Third-person effect, Forer effect, Barnum effect, Illusion of control, False consensus effect, Dunning-Kruger effect, Hard-easy effect, Illusory superiority, Lake Wobegone effect, Self-serving bias, Actor-observer bias, Fundamental attribution error, Defensive attribution hypothesis, Trait ascription bias, Effort justification, Risk compensation, Peltzman effect, Armchair fallacy |
| To stay focused, we favour the immediate, relatable thing in front of us over the delayed and distant | Hyperbolic discounting, Appeal to novelty, Identifiable victim effect |
| To get anything done, we're motivated to complete things that we've already invested time and energy in | Sunk cost fallacy, Irrational escalation, Escalation of commitment, Loss aversion, IKEA effect, Processing difficulty effect, Generation effect, Zero-risk bias, Disposition effect, Unit bias, Pseudocertainty effect, Endowment effect, Backfire effect |
| To avoid mistakes, we're motivated to preserve our autonomy and status in a group, and to avoid irreversible decisions | System justification, Reactance, Reverse psychology, Decoy effect, Social comparison bias, Status quo bias, Abilene paradox, Law of the instrument, Law of the hammer, Maslow’s hammer, Golden hammer, Chesterton’s fence, Hippo problem |
| We favour options that appear simple or that have more complete information over more complex, ambiguous options | Ambiguity bias, Information bias, Belief bias, Rhyme as reason effect, Bike-shedding effect, Law of Triviality, Delmore effect, Conjunction fallacy, Occam’s razor, Less-is-better effect, Sapir-Whorf-Korzybski hypothesis |

**Problem 4: What should we remember?**

* So we remember (what we believe to be) the most important and useful bits of new information.
  * But some of the things we remember just makes all of the above systems more biased and more damaging to our thought processes.

| Addressing the problem | Biases |
| --- | --- |
| We edit and reinforce some memories after the fact | Misattribution of memory, Source confusion, Cryptomnesia, False memory, Suggestibility, Spacing effect |
| We discard specifics to form generalities | Implicit associations, Implicit stereotypes, Stereotypical bias, Prejudice, Fading affect bias |
| We reduce events and lists to their key elements | Peak–end rule, Leveling and sharpening, Misinformation effect, Duration neglect, Serial recall effect, List-length effect, Modality effect, Memory inhibition, Part-list cueing effect, Primacy effect, Recency effect, Serial position effect, Suffix effect |
| We remember differently based on how they were experienced | Picture superiority effect, Levels of processing effect, Testing effect, Absent-mindedness, Next-in-line effect, Tip of the tongue phenomenon, Google effect, Self-relevance effect |

## Debiasing

* Cognitive bias causes _systematic errors_.
  * **Systematic errors**: Errors that are not determined by chance but are introduced by repeatable processes inherent to the system.
  * Cannot be compensated for using a "wisdom of the crowd" technique of averaging answers from several people.
* **Debiasing** is the reduction of biases in judgment and decision-making.
* 3 general approaches to debiasing: _changing incentives_, _nudging_, and _training_.

### Incentives

* Derived from economic theories suggesting that people act in their self-interest by seeking to maximise their utility over their lifetime.
* Many decision-making biases may occur simply because they are more costly to eliminate the biases than to ignore them - the necessary effort outweighs the benefit.
* When people generally have an idea of how a decision should be made, making people more accountable for their decisions (increasing incentives), for example, can increase the extent to which they invest cognitive resources in making decisions.
* Incentives can be calibrated to change preferences toward more beneficial behaviour, e.g., price cuts on healthy foods and soda taxes.
* Incentives can backfire when they are miscalibrated or are weaker than social norms that were preventing undesirable behaviour.
* Large incentives can also lead people to choke under pressure.

### Nudges

* Nudge theory is a concept that proposes adaptive designs of the decision environment (choice architecture) as ways to influence behaviour and decision-making.
  * Choice architecture: The different ways in which choices can be presented to decision makers, and the impact of that presentation on decision-making
* A nudge makes it more likely that an individual will make a particular choice or behave in a particular way, by altering the environment so that automatic cognitive processes are triggered to favour the desired outcome.
* Techniques:
  * **Default option**: The option that person automatically receives for doing nothing.
    * People are more likely to choose a particular option if it is the default option.
  * **Social-proof heuristic**: The tendency of people to look at the behaviour of others to help guide their own behaviour.
    * E.g., in e-commerce, showcasing positive testimonials from previous customers is found to be effective in encouraging potential customers to sign up.
  * **Salience of the desired option**: When people's attention is drawn toward a particular option (the more salient option), they will be more likely to choose it.
    * E.g., consumers purchased more fruit and healthy snack options when they were relocated next to the cash register.

### Training

* Decision makers can be effectively debiased through training in specific domains.
  * E.g., experts can be trained when decision-making entails recognising patterns and applying appropriate responses (_recognition-primed decision_) in domains such as firefighting, chess, and weather forecasting.
* Training using interactive computer games that provide players with personalised feedback, mitigating strategies, and practice, and instructional videos can result in long-term debiasing at a general level.
* Training in _reference class forecasting_ may also improve outcomes.
  * **Reference (or comparison) class forecasting**: A method of predicting the outcome of a planned action based on actual outcomes in a reference class of similar actions to that being forecast (i.e., similar past situations and their outcomes).

## References

* Wikipedia Contributors. (2024, June 17). _Cognitive bias_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Cognitive_bias>
* Benson, B. (2016, September). _Cognitive bias cheat sheet. An organized list of cognitive biases because thinking is hard_. Medium; Better Humans. <https://betterhumans.pub/cognitive-bias-cheat-sheet-55a472476b18>
* Wikipedia Contributors. (2023, November 27). _Debiasing_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Debiasing>
* Wikipedia Contributors. (2024, June 5). _Nudge theory_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Nudge_theory>
