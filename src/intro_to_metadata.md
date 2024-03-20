# What is metadata?

μετά, in Greek, means "after" or "beyond", and as an adjective means "transcending".
In modern English, meta- as a prefix also means "self-referential".
Thus, meta-data is *data about data*.

For example, say that someone is measuring how tall people are.
The dataset might be a series of numbers:
```
1.57, 1.42, 1.50, 1.55, 1.52, 1.48, 1.60, 1.54, 1.38, 1.48
```
Each representing the height of one of your subjects.

However, a lot of questions might have come up in your mind:
- What is the unit of measure?
- What was used to measure the heights?
- Who made the measurements?
- Who were the people that got measured?

All of this information - this *meta*data - is essential to understand the data.
Without it, the numbers above are just that: a series of meaningless numbers.

You will have handled metadata before: even just the title of your files is
metadata: they describe what is inside the file.

A large part of FAIR data is to write meaningful, standardized and useful
metadata alongside your data.
The machine or human that reads your metadata can then quickly understand
what the data is all about, up to the fine details of it.

## Representing metadata
Metadata is represented in much the same way as regular data.
Consider the numbers above. When working with metadata it's useful to give each
data point an ID:
```
A     B     C     D     E     F     G     H     I     J
1.57, 1.42, 1.50, 1.55, 1.52, 1.48, 1.60, 1.54, 1.38, 1.48
```
Once we can univocally refer to each data point, we can create a new string
of numbers with the metadata for each point:
```
A     B       C       D     E     F       G       H     I       J
Male, Female, Female, Male, Male, Female, Female, Male, Female, Male
```
As you can see, the structure of the data and metadata are very similar.
This is an intrinsic characteristic of metadata: metadata *is* data, and
therefore it's represented and handled in much of the same way.

## Down the metadata rabbit hole
We can go one step further: metadata *about metadata*.
This "meta-metadata" might refer to the definitions of the metadata.
For instance, is the gender above what was assigned at birth (i.e.
"biological gender") or what the subject reported as the sex they
identify with?

Such a clarification is metadata *about* metadata and it's just as important.
This example was very simple, but imagine more complex metadata,
especially if it's referring to highly technical features,
such as tumor grading (what does "grade III" really mean?), taxonomic
classification, and other non-self-explanatory fields.

It's important to keep in mind when writing metadata that other people
(including yourself in the future) need to be able to read and understand
the metadata as much as they need to read and understand the data itself.

## Metadata ontologies
This is why metadata ontologies exist.
They hold all of the definitions of what metadata actually means.
Following such a metadata ontology is essential to be understood by
yourself, others and chiefly computer programs which are powerful but
not as intelligent as humans when it comes to interpreting data.

