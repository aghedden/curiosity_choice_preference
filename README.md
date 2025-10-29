# curiosity_choice_preference
Task and Analysis Code for independent project investigating how curiosity shapes choice preferences for incidentally encoded stimuli.

## Tasks

### `trivia_screening_task`
**Part 1: Trivia Screening and Encoding**

Participants complete an initial screening task in which they rate a series of trivia questions based on:
- **Confidence** in knowing the answer
- **Curiosity** to find out the answer

From these ratings, a subject-specific set of 48 **high-curiosity** and 48 **low-curiosity** trivia questions is generated. Participants then view these selected questions again, each paired with a **perceptually novel object**, presented under either high- or low-curiosity conditions. After viewing the object, they are shown the correct trivia answer.

Note: `original_cognition_part_1` contains the same task, just in txt format to easily load into Cognition.run, which already contains HTML and CSS components and is, thus, no needed in the task code itself.

### `memory_choice_task`
**Part 2: Memory and Decision-Making** (24-hour delay between study parts)

Participants complete the following tasks:
1. A **memory recall task** for the **correct trivia answers** presented the day prior
2. A **memory recognition task** (old/new judgements) for the **novel objects** seen in Part 1
3. A **choice task**, where they are asked to make choices between pairs of previously seen objects and new objects

This phase allows researchers to assess how curiosity affects both memory performance and decision-making preferences.

Note: `original_cognition_part_2` contains the same task, just in txt format to easily load into Cognition.run, which already contains HTML and CSS components and is, thus, no needed in the task code itself.

## Analysis Scripts

### `cur_pref_pwr_analyses.ipynb`
**Power analyses script for curiosity project**

- Several power analyses were run to determine how many people do we needed to test to be confident we can detect this effect
- The code simulated running the study with different numbers of participants (50, 100, 150, 200 people) to see how many would be needed to reliably find the curiosity effect.
- Power analyses were run with the object recognition model
- We tested with the following effect sizes:
  - Tests with their own pilot data effect size
  - Tests with smaller effects (to be conservative)
  - Tests using an effect size from a previous 2014 study by other researchers 

### `curiosity_pref_analyses.ipynb`
**Main analyses script for curiosity project**

- Runs through basic participant sumamry stats (age, race, etc.)
- Performs exploratory analyses on mean accuracies, general choice preferences, and distributions of various variables
- Performs the following main analyses:
  - Mixed-effects logistic regressions with outcome variable of image recognition/trivia recall accuracy, predictor variables curiosity and reaction time during initial encoding, random intercepts for subject, and random slopes for curiosity type
  - Mixed-effects logistic regression with outcome variable of P choose right, predictor variables (R-L), the difference in appeal between right and left image, the difference in familiarity between right and left image, the difference in interest between right and left image, and the interaction between R-L and the difference in appeal between right and left image. Random intercepts for subject and random slopes for R-L
- Creats visualizations to illustrate data trends, including violin/swarm overlay plot and regression plots with sigmoidal curves 


## Helper Scripts

### `clean_part1_data`
**Preprocess and Organize Data from Part 1**

- Cleans and reshapes raw data from the `trivia_screening_task`
- Assists in determining participant **eligibility** for Part 2
- Generates a **personalized stimulus set** for each participant in Part 2  
  *(Note: Each participant receives a unique set of stimuli based on their curiosity ratings.)*


### `generate_random_passwords`
**Utility for Participant Code Management**

- Generates a set of unique passwords
- Each password includes the participant's **subject ID**
- For example, FM4KL2PIL124 may be the password for the participant with the subject ID **PIL124** *(FM4KL2**PIL124**)*
- Ensures that the proper stimuli are pulled into Part 2 for the given participant


### `det_mem_task_order.ipynb` 
**Utility for Task Order**
- Shuffles and splits the subject ids to randomly assign participants to each task order
- The output of this script is plugged into the task code for Part 2, telling jspsych what order to present that tasks to that participant in based on their subject id 
 
