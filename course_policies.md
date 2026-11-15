# AI 2000: Assignment Policies

These rules apply to every solo assignment (HW0, A1–A4, and the A6 bonus; the
team project has its own handout). Read this once at the start of the semester;
each assignment links back here instead of repeating it.

## The one rule: Restart & Run All must pass

Your grade comes from running your notebook from a clean kernel, top to
bottom. Notebooks remember every cell you've ever run, in whatever order you
ran them, and that memory disappears when the kernel restarts. A cell you ran,
edited, and forgot to re-run is the most common way to lose points on work you
actually did.

Before you submit: **Kernel → Restart & Run All**, and confirm it reaches the
bottom without errors. Unfinished levels raise `NotImplementedError` on
purpose; once you've attempted every level, a clean run should be possible.

The grader does the same thing: fresh kernel, top to bottom, then it calls
your functions directly and checks what they return. It never reads your
printed output.

## Previewing your score

Each assignment ships with a grader you can run yourself:

```
python grader.py assignment.ipynb
```

It prints a per-level report and writes `results.json`. This is a preview.
The grade of record comes from our re-run of your submitted notebook on our
machines, under the pinned library versions in `requirements.txt`. The two
agree as long as Restart & Run All genuinely passes on your end.

## Submitting

Upload to D2L: `assignment.ipynb`, your final `artifact.png`, and (optional
but recommended) your `results.json` so we can flag any preview mismatch
instead of just grading you down.

## Late work

You have 3 grace days, pooled across A1–A4, applied automatically in whole-day
units. After the pool is spent, late work loses 10% per day, and nothing is
accepted more than 3 days late. The team project deadline is hard. Documented
emergencies are handled case by case; email the instructor.

## Partial credit

Every level grades in tiers: returning an array of the right shape and type
earns something even when values are wrong, and near-miss values earn a
scaled share. A level you never attempt earns nothing. The grader's messages
tell you which tier you missed; read them before coming to office hours,
and bring them with you when you do.

## Collaboration and AI tools

Talk to classmates about ideas as much as you like. The code you submit must
be yours: typed by you, understood by you. Credit substantial help in a
comment ("worked through L5 with J. Kim").

AI assistants (ChatGPT, Claude, Copilot, and the rest) are part of modern
practice and we won't pretend otherwise. On assignments they're permitted
for explanation and debugging. But know what you're trading: these exercises
are small enough that an AI can do them outright, and if you let it, you'll
pass the assignment and fail the exam, which is proctored, offline, and worth
more. A rule of thumb that will serve you all semester: it's fine to ask an
AI *why* your code is wrong; it's self-sabotage to ask it *what to type*.
If Copilot autocompletes the whole function before you've thought about it,
turn it off in the notebook editor. The struggle is the product.

On quizzes and exams, no AI, no exceptions.

## Environment

Assignments are built and graded against the exact versions in each package's
`requirements.txt`. They run on any laptop CPU or free Google Colab; nothing
in this course needs a GPU before the team project, and even that runs on
Colab's free tier. If your environment misbehaves, `pip install -r
requirements.txt` into a fresh virtual environment, or just use Colab.
