# Using protocols
In the previous section, we talked about some definition of what projects, experiments and protocols are.
In this section I will walk you trough an example of such a structure, and how it's implemented in the day to day.

Imagine a project to "Have tea with the others".
To attain the goal of this project, you would need to run the experiments "Prepare biscuits" and "Brew tea".
For the "Brew tea" experiment, we might have more than one protocol, such as "Wash cups" (which takes dirty cups and makes them clean), "Heat up Water" (which takes water and creates hot water), and "infuse water" (which takes hot water and tea leaves to make hot tea).
These protocols might change slightly depending on the fine details of the experiment: for example with the same "Heat up Water" protocol we might decide on different temperatures, or different kinds of tea for "infuse water".

When we are ready to use the "Brew tea" experiment, we need to realize it.
Every variable that was flexible in the various protocols (such as the kind of tea in the "Infuse Water" protocol) must be "locked in" at this stage.
The resulting realized experiment has to be deposited in some way, such as online.
in this case, the experiment might be realized into "Brew lemongrass black tea" by setting the water temperature to 90 degrees Celsius, using lemongrass and black tea leaves during the brewing process and brewing for 5 minutes.

Once we have a realized experiment, we can run it.
During the run something unexpected might happen, so we need to record it.
For example, John ran "Brew lemongrass black tea" on the third of May, 2024 (we cannot ever re-create the third of May, 2024), but the electric kettle was broken so he had to use a saucepan to heat the water (in contrast to what the realized experiment detailed should be done).
The fact that John ran the experiment on that specific day is a variable out of our control: someone *has to* run the experiment and it must be done in *some* day, of course.
The broken kettle is technically in our control (we could have aborted the experiment at that point), but accidents happen and samples, reagents and time might be expensive, so we must be prepared to record such incidents as we run our experiments.

You can see that the actual *thing* that produces real data is the run.
Every other level in this hierarchy also produces variables: our metadata.
The metadata is recorded in both the realized experiment and the notes that we make during the run regarding unexpected or intrinsic variable.

This is the core of the Mimir method.
When we think of a new project, we can:
- Define the goal of the project and give it a name;
- Define what experiments we need to run to achieve the project's goal;
- Define the protocols that make up the experiments that we need and compose them, or reuse old ones;
- Create realizations of the experiments (if we cannot use an old one);
- Run the realizations, writing down what variables we encounter during the run that we did not codify already in the previous steps;

It's possible that it's much easier to draft the protocols needed in a realization of the experiment rather than the more generic, "abstracted" protocols that are readily reused.
If this is the case, take the time to consider your realized protocol and break it up later, "taking out" all variables that might reasonably be changed often.
This can potentially be done at a second time.

Once we have the data produced by the run, we just need to [label](/wetlab/sample_labelling.html) it and upload the text of the realized experiment plus all of the unexpected variables that we have encountered during the run.
