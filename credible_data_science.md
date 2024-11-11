# Am I making myself clear and credible?

(The title is partly inspired by [Harold Evans](https://en.wikipedia.org/wiki/Harold_Evans)'s book [_Do I Make Myself Clear_?](https://www.google.com/books/edition/_/Zvs3DAAAQBAJ?hl=en))



## Data

Always be skeptical of data. Always try to understand the origin of the data and how it has been processed.

Binning is sinning.

Use self-describing binary formats, such as [Apache Parquet](https://parquet.apache.org). Try to be clear about the units, using types or, as worst case alternative, [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation).

Label intervals by their starts and ends. See [CF Metadata Conventions](http://cfconventions.org).

Be alert for leakage from the future. Be alert for leakage in preprocessing transforms.

## Models

> _The Law of Decreasing Credibility_ The credibility of inference decreases with the strength of the assumptions maintained.

(Charles Manski)

[What Is The Chance Of An Earthquake](https://www.stat.berkeley.edu/users/stark/Preprints/611.pdf) by P.B. Stark and D.A. Freedman

[What is Bayesian/Frequentist Inference](https://normaldeviate.wordpress.com/2012/11/17/what-is-bayesianfrequentist-inference/) by Larry Wasserman

Start with a very simple model. End-to-end scaffolding and integration with production systems. Performance baseline. 

Use simulations to test your inference scheme and pretty much everything else.

> Point is that I've been doing this Bayes nonsense for a couple of decades now and I still get confused by basic things like how dispersion gets transformed from latent to outcome scale. I am long past thinking I am clever enough to get things right. Test test test

(Richard McElreath, https://twitter.com/rlmcelreath/status/1464876720331366406)

If there’s a key factor that you cannot quantify meaningfully (e.g., political will in a pandemic), then you should be very clear about the limitations of your model.

## Evaluation

- Compare with a simple model. This is particularly important for time series models. Can you beat a persistence model? If you beat a persistence model, your first thought should be: which of my features are leaking from the future?
- Probabilistic models should be evaluated using appropriate metrics, such as the Brier score and the continuous ranked probability score
- Check that probabilistic models are calibrated, neither under- nor over-dispersed

## Code

Code is, of course, how you instruct the computer to do what you want, but, more importantly, code, like prose, is a means to express your ideas. You should strive to be as clear possible.

Code is also your most important tool.

- Use expressive variable and function names
- Prefer short functions that do only one thing
- Avoid data mutation
- Certainly don’t mutate input variables
- Data, transform, transform, … , but don’t abuse lambdas ... pipelines
- Prefer composition ... pipelines are naturally composable
- Write lots of unit tests
- Unit tests should execute rapidly
- In Python, use type annotations
- Use precise types, such as date and datetimes instead of strings
- If you feel the need to comment code, consider whether the code could be written more clearly
- Raise precise and informative exceptions spelling out what was expected and what happened
- Use modern pandas style
- Where possible, adhere to the sklearn API
- Always explicitly set the seed of pseudorandom number generators
- It’s often helpful to build the scaffolding for the project early to ensure the flow of data, interfaces, etc
- Try to avoid doing to much work in a notebook
- Request reviews early and often; try to avoid submitting more than a couple of hundred lines of code for review (which can be difficult for a brand new project)
- It’s often helpful to take a top-down approach to writing code (Shalizi)
- Delete dead code
- Write docstrings following consistent style
- Use black (or equivalent code formatter)
- Think very hard about default values and whether they make sense
- Don’t do too much abbreviation of imports
- No side-effects
- Keep I/O at the boundaries of your code — see Destroy All Software

## Communication (including visualization)

As with code, the chief goal is clarity. Try to write simple declarative sentences in the active voice.

Write a proposal explaining the motivation for the project. Consider how skillful a model would have to be to have a meaningful impact.

Plots should be legible, axes should be labeled with units.

We should describe the evidence and the conclusions we have drawn as clearly as possible. Be sure to highlight the key assumptions and the sensitivity of the results to the assumptions. Uncertainty.

Review code promptly and thoroughly. Think of code reviews as opportunities to learn. How would you solve the problem your colleague has solved? Do you understand the intent of every function?

Check for spelling mistakes!

## References

[All of Statistics: A Concise Course in Statistical Inference](https://www.google.com/books/edition/All_of_Statistics/qrcuBAAAQBAJ?hl=en&gbpv=0), Larry Wasserman

[Data Analysis: A Bayesian Tutorial](https://www.google.com/books/edition/Data_Analysis/Kxx8CwAAQBAJ?hl=en&gbpv=0), D.S. Sivia with J. Skilling

[Foundations of Agnostic Statistics](https://www.google.com/books/edition/Foundations_of_Agnostic_Statistics/u1N-DwAAQBAJ?hl=en&gbpv=0), Peter Aronow and Benjamin Miller

[Information Theory, Inference and Learning Algorithms](https://www.google.com/books/edition/Information_Theory_Inference_and_Learnin/AKuMj4PN_EMC?hl=en&gbpv=0), David J.C. MacKay

[Structure and Interpretation of Computer Programs](https://www.google.com/books/edition/Structure_and_Interpretation_of_Computer/iL34DwAAQBAJ?hl=en&gbpv=0&kptab=overview), Harold Abelson and Gerald Jay Sussman with Julie Sussman