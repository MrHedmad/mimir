# What is FAIR data?

In 2016, [an article](https://doi.org/10.1038/sdata.2016.18) was published
outlining "The **FAIR** guiding principles for scientific data management
and stewardship".
In the paper, the many authors outline what FAIR data is, why it was
invented, and why it is useful.
It's a highly recommended read: if you have the time, please stop reading
this book and read the article above (or at this DOI, if you cannot click
links: `https://doi.org/10.1038/sdata.2016.18`).

With FAIR data we mean data that is:

- **Findable**: you can actually find FAIR data.
  This is both for your locally-saved data (so that you can no longer say
  "Oh, yes, it's in a hard drive somewhere...") and for online datasets
  uploaded to data repositories.
  It also covers data labelling: when you get a hold of FAIR data you
  should also know what the data is all about, including:
  - What it is describing, meaning the thing that was measured;
  - How it was sourced, meaning the instrument or technique used on the thing
    that was measured;
  - Who generated the data and when it was generated;
  - Why the data was originally gathered;

  Such a large amount of [metadata](./intro_to_metadata.md) is usually stored
  in a separate file that is kept alongside the data that it is describing.
- **Accessible**: you can easily get, or know how to get, FAIR data.
  This might seem trivial, but not all data is born equal.
  Some data is sensitive, for example, pertaining to the health of patients
  or their sexual, political or otherwise secretive opinions.
  Such data should still be findable, but it might require additional levels
  of protection regarding how it can be *accessed*.
  This point is focused around such data: the ways of getting the data should
  be clearly stated (e.g. asking for permission, signing waivers, etc...).

  This point also covers the physical method of getting the data.
  For example, data might not be accessible if, to get it, one needs to send
  a carrier pigeon with a USB strapped to its leg to the recipient.
  The way to get the data needs to be standardized (e.g. the internet) and
  widely available to all.
- **Interoperable**: you can easily understand FAIR data once you have it.
  If you download a dataset only to discover that it is written in ancient
  cuneiform, you might not be able to understand it (unless you are an
  archaeologist, maybe).

  Data should be in a format that is understandable by all, not behind a
  paywall (did you ever consider that if you don't have the money to
  use Excel, you might not be able to read excel datasets?), and that is
  explained in detail (what does the `kplm` column mean?) so that everyone
  might understand the data even for many years to come.
- **Reusable**: you can easily use FAIR data for purposes other than the
  one it was originally made for.
  This point partially overlaps with the Interoperability, but covers the
  specific act of reusing the data.

  If you know in detail how the data was sourced, where it was sourced from,
  when it was taken and how it was recorded in the file, then you are able
  to use the data with confidence for other purposes.

  This is the ultimate goal and beauty of FAIR data. FAIR data is added
  with confidence to the global knowledge base and can be reused many
  times by different people for different purposes, including laboratories
  and individuals that might not have had the ways to gather it in the
  first place but that have creative uses for it.

You can read more about the more specifics of FAIR data and the characteristics
that it should have in both [the publication](https://doi.org/10.1038/sdata.2016.18)
and [in the go-fair website](https://www.go-fair.org).

The process of making data FAIR is known as FAIRification.

This book tries to convert these theoretical principles in a practical, day-to-day
workflow that every researcher can follow in their work in order to produce (more)
FAIR data for the researcher's own sake and the benefit of the public at large.
