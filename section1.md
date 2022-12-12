## Very short introduction to TEI

See [slides](docs/spadini_TEI_coffeeLecture.pdf).

## XML editors

- [oXygen](https://www.oxygenxml.com/)
- [Visual Studio Code](https://code.visualstudio.com/). How to use VSCode for [XML and TEI encoding](http://phc.uni.wroc.pl/interreg/w/losada/VSCode.html)

## Recap XML

*This section and the following extensively reuse the tutorials at https://teibyexample.org.*

### XML declaration

An XML document is introduced by the XML declaration:

```xml
<?xml version="1.0"  encoding="UTF-8"?>
```

The question mark `?` in the XML declaration signals that this is a processing instruction. The following bits state that what follows is XML which complies with version 1.0 of the recommendation and that the used character encoding is UTF-8 or Unicode. An XML declaration is optional, but can only appear as the first content of an XML file.

### Elements and attributes

```xml
<?xml version="1.0" encoding="UTF-8"?>
<document>
	<!-- paragraphs go here -->
	<paragraph number="1">Paragraph one of <title>an XML example</title>
	</paragraph>
	<paragraph number="2">Paragraph two of this example.</paragraph>
</document>
```

XML elements are delimited by start tags (e.g., `<document>`) and end tags (e.g., `</document>`). 

Additional information to these XML elements can be given in attributes, consisting of a name (e.g., `@number`) and a value (e.g., "1"). Attributes can only occur within the start tag of an element. In documentations, attributes are generally prefixed with the “at” sign, e.g., `@number`.

XML comments are delimited by start markers (<!--) and end markers (-->). Everything inside comments is ignored by XML processing software: it is said to be “commented out.”

### Well formed and valid
An XML document is well formed when it complies with the XML syntax. An XML document is valid against a schema.

### W3C standard
XML is a recommendation from the World Wide Web Consortium (W3C): https://www.w3.org/TR/xml/.

## Recap TEI

### General structure
A full TEI document consists of one single `<TEI>` element, which consists of two major components:

- `<teiHeader>`: an element containing all the metadata describing the document;
- `<text>`: an element containing the actual document.

```xml
<TEI xmlns="http://www.tei-c.org/ns/1.0">
	<teiHeader>
	<!---...-->
	</teiHeader>
	<text>
	<!--...-->
	</text>
</TEI>
```

This example, as any TEI text, is recognizable as a TEI text by the outermost `<TEI>` element, which is declared in the dedicated TEI namespace (http://www.tei-c.org/ns/1.0). 

In the previous example, the TEI namespace is declared as the “default” namespace, i.e., without any prefix. It could have been expressed equally as follows: 

```xml
<tei:TEI xmlns:tei="http://www.tei-c.org/ns/1.0">
	<tei:teiHeader>
	<!---...-->
	</tei:teiHeader>
	<tei:text>
	<!--...-->
	</text>
</tei:TEI>
```

Here, the namespace declaration `xmlns:tei="http://www.tei-c.org/ns/1.0"` on the `<TEI>` element binds the TEI namespace URI (http://www.tei-c.org/ns/1.0) to the namespace prefix `tei`. All descendant elements using that prefix before the actual element name belong to this namespace (e.g., `<tei:teiHeader>`).

It is possible to use elements from different namespace in the same XML document.

### TEI Header
The TEI header (`<teiHeader>`) is mandatory and contains descriptive meta-information about the document. The `<teiHeader>` minimally contains a description of the electronic file inside a `<fileDesc>`. The latter element consists of three mandatory components:

- the title statement (`<titleStmt>`), providing information about the title (`<title>`), author (`<author>`), and others responsible for the electronic text
- the publication statement (`<publicationStmt>`), providing publication details about the electronic text in a structured way or as prose inside a paragraph (`<p>`)
- a description of the source (`<sourceDesc>`), documenting bibliographic details about the electronic text’s material source (if any) in a structured way or in a prose paragraph (`<p>`)

```xml
<teiHeader xmlns="http://www.tei-c.org/ns/1.0">
	<fileDesc>
		<titleStmt>
			<title>The Strange Adventures of Dr. Burt Diddledygook:
			a machine-readable transcription</title>
			<respStmt>
			<resp>editor</resp>
			<name xml:id="EV">Edward Vanhoutte</name>
			</respStmt>
		</titleStmt>
		<publicationStmt>
			<p>Not for distribution.</p>
		</publicationStmt>
		<sourceDesc>
			<p>Transcribed from the diaries of the late Dr. Roy Offire.</p>
		</sourceDesc>
	</fileDesc>
</teiHeader>
```

### Text

The element `<text>` minimally contains the text body (`<body>`). The body contains lower-level text structures like paragraphs (`<p>`), or different structures for text genres other than prose: lines (`<l>`) for poetry, speeches (`<sp>`) for drama.

```xml
<text xmlns="http://www.tei-c.org/ns/1.0">
	<body>
		<p>For the first time in twenty-five years, Dr Burt Diddledygook decided not to
		turn up to the annual meeting of the Royal Academy of Whoopledywhaa (RAW). It was a 
		sunny day in late September 1960 bang on noontime and Dr Burt was looking forward 
		to a stroll in the park instead. He hoped his fellow members of the RAW weren't 
		even going to notice his absence.</p>
	</body>
</text>
```

Next to the `<body>`, a text can optionally contain front matter which may be encoded with `<front>`. Clear examples are title pages, headers, prefaces, or dedications. All back matter to a text, such as appendix, glossary, colophon, and others, may be grouped within `<back>`. Divisions `<div>` with a `@type` attribute are used to distinguish the different components of `<front>` and `<back>`, as in the following example:

```xml
<text xmlns="http://www.tei-c.org/ns/1.0">
	<front>
	<div type="dedication">
		<p>In memory of Lisa Wheeman.</p>
	</div>
	<div type="contents">
		<head>Table of Contents</head>
		<list>
			<item>I. The Decision</item>
			<item>II. The Fuss</item>
			<item>III. The Celebration</item>
		</list>
	</div>
	</front>
	<body>
		<p>For the first time in twenty-five years, Dr Burt Diddledygook decided not to 
		turn up to the annual meeting of the Royal Academy of Whoopledywhaa (RAW). It was a 
		sunny day in late September 1960 bang on noontime and Dr Burt was looking forward 
		to a stroll in the park instead. He hoped his fellow members of the RAW weren't 
		even going to notice his absence.</p>
	</body>
	<back>
		<div type="colophon">
			<p>Typeset in Haselfoot 37 and Henry 8. Printed and bound by Whistleshout,
			South Africa.</p>
		</div>
	</back>
</text>
```


### Renditional features

The TEI Guidelines define highlighting as “the use of any combination of typographic features (font, size, hue, etc.) in a printed or written text in order to distinguish some passage of a text from its surroundings” (TEI Guidelines, section [3.3.1 What Is Highlighting?](https://tei-c.org/release/doc/tei-p5-doc/en/html/CO.html#COHQW)). The generic element `<hi>` (highlighting) can be used with a `@rend` or `@rendition` attribute describing its appearance in the text.

```xml
<p xmlns="http://www.tei-c.org/ns/1.0">For the first time in twenty-five years, Dr Burt Diddledygook decided not to turn up to the annual meeting of the <hi rend="italic">Royal Academy of Whoopledywhaa</hi>
 (RAW).</p>
```

### Logical and semantic features

Highlighted words or phrases in a text are commonly distinguished from their surroundings for a reason. Only a thorough understanding of the text and the language can lead to a correct identification and interpretation. The underlying semantics may be encoded with more specific elements than the generic `<hi>` element. Highlighting is commonly used to render the following logical and semantic features:

- Emphasis (`<emph>`), foreign words (`<foreign>`), and other linguistically distinct uses (`<distinct>`) of highlighting.
- The use of quotation marks in the representation of speech and thought (`<said>`), quotation (`<quote>`), cited quotation (`<cit>`), words or phrases mentioned (`<mentioned>`), and words or phrases for which the author or narrator indicates a disclaiming of responsibility (`<soCalled>`).
- Technical terms (`<term>`), glosses (`<gloss>`), or documentation of XML elements, attributes, and classes.

```xml
<p xmlns="http://www.tei-c.org/ns/1.0"><q>Plenty of options</q>, he thought, sat on a bench 
and opened the book he had taken from the Whoopledywhaaian National Library. It was titled 
'While thou art here', by Sir Edmund Peckwood. While reading the first sentence, his placid 
expression turned to a certain <foreign>je ne sais quoi</foreign>: <quote>For the first 
time in twenty-five years, Dr Burt Diddledygook decided not to turn up to the annual 
meeting of the Royal Academy of Whoopledywhaa.</quote></p>
```

### The physical structure
*This section and the following reuse extensively materials from https://www.digitalmanuscripts.eu/digital-editing-of-medieval-texts-a-textbook/*

To represent the physical structure of the documents you encode, the TEI offers a series of “empty” ou “milestone” elements: instead of wrapping a whole passage of text, they simply mark the beginning of a new quire, page, etc. The advantage of empty elements is that they will not interfere with the markup representing the logical structure of the document. That way, a
paragraph can start on one page and finish on another one withou causing any overlapping of the markup.

The `<gb>` (gathering beginning) element can be used to mark up the limits of different quires or gatherings constituting a manuscripts. The `<pb>` (page beginning) element, marking the beginning of pages, is probably the most widely used of this series. Within the space of a page, `<cb>` (column beginning) and `<lb>` (line beginning) can be used to mark up the limits of
columns and lines on the original document, respectively.

### Editorial interventions: normalisation

Editors have the possibility to point (and optionally offer a correction for) apparent errors in the text. The [element `<sic>`](http://www.tei-c.org/Vault/P5/3.0.0/doc/tei-p5-doc/en/html/ref-sic.html) in TEI, “(Latin for ‘thus’ or ‘so’) contains text reproduced although apparently incorrect or inaccurate,” as in the following example:

```xml
I’ve been <sic>hear</sic> before...
```

Editors may also choose to offer a regularised version of the text alongside its original spelling. The [`<choice>` element](http://www.tei-c.org/Vault/P5/3.0.0/doc/tei-p5-doc/en/html/ref-choice.html), which “groups a number of alternative encodings for the same point in a text,” can be used to combined the original version with the corrected or regularised one, as in the following example:

```xml
I’ve been <choice>
	<sic>hear</sic>
	<corr>here</corr>
</choice> before...
```

When the spelling, grammar and punctuation rules of the source differ from the current ones, it might be desirable for the editor to offer a readble version more accessible to modern readers, as in the following example:

```xml
The <choice>
	<orig>tragicall</orig>
	<reg>tragical</reg>
</choice>
<choice>
	<orig>historie</orig>
	<reg>history</reg>
</choice> of Hamlet Prince of <choice>
	<orig>Denmarke</orig>
	<reg>Denmark</reg></choice> by William <choice>	
	<orig>Shake-speare</orig>
	<reg>Shakespeare</reg>
</choice>
```

### Notes
The most explicit form of textual annotation is the addition of notes to the text using `<note>`. This element serves for the encoding of all kinds of annotations, whether they are already present in the text or supplied by the editor; whether they appear as block notes in the main text area, at the foot of the page, at the end of the chapter or volume, in the margin, or in some other place. The `@type` attribute can be used to distinguish between different types of annotations.

```xml
<p xmlns="http://www.tei-c.org/ns/1.0">'Plenty of options', he thought, sat on a bench and
opened the book he had taken from the Whoopledywhaaian National Library
<note n="1" place="foot" type="authorial">The National Library of Whoopledywhaa was founded in 1886 with the acquisition of the library of the late King Anthony.</note>.
It was titled 'While thou art here', by Sir Edmund Peckwood
<note type="editorial" resp="#EV">The manuscript reads 'Petwood'.</note></p>
```

### Global attributes

There are 11 global attributes, available on any TEI element. They are organized in the classes and subclasses `att.global`, `att.global.rendition`, `att.global.responsibility`, `att.global.source`.

`@xml:id` provides a unique identifier for an element.

`@n` provides a number or other label for an element, which does not need to be unique within the document.

`@xml:lang` indicates the language of an element using a “tag” generated according to BCP 47.

`@xml:base` provides a base URI reference with which applications can resolve relative URI references into absolute URI references.

`@xml:space` signals an intention about how white space should be managed by applications. It accepts values `default` or `preserve`.

`@rend`
	indicates how the element was rendered or presented in the source text.
	
`@style`
	contains an expression in some formal style definition language which defines the rendering or presentation used for this element in the source text.
	
`@rendition`
	points to a description of the rendering or presentation used for this element in the source text.
	
`@cert`
	signifies the degree of certainty associated with the intervention or interpretation.
	
`@resp`
	indicates the agency responsible for the intervention or interpretation.
	
`@source`
	specifies the source from which some aspect of this element is drawn.


## Exercise

```txt
Perhaps she did not speak of it, even for an instant,
with the physicist she has been seeing for several weeks,
and who has brought her the offprint of an article titled
"On symmetry in physical phenomena, the symmetry of an
electric field and of a magnetic field." The brochure
is dedicated "To Mlle Sklodowska with the respect and
the friendship of the author P. Curie."

Together they speak enormously, but about physics  or
themselves.
```
Based on: “Marie Curie, So Honorable Woman”, in *The collected stories of Lydia Davis*

1. Encode this text as two paragraphs of prose.
2. Indicate that they are written in English.
3. Indicate the number of the paragraph.
4. Encode all the names with the element [`<persName>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-persName.html).
5. Encode “P.” as an abbreviation with its corresponding expansions ('Pierre').
6. Encode the title of the brochure, using the element [`<title>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-title.html).
7. Encode the dedication using [`<q>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-q.html).


## Reuse materials from
- Melissa Terras, Edward Vanhoutte, and Ron Van den Branden. *TEI by Example*. https://teibyexample.org (accessed December 2022)
- *Digital Editing of Medieval Texts: A Textbook*, https://www.digitalmanuscripts.eu/digital-editing-of-medieval-texts-a-textbook/  (accessed December 2022)






