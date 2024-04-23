# Sample Labelling

Following the [protocol hierarchy](/prep/protocols.md) we can define what
labels on vials, items and files should look like:
```
                                         ID of the          potential file
              Experiment ID           actual ERI run    extension (for files)
                    ▲                        ▲                   ▲
                    │                        │                   │
    ┌───────┐  ┌────┴─────┐  ┌───────┐  ┌────┴────┐  ┌────┐  ┌───┴──┐
    │PROJECT├──┤EXPERIMENT├──┤ E.R.I ├──┤REPLICATE├──┤leaf├──┤[.ext]│
    └───┬───┘  └──────────┘  └───┬───┘  └─────────┘  └─┬──┘  └──────┘
        │                        │                     │
        ▼                        ▼                     ▼
    Project ID               Experiment         Unique sample-specific
                             Realization         string of text
                             ID
```

For example, assume we are studying how in ancient Asian tea was brewed.
We have found several tea leaves in a tomb and we are exploring the taste of
different tea-brewing techniques.
The overarching project is called Ancient Tea, and we decide that its ID will
be `ANTEA`.
It's possible to choose any string of text for a project ID, but it must be
universally unique. If we will do another tea-related project in the future,
we must call it something different than `ANTEA` (and possibly something that is
not easily confused with the original, like `ANTEA2`).

We think that we need an experiment for taste-testing brewed tea, so we define
the experiment with ID `tea_taste` for it.
We then define the protocols that we need:
- Wash liquid containers;
- Heat up liquid: heat up to *some degrees* *some liquid* using the
  electic kettle;
- Brew tea: place tea leaves in hot water and brew them for *some time*;
- Taste substance: use the standard questionnaire to profile the taste of
  *some substance*.

We can now realize the experiment for this specific tea-related case:
- Wash cups: to take dirty cups and wash them;
- Heat up water: to take water and cups, and make cups with hot water inside
  and heating it up to 85 degrees Celsius, to not destroy the fragile leaves;
- Brew tea: brew for 5 minutes while stirring every minute.
- Taste hot tea: to take brewed tea and taste-test it, and record the taste.
  We need an additional section of the questionnaire for the specific bitterness
  of the tea.

This is the *realization* of the experiment. In the realized experiment we
have defined all the variables that are kept purpusefully vague in the generic
experiment.
We assign an ID to the realization too, making sure that the combo `EXPERIMENT`
plus `E.R.I.` is unique. For example, we can use `tea_taste` plus `ancient`,
creating the string `tea_taste-ancient` for this realization of the protocol.

When we actually do the run, we give it an ID. Since this is the first time
that the `tea_taste-ancient` experiment is run in the context of the `ANTEA`
project, we give it the ID of `1`.

At this point, the full ID for this run is `ANTEA-tea_taste-ancient-1`.

## Labelling sigle data points
Each experimental run may have one ore more associated *things*, such as
samples, vials, measurements, etc...
It's important to label each item in the experimental run with a specific
*leaf*, a string with information about it.

How to structure leaves is less strictly defined as we need to allow for
as much flexibility as possible.
However, it's a good idea to continue with the principle of hierarchy.
To continue with the above example, say that we have brewed five different
cups (`cup_1` through `cup_5`) by taking different tea leaves aliquotes (black,
green). Each cup is then idependently tested by five different people 
(`taster_a`, `taster-b`, `taster_c`, etc...).
We might have leaf-ids that look like this:
```
black-cup_1-taster_a
black-cup_1-taster_b
black-cup_1-taster_c
        ...
black-cup_2-taster_a
black-cup_2-taster_b
        ...
green-cup_1-taster_a
        ...
green-cup_5-taster_e
```
Going from highest ranking ("type of tea") to intermediate ("cup number") to
the most fine ("taster ID").

Each measurement (in this case "how good the tea was") is associated with the
*full* ID. For example, `taster_e` has rated 5/5 the tea from cup 2 made from
black tea leaves.
Thus we record the score like this:
```
ID,                   score
black-cup_2-taster_e  5
```

## What to include in the leaf
The above "leaf" is made up of metadata.
However, how *much* metadata should be included in the leaf is up to the
experimenter. A leaf identifier should be primarily useful for the human
experimenter that is performing the run to know at a glance what is in this
vial, what this measurement is about, and/or things useful for housekeeping,
such as when the vial was collected or stored.

In any case, all metadata about the experiment should be saved in separate
metadata files, as detailed in [what is metadata?](/intro_to_metadata.md).
This means that the leaf might be as short and as obscure as a single number,
and as long as containing all metadata variables: as long as it is unique for
the specific *thing* it is describing, it is not really important what form
it takes.

