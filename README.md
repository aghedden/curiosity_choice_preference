# curiosity_choice_preference
Task and Analysis Code for independent project investigating how curiosity shapes choice preferences for incidentally encoded stimuli.

## Tasks

### `trivia_screening_task`
**Part 1: Trivia Screening and Encoding**

Participants complete an initial screening task in which they rate a series of trivia questions based on:
- **Confidence** in knowing the answer
- **Curiosity** to find out the answer

From these ratings, a subject-specific set of 48 **high-curiosity** and 48 **low-curiosity** trivia questions is generated. Participants then view these selected questions again, each paired with a **perceptually novel object**, presented under either high- or low-curiosity conditions. After viewing the object, they are shown the correct trivia answer.

### `memory_choice_task`
**Part 2: Memory and Decision-Making** (24-hour delay between study parts)

Participants complete the following tasks:
1. A **memory recall task** for the **correct trivia answers** presented the day prior
2. A **memory recognition task** (old/new judgements) for the **novel objects** seen in Part 1
3. A **choice task**, where they are asked to make choices between pairs of previously seen objects and new objects

This phase allows researchers to assess how curiosity affects both memory performance and decision-making preferences.


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
