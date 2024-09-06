# Protocols, experiments and projects

In this page I define some terminology related to protocols, experiments and projects used in the rest of the book.

You are probably familiar with experimental protocols.
They are textual files with (detailed) instructions on how to carry out some experimental procedure.
The traditional protocol refers to the whole procedure of carrying out an experiment: from sample collection, to preparation, to measurement, to the interpretation of the results.
However, for the sake of this book, we will use slightly different definitions for all of these terms:
- An **experiment** is a series of *protocols* to follow to obtain one or more measurements, usually - but not necessarely - from real-world objects.
- A **protocol** is a detailed procedure to obtain some output *thing* (be it an item, a measurement, or a combination of) from zero or more inputs.
  It might contain some generic instructions, and it may be flexible in some aspects.
- A **realization** of an experiment is the same experiment with protocols without any potential variability: every choice was made and is now "set in stone".
- A **run** of a realization is an actual real event that took place when the steps of a realized experiment were carried out.
  As life is not perfect, each run might be slightly different because of variables out of our control, be it unforseen circumstances (something is broken) or intrinsic variables (the day that the experiment was performed, or who performed the experiment).
- Each run (generally) produces one or more **measurements**.
  The collection of these measurements is our data.
- A **project** is a collection of *measurements* which ultimately are interpreted together towards some goal, like the refusal of a hypothesis.

<div align="center">
<img src="https://github.com/MrHedmad/mimir/blob/main/resources/images/Basic_project_structure.png?raw=true">
</div>
