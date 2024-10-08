# Choosing file formats
> [!NOTE]
> This section talks about which file formats to use.
> If you don't know what file formats are, or need a refresher, you can read the [Formats, Serialization and Deserialization section](../formats_serde.md).
> This section assumes you know everything covered in that section.

The choice of file formats is important.
We must choose formats that are future-proof and accessible, meaning:
1. They have an encoding that is widely popular and that can be interpreted easily in the future;
2. They can be read by non-proprietary (i.e. free and open-source) software, so that there are as little barriers as possible to its usage;
3. They are easily human-readable with as little serialization as possible.

These considerations generally limit our possible file formats:

## Numeric data
Tables of numbers should be saved in [comma separated values, or `.csv`](https://en.wikipedia.org/wiki/Comma-separated_values).

A `csv` file looks like this:
```
header_1,header_2,header_3
value,value,value
value,value,value
"a value with a comma, inside",value,value
```
Each line is a row in the table, and the first one is often reserved for the heading of the table.
Note that some programs use the first column as row names: avoid this, instead saving the row names as a proper column (with a useful name, like `sample_names`).

A `tsv` or tab-separated values file is similar to a `csv` file, but uses tabs instead of commas. It looks like the text below when opened with a text editor:
```
header_1	header_2	header_3
value	value	value
value	value	value
a value with a comma, inside	value	value
```

There is no obvious advantage or benefit of choosing `tsv` rather than `csv` or vice-versa, but the `csv` format is generally more common.
For this reason, the `csv` format should be preferred over `tsv`.

> [!IMPORTANT]
> Often, TSV files are often saved with the extension `.txt` (as is "plain text").
> This is an old convention. Please save TSV files with the `.tsv` extension, not `.tsv`.
> If you can, change the extensions from `.txt` to `.tsv`, or even better convert them to CSV and save them as such.

A `csv` has [MIME](https://en.wikipedia.org/wiki/Media_type) type of `text/csv`.

#### Formats to avoid
Do *not* use the following formats, whenever possible:
- Excel (`.xlsx` and `.xls`, `application/vnd.ms-excel`);
    - They rely on a proprietary software and are hard to read programmatically.
    - Data should never contain data analysis steps, so nothing that cannot be represented in pure `csv` should be included in the format.

## Images
To store images, the [Tagged Image File Format (`TIFF`)](https://en.wikipedia.org/wiki/TIFF) format should be used.
Multiple images in the same series (e.g. for a time-lapse) should be saved in the same `TIFF` file as a stack of images in the correct order.

If the `TIFF` file format cannot be used, an alternative is [Portable Network Graphics (PNG, `.png`)](https://en.wikipedia.org/wiki/PNG).

TIFF images should adhere to the "basic TIFF" specification, with no extensions to the format. This is mostly a technical detail, but it is important for the long-term accessibility of the image data.
TIFF images have the [MIME](https://en.wikipedia.org/wiki/Media_type) type of `image/tiff` and PNG have `image/png`.

#### Formats to avoid
Do *not* use the following formats, whenever possible:
- JPEG (`.jpg`, `image/jpeg`);
  - JPEG images are compressed with a *lossy* compression, meaning that some image data is lost when the JPEG file is saved.
    JPEG images also do not allow for transparency.

## Documentation
All documents (i.e. forms, certificates, and other bureaucratic items) that are **exclusively meant for human consumption** may be saved as `.pdf` files.
All other documentation should be saved as [plain-text (`.txt`)](https://en.wikipedia.org/wiki/Plain_text) or at most as [markdown (`.md`)](https://en.wikipedia.org/wiki/Markdown) files.

Plain text is both humanly readable and machine readable.
If additional formatting is required (e.g. titles, bold/italics, links, etc...), markdown is a broadly applicable way to add text formatting while still essentially writing plain text files.

Slides and presentations should be saved as `.pdf`.
If videos or animations must be included in the presentation, prefer the [Open Document Format (`.odf`)] instead of PowerPoint-like formats (e.g. `.ppt` or `.pptx`).

> [!WARNING]
> Be careful that ODF files, and in some cases PDF files, may distort or wrongly encode some features of the presentation if converting directly from PPT to ODF.
>
> Always check the presentations before depositing.

#### Formats to avoid
- Do not use PowerPoint formats (`.ppt`, `.pptx`), as they are proprietary.

## Multimedia
Audio files should preferably be saved as raw [Waveform Audio File Format (WAW, `.wav`)](https://en.wikipedia.org/wiki/WAV).
WAV files are uncompressed and simple to read, and may be processed by most audio-processing software.

As a (better) alternative, the [Broadcast Wave Format (BWA, confusigly also `.wav`)](https://en.wikipedia.org/wiki/Broadcast_Wave_Format) can be used, although consumer software to convert to and from it is relatively rare.
Yet another alternative is the [Free Lossless Audio Coded (FLAC, `.flac`)](https://en.wikipedia.org/wiki/FLAC).

Video files should be saved as either [MP4 (`.mp4`)](https://en.wikipedia.org/wiki/MP4_file_format) or [WebM (`.webm`)](https://en.wikipedia.org/wiki/WebM), the latter being one of the few file formats that is distributed with a permissive license (BSD) by Google and is therefore not proprietary.

Be careful of the compression of the output video files, which in some cases may be lossy.

#### Formats to avoid
- Do not use `.gif` files, as they have very inefficient compression that generally does not reduce file size much but causes very bad quality losses.
  Additionally, they do not support transparency.

# Further considerations
## Compressing
Files should be compressed if larger than a few megabytes.
Image files in particular should always be compressed before archiving.

The recommended compression schema is `gzip` (with the `.gz` file extension).
Each file should be compressed on its own, but groups of tightly-related files may be compressed together as a `tarball` (with the `.tar` file extension) first, and then compressed with `gzip` (resulting in a `.tar.gz` file).
If you do, consider creating uncompressed metadata describing the contents of the tarball.

Other possible compressions are 7Zip (`.7z`) or ZIP (`.zip`).

## Plain text encoding
All plain-text files (e.g. `.txt`, `.csv` and source code) should be [`UTF-8` encoded](https://en.wikipedia.org/wiki/UTF-8).
In the modern day, this is the default for most computers.

Another compatible file format that may be used for simple files is `ASCII`, but `UTF-8` is still preferable.

# For developers
It might be useful to check file formats programmatically.
A way to do this is with the [JHOVE](http://jhove.openpreservation.org/) tool, that extracts a number of metadata information from many different file types.
It can also check if the file is well-formatted and valid.

Another possibility is [FIDO](https://openpreservation.org/tools/fido), available as a Python library and command-line tool.

# Specific cases
Some files have specific formats, and require special care.
If you have such files, consider the archival aspects above and choose a format other than those shown here.
If you can, contact a data expert for advice.
