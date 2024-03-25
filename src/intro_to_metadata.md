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
"biological gender") or what the subject reported as the gender they
identify with?

Such a clarification is metadata *about* metadata and it's just as important.
This example was very simple, but imagine more complex metadata,
especially if it's referring to highly technical features,
such as tumor grading (what does "grade III" really mean?), taxonomic
classification, and other non-self-explanatory fields.

It's important to keep in mind when writing metadata that other people
(including yourself in the future) need to be able to read and understand
the metadata as much as they need to read and understand the data itself.

### Metadata ontologies
This is why metadata ontologies exist.
They hold all of the definitions of what metadata actually means,
as well as the structure it should take.
Following such a metadata ontology is essential to be understood by
yourself, others and chiefly computer programs which are powerful but
not as intelligent as humans when it comes to interpreting (meta)data.

Recall [the FAIR principles](./what_FAIR.md): to be Findable, it should be
possible for a computer program to search for and find our data.
This is primarely done by searching through the metadata, not the data.
For instance, if we had a metadata field for "organism", one could look up
all experiments done on some specific organism (but pause and think about
how such a field should be structured. Would "human" and "gorilla" be ok?
or should it be the full taxonomix name, like "homo Sapiens" instead?) with a
simple search.

This sort of automatic lookup is impossible to do without a specific onthology
to refer to.

At the time of writing (start of 2024), it's still not clear what onthology
to use for what data at a global level.
There are some attempts are creating such an onthology
(such as https://www.researchobject.org/), and there are many entries for
specific kinds of data (many of which are deposited in https://FAIRsharing.org),
but - as you might think - the task is harduous and it make take some time
before a recognized, followed standard is found.

This is the reason why this book exists: in the absence of a standard for
data and metadata structure, type and quality, it's still possible to create
local standard to follow.
This has the benefit of making your data FAIR, at least for yourself, and
internally consistent to some quality standard of your choosing.
If a global (meta)data onthology does eventually emerge, it is much easier
to migrate locally FAIR data to this standard rather than non FAIR data
(indeed, annotating old data with metadata might be even impossible).

## Metadata formats
We said that metadata is data, so it follows that all the formats of data
can also be found for metadata.
However, metadata has some common characteristics that narrow the possible
types and formats that it can take:
1. Metadata is usually made up of text. Think of the labels for the example
   above.
2. Metadata should be both human and machine readable, although being machine
   readable is chiefly important.
   - In particular, being *easily* machine redable is important.
3. Metadata should be retrieavable indipendently of the data it describes,
   due to the Accessibility principle (in particular,
   [the A2 point](https://www.go-fair.org/fair-principles/): "Metadata are
   accessible even when the data is no longer available").
4. The structure of metadata should be shared by all data that has to be
   searched through together.
   - This is important! Say that you need to search through all the data that
     your research group/deparment/university generates.
     If all measurements were annotated with a different format, what program
     could reliably search through them?

This leaves a few formats that are textual, encapsulated and easily machine
readable as likely candidates to store metadata:
- [Comma separated values](https://en.wikipedia.org/wiki/Comma-separated_values),
  `csv` and, less preferrably, its flavours (such as `tsv`);
- [Javascript Object Notation](https://en.wikipedia.org/wiki/JSON), JSON;
- Other formats that can be easily [transpiled](https://en.wikipedia.org/wiki/Source-to-source_compiler)
  into JSON, such as [YAML](https://en.wikipedia.org/wiki/YAML) or
  [TOML](https://en.wikipedia.org/wiki/TOML).

JSON and CSV files are most fitting for metadata.
If you have not encountered these formats before, I suggest you look up what
they are before continuing to read.

The JSON format is convenient when there are many fields with little data
in each field. A CSV metadata is instead more capable of capturing a lot
of information for a few fields, for instance clinical metadata of the
patients from which the real data is sourced from.

For example, we might have the following JSON to represent an ecological
measurement:
```json
{
  "metadata_link": "https://doi.org/00000.00000.0",
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

