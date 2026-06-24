## TakeMeter - planning.md

---

## Community
The World Cup is a trending bed of hot opinionated posts, opinions disguised as facts and speculation about the future of soccer (also referred to as football) and its players. r/worldcup is a great medium to extract these posts and comments from while matches are actively happening and classification would be well-contained pulling from this source since it only discusses events related to the World Cup 2026 and not about the general sport of soccer or other broader subject matters. Placing labels can define if a statement is a fact or opinion since prediction tend to be rooted in opinions rather than fact and discussion can be classified as into opinionated reactions and analytic explanations. If fans know what to be mad about, they can be mad at it more effectively.

## Summary
The project will classify r/worldcup posts and comments by the kind of sports discourse they represent: quick reactions/opinions, evidence-backed analysis, future predictions, or information-seeking questions. The dataset should be balanced enough that the model cannot succeed by over-predicting the most common label. Evaluation should focus on the hardest label boundaries, especially **Reaction/Opinion** vs. **Analysis/Explanation** and **Question** vs. **Prediction**.

## Labels
**Label 1: Reaction/Opinion** This label is to be annotated for posts discussing the results of a match and/or player within the scope of the World Cup 2026 and includes only the posts discussing the current and historical state of the sport.
 - Examples:
    - "Cristiano Ronaldo is noted for being incredibly kind and humble. Harry Kane is an infamous jerk and reportedly supports reintroduction of corporal punishment in English schools."
    - "The Fox Sport graphics for this world cup is so fucking bad bro. Just AI slop jammed into every pixel."
    - Uncertain case: "I kept hearing CR7 is washed and should come off the bench?"
      - Decision: Label as **Question** if the post is sincerely asking for community input. Label as **Reaction/Opinion** if the question mark is rhetorical and the main purpose is calling CR7 washed.

**Label 2: Analysis/Explanation** This label is to be annotated for posts that provide concrete evidence (that may be fallible) behind their discussion points rather than making opinionated comments within the scope of the World Cup 2026. This will only include posts with at least one concrete evidence to back up their claims which must be about the past or present.
 - Examples:
    - "Kylian Mbappé reaches Miroslav Klose’s goal record at the World Cup with 16 goals. Closing up to Lionel Messi's record of 18 World Cup goals"
    - "he has an average of 1 goal per match and still 4 world cups to go.
    messi a bit more than 0.64 and it's his last world cup"
    - Uncertain case: "His 2014 and 2010 team were actually very good. So were his 2018, 2022 and 2026 teams. They just were edged out in Quarter final, Semis or Finals or were up against future winning teams. Mbappe has no doubt one of the strongest football teams in World cup history" (what does "good" mean?)
      - Decision: Label as **Analysis/Explanation** because it supports the claim using historical tournament results and team context, even though "very good" is subjective.

**Label 3: Prediction** This label is to be annotated for posts that predict and make calls for futuristic events. This label is only to be included for posts and comments that pertain to the future of soccer and its players within the scope of the World Cup 2026.
 - Examples:
    - "Brazil vs Japan feels like one of those matches that could be much closer than people expect."
    - "Mbappe will become the highest scorer and I predict his record will go unbroken for the next 30 or so years. He's a ferocious goal scorer. Messi is the more complete player, no question, but Mbappe has the luxury of youth, being a dedicated attacking forward, and future world cups will continued to be more watered down with weaker teams. It's a perfect recipe for this kind of record"
    - Uncertain case: "Current projected Round of 32 based on today's standings:

                    Germany vs Czechia
                    France vs Paraguay
                    South Korea vs Switzerland
                    Netherlands vs Morocco

                    Portugal vs Ghana
                    Spain vs Austria
                    USA vs Sweden
                    Egypt vs Cape Verde

                    Brazil vs Japan
                    Ivory Coast vs Norway
                    Mexico vs Scotland
                    England vs DR Congo

                    Argentina vs Uruguay
                    Australia vs Iran
                    Canada vs Belgium
                    Colombia vs Algeria

                    Which matchup would you most want to see?"
      - Decision: Label as **Prediction** if the projected bracket is the main substance. Label as **Question** only if the bracket is just setup for asking user preferences.

**Label 4: Question** This label is to be annotated for posts that are primarily a query (more than 50% of the words must be related to a query). This can be related to the World Cup 2026 matches, travel tips, logistics regarding the sport in any capacity but MUST be primarily a query more than the other labels.
 - Examples:
    - "Would anyone at the Bosnia match tomorrow be interested in a Seattle Sounders / Bosnia jersey swap?" 
    - "Have we had an upset win yet? We did have upset draws (Cape Verde, Curacao, etc) but an outright win?"
    - Uncertain case: "Predictions for Colombia v Congo? Hopefully Colombia wins."
      - Decision: Label as **Question** because the main purpose is asking other users for predictions; label as **Prediction** only when the author makes their own clear forecast.


## Hard edge cases

1. **Question vs. Prediction**
   - Difficult example: "Predictions for Colombia v Congo? Hopefully Colombia wins."
   - Possible labels: Question or Prediction.
   - Decision: Label as **Question** if the main purpose is asking other users for takes, even if the post includes the author's preferred outcome. Label as **Prediction** only when the author makes a clear future-facing claim such as "Colombia will win 2-0" or "Congo is going to upset them."

2. **Reaction/Opinion vs. Question**
   - Difficult example: "I kept hearing CR7 is washed and should come off the bench?"
   - Possible labels: Reaction/Opinion or Question.
   - Decision: Label as **Question** if the post is mainly seeking clarification, confirmation, or community input. Label as **Reaction/Opinion** if the question mark is being used rhetorically and the post mainly states a quick take about a player, team, match, broadcast, or tournament issue.

3. **Reaction/Opinion vs. Prediction**
   - Difficult example: "Brazil vs Japan feels like one of those matches that could be much closer than people expect."
   - Possible labels: Reaction/Opinion or Prediction.
   - Decision: Label as **Prediction** when the post describes what might happen in a future match, bracket, award, lineup, or player performance. Label as **Reaction/Opinion** when the post is mostly a present-tense or past-tense take without a specific future claim.

4. **Projected standings or bracket posts**
   - Difficult example: "Current projected Round of 32 based on today's standings: Germany vs Czechia, France vs Paraguay... Which matchup would you most want to see?"
   - Possible labels: Prediction or Question.
   - Decision: Label as **Prediction** if the post's substance is a projected future bracket, standings result, qualification outcome, or matchup list. Label as **Question** if the future scenario is only background and the main purpose is asking users for preferences, travel advice, tickets, logistics, or personal plans.

5. **Reaction/Opinion vs. Analysis/Explanation**
   - Difficult example: "The Fox Sport graphics for this world cup is so bad. Just AI slop jammed into every pixel."
   - Possible labels: Reaction/Opinion or Analysis/Explanation.
   - Decision: Label as **Reaction/Opinion** when the post mainly gives an emotional or evaluative take without supporting evidence. Label as **Analysis/Explanation** when the post gives concrete reasons, statistics, match events, tactical explanations, historical comparisons, or other evidence for the claim.

6. **Logistics posts**
   - Difficult example: "Anyone know if bags are allowed at MetLife for the semifinal?"
   - Possible labels: Question or Reaction/Opinion.
   - Decision: Label as **Question** when the post asks for practical information, advice, ticket help, travel planning, meetups, rules, or scheduling. These posts still belong in the taxonomy because they are part of World Cup community discourse, even when they are not about match analysis.

7. **Very short or low-context posts**
   - Difficult example: "USA in trouble tomorrow?"
   - Possible labels: Question, Prediction, or Reaction/Opinion.
   - Decision: Use the surface intent when context is limited. If it is phrased as a direct question, label **Question**. If it asserts an expected future outcome, label **Prediction**. If it only reacts to something already happening or already happened, label **Reaction/Opinion**.

8. **Annotation tie-breaker rule**
   - If a post could reasonably fit more than one label, choose the label that describes the post's main communicative purpose:
     - Asking for an answer or advice = **Question**
     - Forecasting a future outcome = **Prediction**
     - Giving a quick take, emotional reaction, or unsupported opinion = **Reaction/Opinion**
     - Explaining a claim with concrete evidence, reasons, statistics, tactics, or historical comparison = **Analysis/Explanation**
   - When the purpose is still unclear, write a short note in the dataset notes column so the decision can be reviewed later for consistency.


## Data collection plan
Collect at least 200 public posts or comments from r/worldcup, focusing on pinned match threads, daily discussion threads, bracket/standings posts, travel/logistics threads, and highly active posts during the World Cup 2026 cycle.

Target label distribution:

- **Reaction/Opinion**: about 50 examples
- **Analysis/Explanation**: about 50 examples
- **Prediction**: about 50 examples
- **Question**: about 50 examples

This split keeps the dataset close to even across all four labels so the model cannot succeed by learning only the most common type of sports comment. If **Reaction/Opinion** is overrepresented, I will intentionally collect more from threads that invite explanation, speculation, or practical help. If **Analysis/Explanation** is underrepresented, I will look for longer comments that compare teams, cite past tournaments, explain tactics, discuss player statistics, or give reasons for why a team succeeded or failed. If **Prediction** or **Question** is underrepresented, I will collect from pre-match threads, bracket projection posts, "who will win" posts, ticket/travel questions, and lineup speculation.

Each example will be saved in one CSV with these columns:

```csv
text,label,notes
```

The **notes** column will be used for ambiguous cases, especially posts that are questions asking for predictions, projected bracket posts, and short comments with limited context. During labeling, each post will be assigned based on its main purpose:

- Asking for information or opinions = **Question**
- Forecasting a future result or outcome = **Prediction**
- Giving a quick take, emotional reaction, or unsupported opinion = **Reaction/Opinion**
- Explaining a claim with concrete evidence, reasons, statistics, tactics, or historical comparison = **Analysis/Explanation**

## Evaluation metrics
Use overall accuracy to measure general performance, but do not rely on accuracy alone because the labels may not be perfectly balanced. Also report per-class precision, recall, and F1.

The primary metric will be **macro F1**, because each label matters and the model should perform reasonably across all four classes instead of only doing well on the most common one.

Important class-level checks:

- **Question recall**: shows whether the model catches posts that are mainly asking for input.
- **Prediction precision**: shows whether the model is over-labeling any future-related language as prediction.
- **Reaction/Opinion precision**: shows whether the model is using this label too broadly for anything emotional or casual.
- **Analysis/Explanation recall**: shows whether the model catches evidence-backed sports reasoning instead of collapsing it into simple opinion.

Use a confusion matrix to identify which boundaries are hardest. The most important expected confusion pairs are:

- **Question** predicted as **Prediction**
- **Prediction** predicted as **Analysis/Explanation** when a future claim includes supporting reasons
- **Analysis/Explanation** predicted as **Reaction/Opinion** when reasoning is mixed with strong opinion
- **Reaction/Opinion** predicted as **Question** when posts use rhetorical questions

Compare the fine-tuned DistilBERT model against the zero-shot Groq Llama baseline on the same test set.

## Definition of success
The classifier is successful if it performs meaningfully better than the zero-shot baseline and handles all four labels with usable consistency.

Minimum success criteria:

- Fine-tuned model accuracy is at least **65%**
- Fine-tuned model macro F1 is at least **0.60**
- No individual label has F1 below **0.50**
- Fine-tuned model beats the zero-shot baseline on either accuracy or macro F1

A strong result would be:

- Accuracy of **72% or higher**
- Macro F1 of **0.68 or higher**
- Most mistakes are understandable boundary cases rather than obvious label failures

The model would be useful as a real community tool if it can reliably separate quick fan reactions, deeper analysis, future speculation, and practical questions. This would let users filter for the kind of World Cup discourse they want: hot takes, reasoned explanations, match predictions, or information-seeking posts. It does not need to be perfect on sarcastic, very short, or highly ambiguous posts, but those failure modes should be documented clearly in the evaluation report.

## Assumptions
- The dataset will use one CSV rather than manually pre-split train/test files.
- Labels will remain exactly **Reaction/Opinion**, **Analysis/Explanation**, **Prediction**, and **Question**.
- r/worldcup is the only source unless there are not enough examples for one label.
- Ambiguous examples will be kept rather than removed, but they will include notes for later failure analysis.

---

## AI Tool Plan
AI tools will be used to stress-test the label definitions, speed up review in controlled ways, and help identify patterns in model failures. AI output will not be treated as final truth; every label and every evaluation claim will be reviewed manually against the taxonomy.

### Label stress-testing
Before labeling the full dataset, I will give an AI tool the four label definitions and the hard edge-case rules from this plan. I will ask it to generate 5-10 r/worldcup-style posts that sit near the boundaries between:

- **Question** and **Prediction**
- **Prediction** and **Analysis/Explanation**
- **Reaction/Opinion** and **Analysis/Explanation**
- **Reaction/Opinion** and **Question**

I will manually label those generated examples using my rules. If I cannot label them consistently, I will revise the label definitions or hard edge-case rules before annotating the full dataset. The goal is to find confusing boundaries early instead of discovering them after 200 examples are already labeled.

### Annotation assistance
I will use an AI tool to pre-label small batches of collected examples, but only as a first-pass assistant. If I use this workflow, I will provide the tool with the exact label definitions and require it to return one of the four valid labels: **Reaction/Opinion**, **Analysis/Explanation**, **Prediction**, or **Question**.

Every AI-suggested label will be manually reviewed before it enters the final CSV. I will use the **notes** column to mark examples where the AI suggestion was wrong, uncertain, or needed human correction. If the AI repeatedly confuses the same pair of labels, I will use that as a signal to collect more examples or clarify the taxonomy.

### Failure analysis
After running the zero-shot baseline and the fine-tuned model, I will use an AI tool to help review the wrong predictions. I will provide the misclassified examples, true labels, predicted labels, and any confidence scores available. I will ask the tool to look for patterns such as:

- Questions being mistaken for predictions because they ask for future outcomes
- Predictions being mistaken for analysis because they include evidence or background
- Analysis posts being mistaken for reaction/opinion because they contain strong fan language
- Reaction/opinion posts being mistaken for questions because they use rhetorical questions
- Very short posts or sarcastic posts causing inconsistent predictions

I will verify any AI-suggested pattern myself by rereading the examples and checking the confusion matrix. Only patterns I can confirm manually will be included in the README evaluation report.
