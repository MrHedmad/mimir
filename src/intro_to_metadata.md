# What is metadata?

μετά, in Greek, means "after" or "beyond", and as an adjective means "transcending".
In modern English, meta- as a prefix also means "self-referential".
Meta-data is self-refential data, or *data about data*.

> [!NOTE]
> Immediately, we hit an interesting point: if metadata is data about data, it is, itself, more data.
> It's important to keep in mind that everything that you can say for data you can also say for metadata.
> This includes the potential for *data about metadata*, or meta-metadata, as we will see below.
> Sometimes I will use the form (meta)data to refer to both data and metadata.

Imagine that I come up to you, and, without a word, hand you a piece of paper.
You read it:
```
1.57, 1.42, 1.50, 1.55, 1.52, 1.48, 1.60, 1.54, 1.38, 1.48
```
You are probably confused at this point[^1].
What do this numbers mean?

Let's take a moment to consider the numbers of themselves.
We say that these numbers are *data*. The definition of "data" is very complicated, but let's simplify it here and think about data as a representation (be it numbers, words, images, etc...) of some aspect of reality.
This helps, somewhat. The numbers represent something about the real world, but what?

Enter, metadata. I hand you another piece of paper, which tells you that these numbers are people's heights.
This helps your understanding: `1.57` is the representation of my height, in some units.
However, a lot of questions might have come up in your mind:
- What is this unit of measure?
- What was used to measure the heights?
- Who made the measurements?
- Who were the people that got measured?

All of this information - this *meta*data - is essential to understand the data.
Without it, the numbers above are just that: a series of meaningless numbers.
There is no data without metadata, and they are tightly linked together.

You will have handled metadata before: even just the title of your files is
metadata: they describe what is inside the file.

A large part of FAIR data is to write meaningful, standardized and practical
metadata alongside your data.
The machine or human that reads your metadata can then quickly understand
what the data is all about, up to the fine details of it.
It follows that - unlike my pieces of papers - data thusly described is generally *useful*.

## Representing metadata
Metadata is represented in much the same way as regular data.
Consider again the numbers above.
When working with metadata it's useful to give each data point an identifier (ID):
```
A     B     C     D     E     F     G     H     I     J
1.57, 1.42, 1.50, 1.55, 1.52, 1.48, 1.60, 1.54, 1.38, 1.48
```
Once we can univocally refer to each data point, we can create a new representation, a new piece of data, with the metadata for each point:
```
subject_id  gender
A           Male
B           Female
C           Male
D           Female
E           Male
F           Male
G           Female
H           Female
I           Male
J           Female
```
We can use the identifiers to cross-reference the data and metadata, so that we know that the person that has identifier "A" is 1.57 meters tall, and has gender of "Male".
We will see that identifiers are very important in many aspects of data handling: they are the "handles" that we can grip to move, link, and break apart data.
Note that identifiers are metadata.
They are described in [the next section](identifiers.md).

For tabular data such as this one, where values are ordered in columns and rows, columns of data are often represented as rows of metadata.

## Down the metadata rabbit hole
We can go one step further: metadata *about metadata*.
This "meta-metadata" might refer to the definitions of the metadata.
For instance, is the gender above what was assigned at birth (i.e. "biological gender") or what the subject reported as the gender they identify with?

Such a clarification is metadata *about* metadata and it's just as important.
This example was very simple, but imagine more complex metadata, especially if it's referring to highly technical features, such as tumor grading (what does "grade III" really mean?), classifications, debated definitions (e.g. "gender") and other non-self-explanatory fields.

It's important to keep in mind when writing metadata that other people (including yourself in the future) need to be able to read and understand the metadata as much as they need to read and understand the data itself.
Additionally, it would be nice to coordinate in some way, so that when we say "gender", everyone gives to that word the same meaning.
This also allows the development of automated tools that can understand what "gender" means without ambiguity, so that the data can be used correctly.

## Machine readability
Recall [the FAIR principles](./what_FAIR.md): to be Findable, it should be possible for a computer program to search for and find our data.
This is primarely done by searching through the metadata, not the data.
For instance, if we had a metadata field for "organism", one could look up all experiments done on some specific organism with a simple search.
But pause and think about how such a field should be structured.
Would terms such as "human" and "gorilla" be ok? or should it be the full taxonomic name, like "homo Sapiens" instead? If so, in which form ("h. Sapiens", "Sapiens, homo", etc...)?
Consider that to a program, the terms "h. Sapiens" and "homo Sapiens" are as different as "gorilla" and "fish".
To make our data machine-readable, the form of our metadata must be standardized in some way.

### Metadata ontologies
A way to standardize the meaning of metadata is through the usage of Ontologies.
They hold all of the definitions of what the (meta)data actually means, as well as the structure it should take.
Following such a metadata ontology is essential to be understood by yourself, others and chiefly computer programs which require no ambiguiity and a lot of standardization when it comes to interpreting (meta)data.

At the time of writing (start of 2024), it's still not clear what ontology to use for what data at a global level.
There are some attempts are creating such an ontology (such as [researchobject.org](https://www.researchobject.org/)), and there are many entries for specific kinds of data (many of which are deposited in [FAIRsharing.org](https://FAIRsharing.org)),
but - as you might think - the task of making everyone agree on what ontology to use is harduous and it will take some time before a recognized, followed standard for most data types is found and widely adopted.

For the purposes of Mimir, we will sidestep the problem altogether.
In the absence of a standard for data and metadata structure, type and quality, it's still possible to create local standards to follow.
If well designed, such metadata can be (automatically) ported to new metadata formats if and when they emerge.
We will therefore be "selfish": your data will be FAIR primarily for yourself, and it will be internally consistent to some quality standard of your choosing.
If a global (meta)data onthology does eventually emerge, it is much easier to migrate locally FAIR data to this standard rather than non FAIR data (indeed, annotating old non-FAIR data with new metadata might be even impossible).

## Metadata formats
We said that metadata is data, so it follows that all the formats of data can also be found for metadata.
However, metadata has some common characteristics that narrow the possible types and formats that it can take:
1. Metadata is usually made up of text. Think of the labels for the example above.
2. Metadata should be both human and machine readable, although being machine  readable is chiefly important.
   - In particular, being *easily* machine redable is important. This means using file formats that can be easily read by anyone. More on file formats later.
3. Metadata should be retrieavable indipendently of the data it describes, due to the Accessibility principle (in particular, [the A2 point](https://www.go-fair.org/fair-principles/): "Metadata are accessible even when the data is no longer available").
4. The structure of metadata should be shared by all data that has to be searched through together.
   - This is important! Say that you need to search through all the data that    your research group/deparment/university generates.
     If all measurements were annotated with a different format, what program could reliably search through them?

This leaves a few formats that are textual, encapsulated and easily machine
readable as likely candidates to store metadata:
- [Comma separated values](https://en.wikipedia.org/wiki/Comma-separated_values), `csv` and, less preferrably, its flavours (such as `tsv`);
- [Javascript Object Notation](https://en.wikipedia.org/wiki/JSON), JSON;
- Other formats that can be easily [transpiled](https://en.wikipedia.org/wiki/Source-to-source_compiler) into JSON, such as [YAML](https://en.wikipedia.org/wiki/YAML) or [TOML](https://en.wikipedia.org/wiki/TOML).
- [Resource Description Framework (RDF)](https://en.wikipedia.org/wiki/Resource_Description_Framework), a very powerful network-like format mainly used for metadata on the web, but is complicated to explain and not easily used by most applications.

RDF, JSON and CSV files are most fitting for metadata.
This book is not a manual for formats, but some more information is available in the [Formats, serialization and deserialization](formats_serde.md) section.

The JSON format is convenient when there are many fields with little data in each field.
CSV is instead more capable of capturing a lot of information for a few fields, for instance clinical metadata of the patients from which the real data is sourced from, with identifiers linking them together (as we saw above).
RDF is usually the most complex of the three, usually used for meta-metadata and generally high-level metadata.
It can, however, be applied at any level, with the proper onthology.

> [!NOTE]
> Since RDF often requires a surrounding framework (such as loading some RDF-schema or [OWL](https://en.wikipedia.org/wiki/Web_Ontology_Language) on the web at a fixed [IRI](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier)), we will focus on mostly schemaless JSON or CSV metadata, although it might not be optimal.

For example, we might have the following JSON to represent an ecological
measurement:
```json
{
  "deposited_in": "https://doi.org/00000.00000.0",
  "author": {
    "full_name": "John Snow Doe",
    "orcid": "0000-0000-0000-0001",
    "email": "jhon.doe@biology_department.org"
  },
  "title": "Number of species in fields",
  "description": "The number of plant species in different fields from expert examination was measured by sampling ten random one-meter squares per field.",
  "objects": [
    {
      "file_name": "my_data.csv",
      "file_format": "csv",
      "column_description": {
        "observation_id": "The unique ID of the observation",
        "field_size": "The size of the field, in meteres squared",
        "species_number": "The total number of different species found in the field",
        "species_density": "The average number of different species per squared meter",
        "field_longitude": "The longitude of the centroid of the field",
        "field_latitude": "The latutide of the field",
        "field_altitude": "The altitude of the field, in meters above sea level"
      }
    }
  ]
}
```
Take a moment to consider if you think that this metadata is complete.
Do you understand precisely what was done? Do you think the metadata is lacking?
Or maybe you think it has too much information.
Think about the structure of the metadata. Can such a template be reused in
other, perhaps largely different experiments? What would you change to make
it more flexible?

Here are some comments on this metadata example which you may or may not have considered:
- Who (did) John Doe work for when they collected the data?
  - This information might be relevant to a sociologist, for example, or
    to check for any conflicts of interest.
- When was this data collected?
  - With the fast changes in climate, when the measurement was done is
    tremendously important;
- A variable is in the description ("Ten random one-metere squares") but it's
  not encoded in the rest of the metadata as a findable field;
  - Perhaps someone might be interested in looking for effects of changing the
    number of samples areas, or their size, in measures such as this one.
- The `species_density` field is redundant if we added the above measure as
  a (meta)data.
- Where is the file described in the metadata located?
  - If we obtained ONLY this metadata file, we would not be able to locate the
    file anywhere.
- Is "Snow" a second name or part of the surname of the author? Is "Doe" the
  given name or the surname?
  - While this might be easy to spot for names from your culture, imagine the
    same situation for names from cultures unknown to you.
  - The author ID, as included here, is very helpful to determine actually who
    this author is.

Some comments might seem pedantic, but remember that if they are not recoded
at the moment of data creation, they might be lost forever, making the data
useless if they are ever needed.

While it's impossible to record every potential variable that is relevant for
the measurement (a large chunk of statistics would not exist if that was the
case), it is important to take the time to think of comments like the ones above
before depositing the data (and forgetting about it).

[^1]: And I disappear immediately in an ominous way.
