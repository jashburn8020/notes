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
  * Dual process theory
    * Type 1: Fast, intuitive
    * Type 2: Slower, methodical
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
    * Slowing down
      * Timeout intervention
    * Metacognition
      * Learning process
      * Limitations of memory
      * Perspectives
      * Self-critique
      * Strategies
    * Cognitive forcing strategies
      * Training in metacognition
      * Knowledge of cognitive errors
      * Identify error scenarios
      * Select strategy
      * Avoid or minimise error
    * Checklists
    * Dialectical bootstrapping
      * Dialectical estimate

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

### Dual Process Theory

* Considers our thought process as a type 1 or type 2 process, with each pathway characterised by their own important attributes.
* **Type 1 thinking**:
  * fast, intuitive
  * pattern recognition driven method of problem solving
  * low cognitive burden on the user
  * allows one to make fast and accurate decisions rapidly.
* **Type 2 thinking**:
  * slower, more methodical and thoughtful
  * higher cognitive strain on the user
  * allows them to appraise data more critically and look beyond patterns
  * may potentially be more suitable for complex problem solving.
* Current opinion among psychologists is that we spend about 95% of our time in type 1 thinking.
* Cognitive bias and resulting error is thought to be more likely to occur during type 1 processing.
* Not all biases originate in type 1 processing, but when bias does occur it is thought this can only be dealt with by activating type 2 processing.
* An appropriate balance of type 1 and type 2 processes is required for optimal decision-making performance.
* Situations of stress, fatigue, sleep deprivation and cognitive overload may predispose to error and allow cognitive bias to emerge. (O'Sullivan & Schofield, 2018)

## List of Biases

* Biases in this section are categorised in terms of the general problems that they attempt to address. (Benson, 2016)
  * This categorisation is mainly for ease of remembering.
  * See also: [Cognitive Bias Codex](https://upload.wikimedia.org/wikipedia/commons/1/18/Cognitive_Bias_Codex_-_180%2B_biases%2C_designed_by_John_Manoogian_III_%28jm3%29.jpg)

### Problem 1: Too much information

* We skim and filter information and decide which few things are actually important.
  * But some of the information we filtered out is actually useful and important.

| Addressing the problem | Biases |
| --- | --- |
|  We notice things that are already primed in memory or repeated often | [Availability heuristic]({{ site.baseurl }}{% post_url 2024-06-20-availability-heuristic %}), Attentional bias, Illusory truth effect, Mere exposure effect, Context effect, Cue-dependent forgetting, Mood-congruent memory bias, Frequency illusion, Baader-Meinhof Phenomenon, Empathy gap |
|  Bizarre, funny, visually-striking, or anthropomorphic things stick out more | Bizarreness effect, Humor effect, Von Restorff effect, Negativity bias, Publication bias, Omission bias |
|  We notice when something has changed | Anchoring, Contrast effect, Focusing effect, Framing effect, Weber–Fechner law, Distinction bias |
|  We are drawn to details that confirm our own existing beliefs | [Confirmation bias]({{ site.baseurl }}{% post_url 2024-07-17-confirmation-bias %}), Congruence bias, Post-purchase rationalization, Choice-supportive bias, Selective perception, Observer-expectancy effect, Experimenter's bias, Observer effect, Expectation bias, Ostrich effect, Subjective validation, Continued influence effect, Semmelweis reflex, Bucket error, Law of narrative gravity |
|  We notice flaws in others more easily than flaws in ourselves | Bias blind spot, Naïve cynicism, Naïve realism |

### Problem 2: Not enough meaning

* We need to fill in the gaps and map it all to our existing mental models.
  * But we sometimes imagine and make assumptions on the details, and construct meaning and stories that are not really there.

| Addressing the problem | Biases |
| --- | --- |
| We find stories and patterns even in sparse data | Confabulation, Clustering illusion, Insensitivity to sample size, Neglect of probability, Anecdotal fallacy, Illusion of validity, Masked man fallacy, Recency illusion, Gambler's fallacy, Hot-hand fallacy, Illusory correlation, Pareidolia, Anthropomorphism |
| We fill in characteristics from stereotypes, generalities, and prior histories | Group attribution error, Ultimate attribution error, Stereotyping, Essentialism, Functional fixedness, Moral credential effect, Just-world hypothesis, Argument from fallacy, Authority bias, Automation bias, Bandwagon effect, Placebo effect |
| We can better imagine things and people we're familiar with or fond of than otherwise | Halo effect, In-group bias, Out-group homogeneity bias, Cross-race effect, Cheerleader effect, Well-traveled road effect, Not invented here, Reactive devaluation, Positivity effect |
| We simplify probabilities and numbers to make them easier to think about | Mental accounting, Normalcy bias, Appeal to probability fallacy, Base rate fallacy, Murphy's law, Hofstadter's law, Subadditivity effect, Survivorship bias, Zero sum bias, Denomination effect, Magic number 7±2, Swimmer's body illusion, Money illusion, Conservatism |
| We think we know what others are thinking | Curse of knowledge, Illusion of transparency, Spotlight effect, Streetlight effect, Illusion of external agency, Illusion of asymmetric insight, Extrinsic incentive error |
| We project our current mindset and assumptions onto the past and future | Hindsight bias, Outcome bias, Moral luck, Declinism, Telescoping effect, Rosy retrospection, Impact bias, Pessimism bias, Planning fallacy, Time-saving bias, Pro-innovation bias, Projection bias, Restraint bias, Self-consistency bias |

### Problem 3: Need to act fast

* Our brains make split-second decisions.
  * But some of the quick reactions and decisions we jump to are unfair, self-serving, and counter-productive.

| Addressing the problem | Biases |
| --- | --- |
| To act, we need to be confident in our ability to make an impact and to feel like what we do is important | Overconfidence effect, Egocentric bias, Optimism bias, Social desirability bias, Third-person effect, Forer effect, Barnum effect, Illusion of control, False consensus effect, Dunning-Kruger effect, Hard-easy effect, Illusory superiority, Lake Wobegone effect, Self-serving bias, Actor-observer bias, Fundamental attribution error, Defensive attribution hypothesis, Trait ascription bias, Effort justification, Risk compensation, Peltzman effect, Armchair fallacy |
| To stay focused, we favour the immediate, relatable thing in front of us over the delayed and distant | Hyperbolic discounting, Appeal to novelty, Identifiable victim effect |
| To get anything done, we're motivated to complete things that we've already invested time and energy in | Sunk cost fallacy, Irrational escalation, Escalation of commitment, Loss aversion, IKEA effect, Processing difficulty effect, Generation effect, Zero-risk bias, Disposition effect, Unit bias, Pseudocertainty effect, Endowment effect, Backfire effect |
| To avoid mistakes, we're motivated to preserve our autonomy and status in a group, and to avoid irreversible decisions | System justification, Reactance, Reverse psychology, Decoy effect, Social comparison bias, Status quo bias, Abilene paradox, Law of the instrument, Law of the hammer, Maslow's hammer, Golden hammer, Chesterton's fence, Hippo problem |
| We favour options that appear simple or that have more complete information over more complex, ambiguous options | Ambiguity bias, Information bias, Belief bias, Rhyme as reason effect, Bike-shedding effect, Law of Triviality, Delmore effect, Conjunction fallacy, Occam's razor, Less-is-better effect, Sapir-Whorf-Korzybski hypothesis |

### Problem 4: What should we remember?

* We remember (what we believe to be) the most important and useful bits of new information.
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
  * **Recognition-primed decision**: Experts can be trained when decision-making entails recognising patterns and applying appropriate responses in domains such as firefighting, chess, and weather forecasting.
* Training using interactive computer games that provide players with personalised feedback, mitigating strategies, and practice, and instructional videos can result in long-term debiasing at a general level.
* Training in _reference class forecasting_ may also improve outcomes.
  * **Reference (or comparison) class forecasting**: A method of predicting the outcome of a planned action based on actual outcomes in a reference class of similar actions to that being forecast (i.e., similar past situations and their outcomes).
* However, with bias-specific teaching, while it may improve learners' awareness of bias, interventional studies of teaching sessions demonstrated effect sizes that were often insignificant or small. (Niu et al., 2013)

### Slowing Down

* Slowing down during cognition could allow the decision-maker to transition into 'type 2' thinking, reflect more critically on data and ultimately make fewer errors. (O'Sullivan & Schofield, 2018)
* From a trial on antibiotic-prescribing:
  * A **timeout intervention** was added to physicians' workflow in the form of an electronic template note to be filled in.
    * The template note walked through the reasoning for continuing antibiotics at day 3.
    * Forced physicians to slow down and consider 'why' and 'how' antibiotics were prescribed.
  * 2 important themes that emerged from the qualitative analysis were respondents' comments that the intervention:
    * forced their attention to important questions ("it reminds us to think about it"), and
    * induced slow and deliberative reasoning ("it makes you think twice").
  * Requiring template completion to continue antibiotics nudged clinicians to re-assess the appropriateness of specified antibiotics. (Jones et al., 2017)

### Metacognition

* Metacognition: Thinking about thinking.
* An individual's ability to stand apart from their own thinking, to observe it, and to recognise opportunities for using interventional thinking strategies.
* Characterised by a number of core features:
  * Awareness of the **learning process** itself.
    * Was the piece of information important enough to commit to memory and was appropriate attention paid to it?
    * Has enough time been spent acquiring a specific piece of knowledge?
    * Has it been rehearsed adequately?
    * Can it be recalled appropriately, especially under conditions of stress?
  * Recognition of **limitations of memory**.
    * Awareness of strategies to cope with any failings that have manifested in the past and that might appear in the future.
    * Use of cognitive aids that lessen the burden on memory.
  * Ability to appreciate **perspectives**.
    * See the broader range of possibilities than the problem initially appears to offer (i.e., the ability to step back from the immediate problem at hand).
    * Recognise incongruity, ambiguity, atypical presentations, and instances when data are not fitting together.
  * Capacity for **self-critique**.
    * Recognise when they are not performing well and are better able to criticise themselves realistically.
    * Able to reliably self-monitor.
  * Ability to select **strategies**.
    * Actively select a strategy to deal with problems in decision-making.
    * Deliberate cognitive intervention in the thinking process.
* Through the process of metacognition, people can develop cognitive forcing strategies to abort latent cognitive errors. (Croskerry, 2003)

### Cognitive Forcing Strategies

* Cognitive forcing strategies are a specific debiasing technique that introduces self-monitoring of decision-making.
  * Designed to prevent decision-makers from pursuing a pattern-recognition path that typically will lead to error.
  * Rules that depend instead on the decision-maker consciously applying a metacognitive step and cognitively forcing a necessary consideration of alternatives.
  * The forcing feature of a cognitive strategy derives from "forcing functions," which can be built into system design such that error is minimised or avoided.
* 3 levels of cognitive forcing strateges: (1) universal, (2) generic, and (3) specific.
* **Universal cognitive forcing strategy**
  * Requires knowledge of error theory, and cognitive error in particular.
  * It is a forcing strategy insofar as there is an obligation to perform this cognitive step to appreciate how metacognitive processes work.
  * Without this stage, the other 2 cannot follow.
  * Such awareness might accomplish several goals:
    * Decision-makers become more cognisant of the range of pitfalls they can expect and therefore learn to avoid.
    * A language or lexicon develops that allows more ready description, communication, understanding, and prediction of common errors.
    * The heightened awareness promotes greater diligence.
    * A clearer vision about what research is necessary to investigate cognitive errors.
* **Generic cognitive forcing strategy**
  * Requires understanding of the major classes of heuristics used in decision-making.
  * The choice of a particular cognitive forcing strategy depends on this knowledge.
  * For example, consider search satisficing error.
    * "Satisficing" refers to the general tendency to call off a search once something has been found.
    * The generic cognitive forcing strategy for this error is to force oneself always to conduct a secondary search or survey once a positive finding has been made or when a search has failed to turn up an expected finding.
* **Specific cognitive forcing strategy**
  * Requires awareness of specific scenarios in which the error is known to occur.
* Consider the case of an animal bite wound as an example, the steps in choosing a specific cognitive forcing strategy:
  1. **Initial training in the theory of metacognition.**
     * The individual is taught the value of stepping back from the immediate situation and reflecting on their thinking process.
     * Instead of going directly to the many important issues involved in the assessment of the wound and how it should be treated, the physician steps back cognitively and observes, "This patient has an animal bite wound."
     * Besides assessment and repair of the wound, what other issues absolutely must be considered?
  2. **Acquire knowledge of specific cognitive errors.**
     * In this example, the relevant error is one of omission, i.e., the physician might omit a critical step.
     * One of the most significant errors of omission for such a case lies in failing to elicit a history of immunocompromise where it exists.
     * In responding to the past medical history inquiry, the patient might not necessarily see the connection between these conditions and their present complaint.
  3. **Identify the particular scenario in which the cognitive error is likely to occur.**
     * In this example, the situation is clearly defined.
     * Any bite wound, human or animal, is usually straightforward, although ambiguity occasionally arises in cases of assault (e.g., clenched-fist injuries).
  4. **Select of a cognitive forcing strategy.**
     * In the case of an animal bite wound, the cognitive forcing strategy requires that the clinician should always work through a checklist of immunocompromise indicators in eliciting a past medical history.
  5. **Avoid or minimise error.**
     * By working through a checklist, the physician avoids the omission error of failing to detect immunocompromise and vulnerability to an opportunistic infection. (Croskerry, 2003)

### Checklists

* Ideal for deployment in a controlled environment with predictable situations and procedures.
* A debiasing strategy that challenges 'structure' of thought, attempting to force our cognition onto certain topics even if they were not previously considered.
* Nature of the checklist and content are likely important factors in their efficacy.
  * An experiment conducted by Shimizu et al. (2012) evaluated whether intuitive and analytic processes (using checklists) improve clinical diagnostic performance.
  * 2 types of checklists:
    * General debiasing checklist (GDBC)
      * Contained generic statements such as to obtain medical history and conduct physical examination, and generate initial hypothesis and take diagnostic "time out".
    * Differential diagnosis checklist (DDXC)
      * Contained, for each presenting complaint, a list of possible diagnosis and markers indicating frequently-missed and do-not-miss diagnoses.
      * E.g., the list for headache included migraine, dental caries (frequently missed), and meningitis (do not miss).
  * Findings:
    * DDXC may improve the diagnostic performance in difficult cases.
      * The frequently-missed and do-not-miss markings may have helped.
    * GDBC did not work well as a tool for better diagnostic performance.
      * Each item in the checklist was not designed to hint any specific differential diagnosis and so may be ineffective for specific clinical scenarios.
      * Participants were medical students (novices) and so the checklist might not have contributed to the baseline performance level without heuristic thinking.
    * Intuitive process may still be better for simpler cases.

### Dialectical Bootstrapping

* **Wisdom of crowds**
  * The average quantitative estimate of a group of individuals (where their errors are likely to differ) is consistently more accurate than the typical estimate, and is sometimes even the best estimate.
  * Individuals' estimates may be riddled with errors.
    * Averaging them boosts accuracy.
    * Both systematic and random errors tend to cancel out across individuals.
* Wisdom of the crowds can be simulated by a single mind through **dialectical bootstrapping**.
  * Enhances the quality of quantitative judgments by averaging the first estimate with a second, **dialectical estimate**.
    * Originating from the same person, has a different error than the first estimate.
    * Based on different knowledge and assumptions.
  * The 2 estimates are made as separate steps.
    * Encourages people to sample their knowledge twice, once for a low estimate and again for a high estimate. (Herzog & Hertwig, 2009)
* A technique for generating dialectical estimate: "**consider the opposite**".
  * Prompt people to consider knowledge that was previously overlooked, ignored, or deemed inconsistent with current beliefs.
  * Direct approach: Direct instructions to consider various hypothesis and opposite possibilities.
    * E.g., a professor asks a student what the data from a proposed experiment might mean if the expected results were reversed.
    * Or, asking people to think of reasons why their first judgment might be wrong.
  * Indirect approach: Alter the task or conditions in such a way as to make opposite possibilities more salient.
    * E.g., a professor asks the student to read a paper whose conclusions suggest an experimental outcome opposite to that expected by the student who has read only one side of a theoretical dispute.
      * The professor neither describes the tendency to ignore alternative data patterns nor instructs the student to adopt any particular cognitive strategy, but instead relies on the recommended paper to render opposite possibilities more accessible. (Lord et al., 1984)

## References

* Wikipedia Contributors. (2024, June 17). _Cognitive bias_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Cognitive_bias>
* Benson, B. (2016, September). _Cognitive bias cheat sheet. An organized list of cognitive biases because thinking is hard_. Medium; Better Humans. <https://betterhumans.pub/cognitive-bias-cheat-sheet-55a472476b18>
* O'Sullivan, E., & Schofield, S. (2018). Cognitive bias in clinical medicine. _Journal of the Royal College of Physicians of Edinburgh, 48_(3), 225–232. <https://doi.org/10.4997/jrcpe.2018.306>
* Wikipedia Contributors. (2023, November 27). _Debiasing_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Debiasing>
* Wikipedia Contributors. (2024, June 5). _Nudge theory_. Wikipedia; Wikimedia Foundation. <https://en.wikipedia.org/wiki/Nudge_theory>
* Niu, L., Behar-Horenstein, L. S., & Garvan, C. W. (2013). Do instructional interventions influence college students' critical thinking skills? A meta-analysis. _Educational Research Review, 9_, 114–128. <https://doi.org/10.1016/j.edurev.2012.12.002>
* Jones, M., Butler, J., Graber, C. J., Glassman, P., Samore, M. H., Pollack, L. A., Weir, C., & Goetz, M. B. (2017). Think twice: A cognitive perspective of an antibiotic timeout intervention to improve antibiotic use. _Journal of Biomedical Informatics, 71_, S22–S31. <https://doi.org/10.1016/j.jbi.2016.06.005>
* Croskerry, P. (2003). Cognitive forcing strategies in clinical decisionmaking. _Annals of Emergency Medicine, 41_(1), 110–120. <https://doi.org/10.1067/mem.2003.22>
* Shimizu, T., Matsumoto, K., & Tokuda, Y. (2012). Effects of the use of differential diagnosis checklist and general de-biasing checklist on diagnostic performance in comparison to intuitive diagnosis. _Medical Teacher, 35_(6), e1218–e1229. <https://doi.org/10.3109/0142159x.2012.742493>
* Herzog, S. M., & Hertwig, R. (2009). The wisdom of many in one mind. _Psychological Science, 20_(2), 231–237. <https://doi.org/10.1111/j.1467-9280.2009.02271.x>
* Lord, C. G., Lepper, M. R., & Preston, E. (1984). Considering the opposite: A corrective strategy for social judgment. _Journal of Personality and Social Psychology, 47_(6), 1231–1243. <https://doi.org/10.1037/0022-3514.47.6.1231>
