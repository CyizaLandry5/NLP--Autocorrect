# NLP: Autocorrect

## Course Information
- **Course:** Course 2 - Natural Language Processing (Probabilistic Models)
- **Platform:** DeepLearning.AI
- **Assignment:** #1 - Autocorrect System

## 📌 Overview
This assignment gave me a chance to brush up on my Python and probability skills while building an effective and practical **autocorrect system** – similar to what you see every day on your cell phone and computer. Behind the scenes, autocorrect uses clever string manipulation and probability to suggest the right word when you make a typo.

The model I implemented was first created by [Peter Norvig](https://norvig.com/spell-correct.html) in 2007, and it remains a classic introduction to spelling correction systems.

## 🎯 What I Learned
- **Word Counting & Probability:** Computed word frequencies and probabilities from a given corpus (Shakespeare text).
- **String Manipulation:** Implemented four core edit operations:
  - Delete a letter
  - Switch two adjacent letters
  - Replace a letter with another
  - Insert a new letter
- **Edit Distance:** Built all possible words that are 1 or 2 edits away from a given word.
- **Suggestion Algorithm:** Combined probability and edit distance to return the most likely correct spelling.
- **Minimum Edit Distance (Dynamic Programming):** Implemented the classic DP algorithm to compute the minimum number of edits required to transform one string into another.

## ⚙️ Key Skills Practiced
- Corpus preprocessing (reading files, lowercasing, tokenization)
- N-gram frequency analysis
- Set operations for vocabulary filtering
- Dynamic programming for string alignment
- Bayesian probability for word correction
- List comprehensions and string slicing

## 🚧 Challenges Faced
1. **Getting the Splits Right:** Generating all possible splits (L,R) of a word required careful indexing, especially handling edge cases like empty strings.
2. **Duplicate Elimination:** Ensuring that edit functions returned unique strings (using sets instead of lists) was critical to avoid redundant suggestions.
3. **Handling the Empty String in Insertions:** The `insert_letter` function initially missed insertions at the end of the word because I didn't include the final split `('word', '')`.
4. **Combining Edits Efficiently:** For `edit_two_letters`, running edit operations on every output of `edit_one_letter` created thousands of candidates – managing performance while keeping the set unique was challenging.
5. **Dynamic Programming Table Initialization:** Filling the first row and column of the distance matrix with cumulative insertion/deletion costs took practice to get right.
6. **Understanding the Minimum Edit Distance Recurrence:** Implementing the `min()` of three operations (delete, insert, replace/match) required careful debugging to ensure the costs propagated correctly.

## 📋 Important Submission Notes (AutoGrader)
To avoid `Grader Error: Grader feedback not found` or similar unexpected errors from the DeepLearning.AI AutoGrader, I made sure NOT to:
- Add any extra `print` statements in the assignment
- Add any extra code cells
- Change any of the function parameters
- Use global variables inside graded exercises (unless specifically instructed)
- Change the assignment code where not required (like creating extra variables)

> 💡 **Tip:** If you run into unexpected grader errors, check the above points first. You can always get a fresh copy of the assignment by following the workspace refresh instructions on DeepLearning.AI.

## 🛠️ Technologies & Tools
- Python 3
- NumPy
- Pandas (for displaying distance matrices)
- Regular Expressions (re module)
- Collections (Counter, defaultdict)
- Jupyter Notebook / VS Code

## 📈 Results
- Successfully built a working autocorrect prototype.
- The model can suggest corrections for misspelled words using 1-edit and 2-edit distances.
- Implemented a spell checker that returns the most probable correct word based on corpus statistics.
- Built a minimum edit distance calculator using dynamic programming (insert/delete/replace costs).

### Example Output
For input `'dys'`, the model suggested:
- `'days'` (probability 0.000410)
- `'dye'` (probability 0.000019)

For minimum edit distance from `'play'` to `'stay'`:

s t a y
0 1 2 3 4
p 1 2 3 4 5
l 2 3 4 5 6
a 3 4 5 4 5
y 4 5 6 5 4

Minimum edits: **4**

## 🔗 Related Concepts
- Bayesian spelling correction: P(c|w) = P(w|c) × P(c) / P(w)
- Edit distance (Levenshtein distance)
- Dynamic programming for string alignment
- N-gram language models
- Peter Norvig's spell corrector

## 📚 Acknowledgments
This assignment was completed as part of the Natural Language Processing specialization on **DeepLearning.AI**. The autocorrect implementation follows Peter Norvig's classic approach, with additional focus on edit distance algorithms from Stanford's CS124 (Dan Jurafsky).

---