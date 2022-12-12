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






## Reuse materials from

This tutorial extensively reuse materials from:

- Melissa Terras, Edward Vanhoutte, and Ron Van den Branden. *TEI by Example*. https://teibyexample.org (accessed December 2022)
- *Digital Editing of Medieval Texts: A Textbook*, ed. by Marjorie Burghart. https://www.digitalmanuscripts.eu/digital-editing-of-medieval-texts-a-textbook/  (accessed December 2022)


## License
See [readme](readme.md).
