---
layout: post
title: Cognitive Bias - Availability Heuristic
categories: psychology bias
published: true
plantuml: true
---

Availability heuristic, also known as _availability bias_, is the tendency to overestimate the importance and likelihood of events with greater "availability" in memory, which can be influenced by how recent the memories are or how unusual or emotionally charged they may be.

<plantuml data-caption="Availability heuristic at a glance" data-alt="Availability heuristic at a glance - what is, psychology processes, impact, debiasing">
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

* Availability heuristic
  * Using information that comes to mind quickly and easily
    * Learned recently (proximity)
    * Salient or easier to remember (memorability)
    * Significant impact
    * Think about frequently
  * Psychology processes
    * Conditions of uncertainty
    * Number of examples recalled
    * Ease of recalling examples
  * Bad decision-making
    * Memories recalled insufficient to gauge likelihood of recurrence
    * Overestimation with low-quality information
  * Debiasing
    * Avoid impulse decisions/judgements
    * Clear echo chambers
    * Watch trends
    * Consider statistics
    * Keep records
    * Apply red-teaming

@endmindmap
</plantuml>

_Note: The information on this page is mainly summarised from the references listed below._

## Availability Heuristic

* Describes our tendency to use information that comes to mind quickly and easily when making decisions about the future.
  * Singular memorable moments have an outsized influence on decisions when compared to less memorable ones.
  * We analyse information in a way that prioritises memorability and proximity over accuracy.
* Helps us make choices easier and faster by drawing information from our memory.
  * The tradeoff for this snap judgment is losing our ability to accurately gauge the probability of certain events.
  * Our memories may not be realistic models for forecasting future outcomes.
* Certain information might be more readily available in your mind because it is:
  * something you recently learned (proximity),
  * more salient or easier to remember (memorability).
  * an event that had a significant impact on you,
  * something that you think about frequently, or
* Some memories appear to happen more often than they do because they are more easily recalled.
  * E.g., some people assumed that more words begin with K, even though a typical body of text contains twice as many words in which K is the third letter.
* Events that leave a lasting impression seem more common.
  * E.g., many people falsely assume that driving is safer than flying since it is easier to recall vivid images of deadly plane crashes than car crashes.
* Possible psychology processes that create the availability heuristic:
  * Conditions of uncertainty (situations involving imperfect or unknown information) trigger the use of the availability heuristic.
  * The number of examples recalled from memory is used to infer the frequency with which such instances occur.
  * The ease with which examples come to mind is used to infer the frequency of such instances.
* Can lead to bad decision-making.
  * Memories that are easily recalled are often insufficient for figuring out how likely these things are to happen again.
  * Our overestimation leaves us with low-quality information to form the basis of our decisions.
    * Less memorable events that contain better quality evidence to inform our predictions remain untouched.

## Examples

* Researchers in 1989 found that mock jurors rated a witness to be more deceptive if the witness testified truthfully before lying than when the witness was caught lying first before telling the truth.
  * Lying second remained in jurors' minds since it was more recent.
* After Hurricane Katrina in 2006, flood insurance policies increased by 14.3%.
  * After some time passed, insurance rates steadily declined back to normal.
  * Since it's easier to recall the experience of a disaster that occurred recently, people are likely to overestimate the risk that it can happen again.
  * On the other hand, since it is more difficult to recall a disaster that occurred in the past, people are likely to underestimate the risk of it happening again.
* Physicians who are influenced by a recent experience with a certain kind of disease may be more likely to diagnose other similar diseases as that particular disease. (Li et al., 2020)
  * Diagnostic accuracy is not significantly improved by reflective reasoning.
    * Reflective reasoning: Reasoning about one's own reasoning.
    * In this study, reflective reasoning was induced with instructions to participants to:
      * review the medical cases again;
      * write down the initial diagnosis;
      * list evidence that supports the initial diagnosis;
      * list items that are against the initial diagnosis;
      * list evidence that should be present if the initial diagnosis was accurate but not mentioned in the case;
      * list alternative diagnoses if they felt their initial diagnosis was incorrect, and follow the 3 preceding steps for each alternative diagnosis;
      * finally, write down the final diagnosis.
  * When a wrong initial hypothesis is triggered by availability bias, other biases, such as the _anchoring effect_, _confirmation bias_ and _premature closure_, may activate, thereby hindering the correction of the incorrect diagnoses.

## Debiasing

* Avoid making **impulse decisions or judgments**.
  * Instead of making snap decisions, give yourself time to examine the evidence and reach a conclusion.
  * When you're about to make a decision on the fly, take a moment to think about it:
    * What's informing your decision?
    * Where's your judgment of the situation coming from?
* Clear out your **echo chambers**.
  * Seek out information sources that don't necessarily line up with your personal beliefs.
* Watch overall **trends and patterns**.
  * Recent events can skew your perception of reality, but the long-term trends and patterns may tell a different story.
* Consider overall **statistics**.
  * Relying on singular anecdotes can lead to inaccuracy.
  * Research the base rate.
* Keep **records**.
  * If you know you will be basing a decision on a specific type of information, keep records to track such information rather than relying on memory.
* **Red teaming** (for teams)
  * Pick one or more person from the team to be the devil's advocate.
    * Main role is to challenge or oppose the ideas of the majority and suggest alternatives.
  * May show weak points and may reduce the effect of the availability heuristic.
  * Others will be more willing to come up with their own ideas and disagree with the original suggestion.

## References

* Wikipedia contributors. (2024, May 23). _Availability heuristic_. Wikipedia. <https://en.wikipedia.org/wiki/Availability_heuristic>
* Pilat, D., & Krastev, S. (2024, May 21). _Why do we tend to think that things that happened recently are more likely to happen again?_. The Decision Lab. <https://thedecisionlab.com/biases/availability-heuristic>
* Perry, E. (2021, October 4). _The Cognitive Biases Caused by the Availability Heuristic_. Betterup.com. <https://www.betterup.com/blog/the-availability-heuristic>
* Cherry, K. (2023, September 5). _What Is the Availability Heuristic?_. Verywell Mind. <https://www.verywellmind.com/availability-heuristic-2794824>
* Buric, R. (2022, September 15). _Availability Heuristic - Everything You Need to Know_. InsideBE. <https://insidebe.com/articles/availability-heuristic/>
* Li, P., Zi Yan Cheng, & Gui Lin Liu. (2020). Availability Bias Causes Misdiagnoses by Physicians: Direct Evidence from a Randomized Controlled Trial. _Internal Medicine_, 59(24), 3141–3146. <https://doi.org/10.2169/internalmedicine.4664-20>
