# Identifiers
We will use identifiers troughout the book, so it's worthwile to make sure that some concepts are very clear from the get-go.

An *Identifier* or "ID" for short is an alphanumeric series of characters (like, a word), that refers to some item.
This item might be anything: a column in a spreadsheet, an idea, a textual note, a fossilized bone in a museum drawer, etc...

An ID is said to be *unique* if, in some context (i.e. the museum), that identifier refers to one, and one only, item.
For instance, in the Natural Sciences museum next to my department, the item with identifier "mammoth-bone-12" is a bone from a Mammoth, and only *that particular* bone from that particular mammoth.

We say that an ID is *globally* unique if, in addition to being locally unique as in the previous example, the ID refers to one item *in the whole world*.
For instance, another museum in Munich might have the same ID "mammoth-bone-12" for one of their own Mammoth bones.
Therefore, the ID "mammoth-bone-12" is not globally[^1] unique.

An example of a globally unique identifier is the URL to this webpage: `https://mrhedmad.github.io/mimir/identifiers.html` is an alphanumeric string that identifies this file *in the whole internet*.
There cannot be, on the internet, another page with the same identifier.
Indeed, every webpage has a globally unique identifier to it, and it's always visible in your browser.
If the ID were not globally unique, the web infrastructure would not be able to reliably find the one page that the URl refers to.

## Resovable identifiers
Say that I build a robot that, given an identifier for an item in a museum, will go and fetch it for me.
For it to work reliably, we would need to use an unique identifier for the whole search space that the robot works in, in this case the whole museum.
So, if I type in "mammoth-bone-12" in the museum next door, I'd obtain a mammoth bone on my desk.

The fact that we have the robot confers to the identifiers the property of being "resolvable": I have the ability to "use" the identifier (through the robot) to obtain the item that the identifier refers to.
This is very neat - in some way, the identifier *becomes* the item.

You might see where I am going with this.
The URL of web pages are resolvable: we can use them, through the internet infrastructure, to obtain the item that they refer to (the web pages).
In the strictest definition, an ID is resolvable if we can use it together with some infrastructure to obtain the item it refers to *or* some additional information about the same item (oftentimes the metadata for it).

Similarly, the path of a file in a filesystem (e.g. "C:\users\person\Desktop\my_file.xlsx") is a (locally) unique identifier to that specific file in that computer that is resolvable by using it in conjunction with some program (like File Explorer).

## What identifiers identify
Now that we know what an identifiers is, let's talk about what the item that it is identifying actually is.
As we said, the "item" might be a real-world item, a file (like a webpage), a concept (a word is a kind of identifier, don't you think?), etc...

In the context of data management, and Mimir in particular, identifiers are used to refer to things like experiments, protocols, people, real-world items (like vials, culture plates, flasks, samples), and basically anything that we need to describe.

Sometimes, we need identifiers for multiple levels of granularity.
For example, a culture plate is made up of different culture wells, each with spaces for one sample.
Oftentimes, we need to refer to both the plate as a whole ("the plate has been in the incubator for 10 hours")
So, we could say that the plate with ID "AAAA" has the samples with IDs "001", "002", ..., "348": the concept of "AAA" refers to the whole 348 samples, each with a more specific identifier.
In situations such as these it's useful to reflect the hierarchy in the identifiers themselves.
Let's take the plate example again: it would be much more convenient in practical terms to refer to sample 230 using an identifier like "plate_2-well_230", so we know from the get-go which plate the ID refers to.
This also lets use re-use the suffix "well 230" for other wells while still having unique identifiers.

Again, this is also exactly what the internet and your filesystem is doing: the URL "https://en.wikipedia.org/wiki/Microplate" is hierarchical in nature: the specific item (the webpage named "Microplate") is under the larger group of "wiki", which is itself in the larger container of "en.wikipedia.org"[^2].
You can see the same in the filesystem path: "C:\users\person\Desktop\my_file.xlsx" is a series of "containers" that get smaller and smaller until the final file is uniquely identified.

You can see that this method of using identifiers is very logical, and quite easy to use.

[^1]: If you're smart - and you are - you might have noticed thatthis  "globally" is not very well defined. This is because "globally" as used here is context-dependent. In the widest sense of the word, it mean "universally" unique: this ID is never used to refer to anything other than this one item in the whole universe. However, it's often unfair to use such a definition: if everyone in the world agrees that some ID refers to one, and one only, item, but Jane in accounting reuses it in their own catalogue to mean something else, we wouldn't care that much, and the ID would still be - for all practical purposes - globally unique. Imagine this "globally" to be flexible: for instance, we have one, large, integrated internet. Every URL in the whole internet is unique, and since we have just the one internet, we say that they are "globally unique" even though we might not be "universally unique" in the strict sense.
[^2]: "en.wikipedia.org" is yet again an hierarchical identifier: the largest domain is ".org", with all organization sites. In that container, "wikipedia" is one such site. Inside the "wikipedia.org", "en." is the English version of wikipedia.
