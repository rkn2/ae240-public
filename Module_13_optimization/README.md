# optimization

## Lesson 1: Brute Force, Grid Search & the Curse of Dimensionality
- [1_optimization_session1_v26](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/1_optimization_session1_v26.ipynb)
- [1_optimization_session1_v26_SOLUTION](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/1_optimization_session1_v26_SOLUTION.ipynb)

## Lesson 2: Working Smarter — scipy.optimize.minimize, and Finding Optima with Calculus
- [2_optimization_session2_v26](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/2_optimization_session2_v26.ipynb)
- [2_optimization_session2_v26_SOLUTION](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/2_optimization_session2_v26_SOLUTION.ipynb)

Session 2 now ends with a cubic-function example (profit vs. number of
employees) that finds the optimum using the function's derivative instead
of guessing -- trimmed down from the original draft (skips re-demonstrating
curve_fit/minimize on a new dataset, which students already know) and
re-bridged so it reads as one continuous lesson rather than a tacked-on
addition.

## Homework
- [3_optimization_homework_v26](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/3_optimization_homework_v26.ipynb)
- [3_optimization_homework_v26_SOLUTION](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/3_optimization_homework_v26_SOLUTION.ipynb)

Problem 1 has a Part E (15 points total, up from 12) where students find
the lamp-height optimum via the model's derivative instead of guessing an
`x0` -- the same technique Session 2 now teaches. The old "Part E"
(analytical vs. computational) is renumbered to Part F and now compares
against both the guess-based (D) and derivative-based (E) answers.

## Extra material (optional, cut from Session 2 for time)
The bad-guess-vs-good-guess numerical optimization demo (shows
`optimize.minimize()` failing with a poor initial guess on the cubic, then
succeeding with a better one) and a set of discussion/reflection questions
on diminishing returns in AE. Builds on Session 2's cubic-function cells --
run those first if using this standalone.
- [optimization_extra_cubic_v26](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/optimization_extra_cubic_v26.ipynb)
- [optimization_extra_cubic_v26_SOLUTION](https://colab.research.google.com/github/rkn2/ae240/blob/v26/Module_13_optimization/optimization_extra_cubic_v26_SOLUTION.ipynb)

## Canvas Submissions
- [Session 1 In-Class](./optimization_inclass1.xml)
- [Session 2 In-Class](./optimization_inclass2.xml)
