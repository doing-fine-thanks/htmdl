<!--- META:header 
author: Logan H. G. Davis
date: 9/4/25
-->
# htmdl
### A Tool for Scholarly Yak Shaving

`htmdl` (or Hyper Text MarkDown Language) is a tool-set for compiling [Markdown](https://daringfireball.net/projects/markdown/) document to HTML in a more "scholarly"[^1] format. 

Though numerous tools exist for the general task of of converting markdown to HTML (such as [Pandoc](https://pandoc.org)), many remained too generic for my use-case and building around them would result in just as much work (for a far more brittle tool) as writing it from scratch. 

As someone working in academia, I have specific styling and formatting requirements for my writing and general-markdown is, well, _too general_. `htmdl` has been made with a very specific set of tags, styles, and options in mind (with a few escape hatches for the edge cases I neglected to see when making the tool). 

## Tool Requirements and Philosophy:
 
Handle text formatting of paragraphs, headers (`h1-3`), subtitles, block quotes, citations, single & double column documents, figures, and call-outs.  

This tool draws inspiration from (at least) 2 sources: [tufte-css](https://edwardtufte.github.io/tufte-css/) and [gwern.net](https://gwern.net/about). The main principles I will highlight here are:
 
 - __clear and accessible html structures:__ not everyone can use dynamic apps with resource intense Javascript, so minimizing the dependencies on those tool helps converse energy and increase accessibility for those who use screen readers. 
 - __understanding the difference between links and citations:__ A lot of markdown tools assume `anchor tags` accomplish the same goal as citations. This is misunderstanding: links always take users away from the document they are reading, citations allow for additional context to a reader while staying "in the document." Of course citations _can_ be used to offer links to explore, but that is a subset what they can do.
 - __prefer side notes, default to end notes:__ webpages are not print and they _can_ do things print media struggles with. There are, of course, instances of sidenotes in printed media.[^2] But webpages can support them without needing to worry about paper sizes, blank space, or printer constraints. When possible (wide screen, single column documents) should prefer to use sidenote citations. 
 - __allow for printing:__ HTML should prioritize printed formatting as much as it prioritizes mobile and desktop reactivity. Though the web can do things print cannot, so too can print do difficult (or impossible) to do on the web.

This tools supports a subset of markdown based on my own usage and needs:

|type          | notes                                                                                   |
|--------------|-----------------------------------------------------------------------------------------|
| _italics_    | using \_ notation                                                                       |
| __bold__     | using double \_ notation                                                                |
| headers      | 1 through 3, if you need any more than than, consider restructuring your document).[^3] |
|`code`        | colored with [pygments](https://pygments.org)                                           |
| talbes       | using \| notation                                                                       | 
| citations    | using `[^1]` notation (examples in the document)                                        | 
| block quotes | using double-space notation (examples in the document)                                  | 
| figures      | TBD


## To Use:

This document is both documentation and a test of the tool. To test the tool, run it on this very file:

```bash
# for single column documents
$ uv run htmdl --file README.md --output test.html

# for double column
$ uv run htmdl --file README.md --output test.html -double-column
```


<!--- META:footnotes -->
[^1] I say "scholarly" and what I mean is more formal/in line with style guides for academic journals. 
[^2] Logan, find this example...
[^3] Generally speaking, I have seen technical documentation trying to architect itself _in and through_ the prose that explain it. The point of an object's documents are to _simply_ its structure around some particular reading of it. Restricting headers helps limit the impulse to add hierarchy to an otherwise linear document. For more see "Sections and headings" [here](https://edwardtufte.github.io/tufte-css/).
