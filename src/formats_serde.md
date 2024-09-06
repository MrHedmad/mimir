# Formats, serialization and deserialization
This section will cover very technical concepts in a very non-technical way.
If you know something about computer science, how files are read and manipulated by machines, you can safely skip this section.
If you are not familiar on how that works, read on.

How do machines represent information? With "information" I mean everything a computer can handle: the words on the webpage you are reading now, the numbers in spreadsheets, the pixels on a chart, etc..
You probably know that computers "think" in binary, with ones and zeroes - bits.
This is true: the hardware that is able to do the computations required to display the pixels on the screen can only work with 0s and 1s.
A lot of work, research and effort goes in the manipulation of these long lists of zeroes and ones to obtain the pictures on screens of all devices.
For the rest of the book, and to understand what "machine readability" is, it's useful to know with an eagle-eye overview what some of this work is: in particular, we will talk about serialization, deserialization and file formats.

## Serialization and Deserialization
Physically, files are long strings of zeroes and ones saved in the hard-drives of computers.
For example:
```
0110100001100101011011000110110001101111
```
might be a small piece of a file. Of course, we cannot work with this: we see files as collections of letters, words, tables, images, not obscure lists of bits.

Enter - serialization. With "serialization" we mean a process that takes data in one form and generates some new object that we can better understand.
For instance, [ASCII](https://en.wikipedia.org/wiki/ASCII) is a pre-formed table of bits to convert them to letters.
For instance, the series of bits `01101000` is equal to the letter "h".
I know that the bits above can be serialized to letters using the ASCII table to obtain the word "hello".
In technical terms, the bits were serialized to "hello".

The opposite of serialization is *deserialization*, converting a humanly-readable object into a form that is better understood by computers or that can be better stored on disk.

## File formats
We said before that we serialized the bits into the word "hello" trough the usage of the ASCII table.
Technically, we say that the series of bits - in other words, the file - was in the ASCII format, or "encoding"[^1].
When we serialize something, we use the proper method to move from a representation of a lower level (i.e. bits) to a representation in a higher level (i.e. words).

The extension of file (the `.txt` after `some_file.txt`) is useful to know at a glance the format of the file that it refers to: in this case, a text file (that can use ASCII, for instance).
Note that there is no obligation for the extension to be truthful.
I can rename a picture from `cat.png` to `cat.txt` with no issues: the file is still a picture of a cat.
However, by default the computer will now try to open `cat.txt` as a text file, and will probably fail (or show weird, random text chracters it has obtained by applying the serialization rules for text to the image).

There can be more than one layer of file formats, not just from bits to words.
For instance, take a Webpage (.html).
I will not delve in the technicalities of webpages, but suffice to say that a single wepage is just a text file
Some of the files that make up the Word document are text files with words.
To read these, the computer serializes the bits to words, just like we saw before.
However, the resulting files are in yet another format: HTML.
Html files are just text files with a specific structure. Here's an example:
```xml
<!doctype html>
<html>
<head>
    <title>Example Domain</title>

    <meta charset="utf-8" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
</head>

<body>
<div>
    <h1>Example Domain</h1>
    <p>This domain is for use in illustrative examples in documents. You may use this
    domain in literature without prior coordination or asking for permission.</p>
    <p><a href="https://www.iana.org/domains/example">More information...</a></p>
</div>
</body>
</html>
```
Why the file is structured this way is not important right now: simply notice that the patterns in file file are somewhat regular (notice the indentation, the tags with specific names, etc)...

The format of this file, HTML, is another layer of encoding: we can serialize this file into another one, more accessible by humans, through additional programs: in this case, the web browser[^3].

[^1]: We can think of serialization as the "decoding" of the secret message that was "encoded", deserialized, with the ASCII table. This is why we use the term "encoding" in this context.
[^2]: If you right click on a webpage and "show source", you will see the (very complicated) text file underneath the webpage that you see.
[^3]: Nobody would call this step "serialization", but rather "rendering" or something along those lines. However, I wanted to be clearer on what serialization actually does, and how it is linked with file formats.
