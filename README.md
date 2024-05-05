# GSU-R-Workshop-Day2

This workshp works through data used in [Kim et al. (2019)](https://doi.org/10.1017%2FS0272263119000093)


> Kim, Y., Jung, Y., & Skalicky, S. (2019). Linguistic alignment, learner characteristics, and the production of stranded prepositions in relative clauses. *Studies in Second Language Acquisition*, *41*(5), 937–969.

This research compared the degree of **primed production** of English stranded prepositions among Korean learners of English. Learners completed an alignment session, where half of their input trials included a stranded preposition, and half did not. After each trial, we assessed whether the participants produced (or did not produce) a stranded preposition. If a participant produced a stranded preposition after an input trial containing a stranded preposition, this was taken as evidence of alignment. We also measured the degree of **learning** of stranded prepositions from the alignment sessions using a pre/immediate/delayed posttest design. These two questions are further nested within a comparison of **modality**: half of the participants completed the alignment session in a face-to-fact (FTF) context, whereas the other half completed the session in a synchronous computer-mediated context (SCMC). A separate control condition only completed the pre/immediate/delayed posttests and did not participate in the alignment sessions. 

As such there are two main analyses:
    1. What is the degree of linguistic alignment, and are there differences between FTF/SCMC modality?
    2. Does the alignment session lead to learning of stranded prepositions, and are there differences between FTF/SCMC modality?

We answered both questions using *logistic regression*, which determines the probability of a binary outcome (yes/no, accurate/innacurate, etc) based on independent variables (modality, pre/post, etc.).

## The Priming Data

The priming data is in the file `sp-priming.csv`, with these columns and variables:

variable|type|explanation
:-:|:-:|:-:
`score`|dependent variable| whether participant produced the target structure (1) or not (0)
`type` | independent variable | the trial type, whether it was a prime (containing a stranded preposition) or control (no stranded preposition)
`modality` | independent variable | whether participant was in an FTF or SCMC context
`wmc` | independent variable | particpant's working memory capacity score 
`prod_pre` | independent variable | participant's pretest production score (production test)
`rec_pre` | independent variable | participant's receptive knowledge score (GJT)
`cloze` | independent variable | participant's proficiency score (cloze test)
`test` | control variable | test version (A or B, for counterbalancing)
`session` | control variable | first or second alignment session
`trial_order` |control variable| order of the questions within any one alignment session
`subject` | random effect | random intercept fit for each subject
`verb`| random effect | random intercept fit for each alignment trial (each trial had a unique verb)

## The Production Data

The production data is in the file `sp-production.csv`, with these columns and variables:

variable|type|explanation
:-:|:-:|:-:
`score`|dependent variable| whether participant produced the target structure (1) or not (0)
`priming_amount` | independent variable | the total number of trials where participant produced a stranded preposition after a prime trial during both alignment sessions
`group` | independent variable | whether participant was in `control` condition (no alignment sessions) or `exp` condition (completed alignment sessions)
`modality` | independent variable | whether participant was in an FTF or SCMC context
`time` | independent variable | test order: pretest, immediate posttest, delayed posttest
`wmc` | independent variable | particpant's working memory capacity score 
`rec_pre` | independent variable | participant's receptive knowledge score (GJT)
`cloze` | independent variable | participant's proficiency score (cloze test)
`test` | control variable | test version (1, 2, or 3, for counterbalancing)
`trial_order` |control variable| order of the questions within any one production test session
`subject` | random effect | random intercept fit for each subject
`verb`| random effect | random intercept fit for each test question (each question had a unique verb)


```
priming.model.full.interactions.m <- 
glmer(binary_score~Modality*Type+trial_order*Type+Session*Type+Cloze*Type+WMC*Type+prod_pre*Type+rec_pre_1_2*Type + 

(1+Type|subject)+(1|verb),a,family="binomial"(link="logit"),glmerControl(optimizer = "bobyqa",optCtrl=list(maxfun = 100000)))`
```

```
A total of 18 prime-target pairs and 18 filler pairs were used in alignment sessions 1 and 2, for a total of 36 trials per session (72 trials per student for both sessions).
```

