# Workshop. TEI put into practice

Universität Basel, 13.12.2022

Research and Infrastructure Support (RISE)

Elena Spadini


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

### Reference
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
			<title>The Strange Adventures of Dr. Burt Diddledygook: a machine-readable transcription</title>
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
		<p>For the first time in twenty-five years, Dr Burt Diddledygook decided not to turn up to the annual meeting of the Royal Academy of Whoopledywhaa (RAW). It was a sunny day in late September 1960 bang on noontime and Dr Burt was looking forward to a stroll in the park instead. He hoped his fellow members of the RAW weren't even going to notice his absence.</p>
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
		<p>For the first time in twenty-five years, Dr Burt Diddledygook decided not to turn up to the annual meeting of the Royal Academy of Whoopledywhaa (RAW). It was a sunny day in late September 1960 bang on noontime and Dr Burt was looking forward to a stroll in the park instead. He hoped his fellow members of the RAW weren't even going to notice his absence.</p>
	</body>
	<back>
		<div type="colophon">
			<p>Typeset in Haselfoot 37 and Henry 8. Printed and bound by Whistleshout, South Africa.</p>
		</div>
	</back>
</text>
```





## Reuse of
https://teibyexample.org/






