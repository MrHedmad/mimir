# Experimental protocols

You are probably familiar with experimental protocols.
They are textual files with (detailed) instructions on how to carry out some
experimental procedure.

The traditional protocol refers to the whole procedure of carrying out an
experiment: from sample collection, to preparation, to measurement, to
the interpretation of the results.
However, for the sake of this book, we will use slightly different definitions
for all of these terms:
- A **project** is a collection of *experiments* which ultimately work in
  concert to support a certain hypothesis, or a collection of hypotheses.
  - Example: "Have tea with the others".
  - You can think of this to coincide with a scientific publication.
- An **experiment** is a series of *protocols* to follow to obtain one or more
  measurements, usually - but not necessarely - from real-world objects.
  - Example: "Prepare biscuits", "Brew tea"
- A **protocol** is a detailed procedure to obtain some output *thing* (be it
  an item, a measurement, or a combination of) from zero or more inputs.
  It might contain some generic instructions, and it may be flexible in some
  aspects.
  - Example: for the "Brew tea" experiment, we might have more than one
    protocol, such as "Wash cups" (which takes dirty cups and makes them
    clean), "Heat up Water" (which takes water and creates hot water), and
    "brew tea" (which takes hot water, clean cups and tea bags to make hot tea).
    These protocols might change slightly depending on the fine details of
    the experiment: for example with the same "Heat up Water" protocol we
    might decide on different temperatures, or different kinds of tea for
    "brew tea".
- A **realization** of an experiment is the same experiment with protocols
  without any potential variability.
  - Example: The "Brew tea" experiment might be realized into "Brew lemongrass black tea"
    by setting the water temperature to 90 degrees Celsius, using lemongrass and
    black tea leaves during the brewing process and brewing for 5 minutes.
- A **run** of a realization is an actual real event that took place when the
  steps of a realized experiment were carried out.
  As life is not perfect, each run might be slightly different due to
  variables potentially out of our control, be it due to unforseen
  circumstances or intrinsic variables.
  - Example: John ran "Brew lemongrass black tea" on the third of May, 2024 (we
    cannot ever re-create the third of May, 2024), but the electric kettle was
    broken so he had to use a saucepan to heat the water (in contrast to what
    the realized experiment detailed should be done).
    - The fact that John ran the experiment on that specific day is a variable
      out of our control: someone *has to* run the experiment and it must be
      done in *some* day, of course.
      The broken kettle is in our control, but accidents happen, so we must be
      prepared to record them.
- Each run (generally) produces one or more **measurements**.
  The collection of these measurements is our data.

You can see that the actual entity which produces real data is the run.
Every other level in this hierarchy also produces variables: our metadata.

This is the core of the Mimir method. When we think of a new project, we can:
- Define the goal of the project and give it a name;
- Define what experiments we need to run to achieve the project's goal;
- Define the protocols that make up the experiments that we need and compose
  them, or reuse old ones;
- Create realizations of the experiments (if we cannot use an old one);
- Run the realizations, writing down what variables we encounter during the
  run that we did not codify already in the previous steps;

Once we have the data produced by the run, we just need to
[label](/wetlab/sample_labelling.html) it and upload the text of the realized
experiment plus all of the unexpected variables that we have encountered during the run.
