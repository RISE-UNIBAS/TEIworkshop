## Logical and semantic features

Highlighted words or phrases in a text are commonly distinguished from their surroundings for a reason. Only a thorough understanding of the text and the language can lead to a correct identification and interpretation. The underlying semantics may be encoded with more specific elements than the generic `<hi>` element. Highlighting is commonly used to render the following logical and semantic features:

- Emphasis (`<emph>`), foreign words (`<foreign>`), and other linguistically distinct uses (`<distinct>`) of highlighting.
- Technical terms (`<term>`), glosses (`<gloss>`), or documentation of XML elements, attributes, and classes.
- The use of quotation marks for any purpose (`<q>`), in the representation of speech and thought (`<said>`), quotation (`<quote>`), cited quotation (`<cit>`), words or phrases mentioned (`<mentioned>`), and words or phrases for which the author or narrator indicates a disclaiming of responsibility (`<soCalled>`).

```xml
<p xmlns="http://www.tei-c.org/ns/1.0"><q>Plenty of options</q>, he thought, sat on a bench 
and opened the book he had taken from the Whoopledywhaaian National Library. It was titled 
'While thou art here', by Sir Edmund Peckwood. While reading the first sentence, his placid 
expression turned to a certain <foreign>je ne sais quoi</foreign>: <quote>For the first 
time in twenty-five years, Dr Burt Diddledygook decided not to turn up to the annual 
meeting of the Royal Academy of Whoopledywhaa.</quote></p>
```

## Citations and references

Passages of the edited text may be quoted explicitly or implicitly from other works. When the editor whishes to encode a quotation together with the source, the element `<cit>` can be used, which contains `<quote>` and a reference to the source, often encoded as `<bibl>` or `<ref>`, as in the following examples:

```xml
<div xml:id="mm01" type="chapter">
 <head>Chapter 1</head>
 <epigraph>
  <cit>
   <quote>
    <l>Since I can do no good because a woman</l>
    <l>Reach constantly at something that is near it.</l>
   </quote>
   <bibl>
    <title>The Maid's Tragedy</title>
    <author>Beaumont and Fletcher</author>
   </bibl>
  </cit>
 </epigraph>
 <p>Miss Brooke had that kind of beauty which seems to be thrown into
   relief by poor dress...</p>
</div>
```


```xml
Lexicography has shown little sign of being affected by the
 work of followers of J.R. Firth, probably best summarized
 in his slogan, <cit>
 <quote>You shall know a word by the company it keeps.</quote>
 <ref>(Firth, 1957)</ref>
</cit>
```

### Links to a bibliography

 Instead of providing the source reference in the `<bibl>` element within `<cit>`, it is also possible to create a bibliography and link to it. The bibliography can be put in the `<front>` or `<back>` elements, to separate it from the `<body>`.
 
 The TEI offers many options to encode a bibliography, here it is just an example:
 
 ```xml
 <bibl xml:id="Firth1957">
	<author>
	   <forename>John Rupert</forename>
	   <surname>Firth</surname>
	</author>
	<title>A synopsis of linguistic theory. Studies in linguistic analysis</title>
	<publisher>Blackwell</publisher>
	<pubPlace>Oxford</pubPlace>
	<date>1957</date>
 </bibl>
 ```
 
Once this is done, the previous citation can be encoded as following:
```xml
<cit>
   <quote>You shall know a word by the company it keeps.</quote>
   <ptr target="#Firth1957"/>
</cit>
```

or using `<ref>` when we want to add information to be processed or displayed to the link, for example:
```xml
<cit>
   <quote>You shall know a word by the company it keeps.</quote>
   <ref target="#Firth1957">Firth 1957, p. 11</ref>
</cit>
```

### Canonical references: the example of biblical quotations

Canonical references are identified not by bibliographic citation, like most literary sources, but by a short reference following rules defined by a scholarly community. That is the case of many religious texts as well as some classical works.

Biblical quotations are identified by canonical references, which take the form of a book name or abbreviation and, optionally, chapter and verse numbers. Despite their resemblance, they may vary considerably, because the book names are translated and abbreviated differently, various separators might be used (comma, colon) and there exist multiple editions and translations to which one might want to refer.

A simple encoding of a biblical reference is as following:

```xml
Unde in Genesim: <cit type="bible">
	<quote>In principio creavit Deus celum et terram.</quote>
	<ref>Gn 1:1</ref>
</cit>
```

We can refine this further, by using the attribute `@cRef` (canonical reference) on the element `<ptr>` and `<ref>`, as in the following example:

```xml
Unde in Genesim: <cit type="bible">
	<quote>In principio creavit Deus celum et terram.</quote>
	<ptr cRef="Gn 1:1"/>
</cit>
```

The referencing scheme used in the attribute `@cRef` should be explained in the element `<refsDecl>` (references declaration) within `<encodingDesc>` in the TEI header. The explanation might be in prose, as the following:

```xml
<refsDecl xml:id="biblicalCitations">
	<p>The <att>cRef</att> attribute of <gi>ref</gi> elements
	citing the Bible contain a canonical reference in one to three
	parts. The first part is an abbreviation for the name of the
	relevant book of the Bible, and it is the only mandatory one. The
	second part, preceded by a space, is a chapter number. The third,
	preceded by a colon, is either a single verse number, or a series
	of consecutive verses with the number of the first verse followed
	by a hyphen, followed by the number of the last verse. </p>
	<p>The following list of abbreviations has been used for the
	books of the Bible: Gn: Genesis; Exodus: Ex; Leviticus: Lv; [etc.]</p>
</refsDecl>
```

This information will be very useful to future users (including yourself) and current collaborators, but it cannot be processed automatically.

An alternative is to define a pattern that the canonical reference must match and how to automatically transform it into a valid URI. Several patterns can be defined, each in a `<cRefPattern>` element, using the two attributes `@matchPattern` (to define how canonical references are constructed), and `@replacementPattern` (to define how the different parts of the matching references must be transformed), as in the following:

```xml
<refsDecl xml:id="biblicalCitations">
	<cRefPattern matchPattern="(.+) (.+):(.+)"
	replacementPattern="http://vulsearch.sourceforge.net/html/
	$1.html#x$2_$3">
		<p>This pointer pattern extracts and references the <q>book,</q> <q>chapter,</q> and <q>verse</q> parts of a biblical reference pointing to a single verse, like “Gn 1:1”, and reconstructs a link to an online version of the biblical text.</p>
		<p>The following list of abbreviations has been used for the books of the Bible: Gn: Genesis; Exodus: Ex; Leviticus: Lv; [etc.]</p>
	</cRefPattern>
</refsDecl>
```

The replacement pattern will transform 'Gn 1:1' in http://vulsearch.sourceforge.net/html/Gn.html#x1_1.




## Reuse materials from

This tutorial extensively reuses materials from:

- Melissa Terras, Edward Vanhoutte, and Ron Van den Branden. *TEI by Example*. https://teibyexample.org (accessed December 2022)
- *Digital Editing of Medieval Texts: A Textbook*, ed. by Marjorie Burghart. https://www.digitalmanuscripts.eu/digital-editing-of-medieval-texts-a-textbook/  (accessed December 2022)


## License
See [readme](readme.md).
