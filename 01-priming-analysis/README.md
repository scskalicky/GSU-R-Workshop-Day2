# The Priming Data

The priming data is in the file `sp-priming.csv`, with these columns and variables:

variable|type|explanation
:-:|:-:|:-:
`score`|dependent variable| whether participant produced the target structure (1) or not (0)
`trial_type` | independent variable | the trial type, whether it was a prime (containing a stranded preposition) or control (no stranded preposition)
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