<style>

</style>



TEI Customization: ODD and schema
========================================================
author: Programme doctoral en études numériques. Formation 'Textes et éditions numériques'
date: Université de Lausanne, 25-26 avril 2019
autosize: true


TOC
=========
- Have we met before ?
- TEI Customization
- ODD (One Document Does it all)
- TEI bricks
- Customizing the TEI



CHAPTER 0
=========

# Have we met before?



Well formed and valid
========================
<br/>
Remember?
<br/><br/>
- An XML document is well formed when it complies with the XML syntax
<br/><br/>
- An XML document is valid against a **schema**
<br/><br/><br/><br/><br/><br/>


=======================
<img src="images/teiall.png">


A schema
========================
<br/>
## defines **vocabulary** and **grammar**
<br/>
## which elements and attributes are to be used, where and how 
<br/>
for example, which element you can use inside another element, which values you can give to an attribute


Chapter 1
======================
# TEI Customization


Associate schema to a document
=======================

<img src="images/teiall.png">

***
<br/>
## Schema helps you
Suggestions, code completion, pop-up descriptions ...
<br/><br/>
## Schema controls you

Red square, error messages, invalid document ...




===============

The good news is
<br/>

## that you can create or adjust the schema


TEI customization
===================
<img src="images/tei_areas.jpg">

***

Customization of the TEI is motivated by two important things:

- the **diverse disciplinary needs and concerns** of the TEI community

- The goal of reconciling the need for a **common encoding language** with the need for **expressiveness**

See Guidelines <a href="https://www.tei-c.org/release/doc/tei-p5-doc/en/html/index.html" target="_blank">chapters</a>


Community-maintained TEI schemas
=========================
<br/>

- **tei\_all** 
- **tei\_lite** (light and basic encoding)
- **tei\_drama** (performance texts)
- **tei\_speech** (speech and spoken texts)

<small>
More at <http://www.tei-c.org/Guidelines/Customization/>
</small>
<br/><br/><br/>
Have you met them before?


Community-maintained TEI schemas
=========================
<br/>

- **tei\_all** 
- **tei\_lite** (light and basic encoding)
- **tei\_drama** (performance texts)
- **tei\_speech** (speech and spoken texts)

<small>
More at <http://www.tei-c.org/Guidelines/Customization/>
</small>
<br/><br/><br/>
Have you met them before? <br/>Yes, they are available in **oXygen** through its TEI framework.


Recap (theory)
========================
<br/>
## A schema defines **vocabulary** and **grammar** 
#### which elements and attributes are to be used, where and how 

# &#8679;

#### it represents in a structured and formalized way
## your **understanding of** and **approach towards** 
## the text to be encoded (scientific choices)

Recap (practice)
=========================
<img width="40%" src="images/teiall.png">

What happens if you change the schema?

**Exercise**: take the last TEI document you worked with yesterday (or download it from the materials folder) and change the schema from 'tei_all' to 'tei_lite'. Is the green square still green?




Chapter 2 
=============================
# ODD (One Document Does it all)


============================
## A TEI Customization
## comes in the form of / is referred as 
## an ODD (One Document Does it All) 
<br/>

- TEI document (that is a XML document)
- schema (for the machine)
- documentation (for the user)

#### E.g. **tei\_myCustomization.xml** or you can change the extension to **tei\_myCustomization.odd**


The ODD tree
=============
<img src="images/odd-tree.png">


========================
<img src="images/odd_stack.png">
<small>[A view of the whole system](http://www.wwp.northeastern.edu/outreach/seminars/_current/presentations/basic_odd/basic_odd_simple_tutorial_13.xhtml)</small>
<br/><small><small><small><small>From: Syd Bauman, Julia Flanders, and the Women Writers Project</small></small></small></small>


========================
<img src="images/tei_odd_customization_detail_iconed.png"/>
<small>[TEI customization under the hood (in a nutshell)](http://www.wwp.northeastern.edu/outreach/seminars/_current/presentations/customization/customization_overview_tutorial_12.xhtml)</small>
<br/><small><small><small><small>From: Syd Bauman, Julia Flanders, and the Women Writers Project</small></small></small></small>



Chapter 3
===============
# The TEI bricks


The TEI is ...
===========
<br/><br/>
not only a [big list of elements](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/REF-ELEMENTS.html) ...
<br/><br/><br/>
They are structured in modules and classes

Elements
==============
<br/>
<img src="images/tei_as_lego.png">

***

+/- 550 elements and a very large number of attributes!

Grouped into:

- **modules**

- **classes** 


Modules = lego kits
===================
left: 30%
<br/>
<img src="images/TEI_modules_simple.png">

***
<br/>
- Basic and specialized kits

- Each module corresponds to [a **chapter** in the TEI guidelines](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/index.html)

- Each element belongs to one and only one module


The class system
============================
<br/><br/>
### A class groups elements or attributes that **behave in the same way** and that tend to **go in the same place**.
<br/><br/>
- Classes of elements are named model.*the class* (e.g. **model.global**)

- Classes of attributes are named att.*the class* (e.g. **att.global**)


Examples
============================
<img width="150%" src="images/tei_classes_conceptual4.png">


The class system
=========================
<br/><br/>
Exercise time

<br/><br/>
3 mins !


Chapter 4
================
# Customizing the TEI


=====================
## Customization options
<br/>
- Select modules
- Remove unnecessary elements
- Add new elements or attributes
- Change element or attribute names
- Constrain attribute values
- Manipulate functional groupings of elements (classes)
- Produce an internationalized version of the TEI


==================================
left:40%

## 1. Create the ODD 
<br/>
- manually writing it
- using web app [Roma](https://roma2.tei-c.org/)

***

============================
left:40%

## 1. Create the ODD 
<br/>
- manually writing it
- using [Roma](https://roma2.tei-c.org/)

***

## 2. Generate the schema
(ODD ---> RNG, RNC, DTD, etc.)

- web app  [Roma](https://roma2.tei-c.org/)
- oXygen's built-in stylesheets
- Oxford University's [OxGarage](https://oxgarage2.tei-c.org/) multi-transformer
- roma: a command-line tool
- Complete list with links and instructions at WWP [ODD Processors page](http://www.wwp.northeastern.edu/outreach/seminars/_current/presentations/customization/customization_overview_tutorial_13.xhtml)


Let's go to Roma!
=========================
<img src="images/teiRoma.png"/>


Recap
==========================

- ODD Customization reflects your scientific choices, reinforces consistency, documents your work


Recap
==========================

- ODD Customization reflects your scientific choices, reinforces consistency, documents your work

- For creating an ODD Customization <--- manipulate (delete, add, change) the TEI bricks (elements, attributes, modules, classes)



Recap
==========================

- ODD Customization reflects your scientific choices, reinforces consistency, documents your work

- For creating an ODD Customization <--- manipulate (delete, add, change) the TEI bricks (elements, attributes, modules, classes)

- From an ODD Customization ---> generate documentation and schema


Recap
==========================

- ODD Customization reflects your scientific choices, reinforces consistency, documents your work

- For creating an ODD Customization <--- manipulate (delete, add, change) the TEI bricks (elements, attributes, modules, classes)

- From an ODD Customization ---> generate documentation and schema

- A TEI document should be well formed (XML rules) and valid (schema rules)


Credits and links
==============
<small>

These slides reuse materials from

- the TEI-C resources, and in particular
  - <http://www.tei-c.org/Guidelines/Customization>

- the Women Writers Project educational resources, and in particular
  - <http://www.wwp.northeastern.edu/outreach/resources/customization.html>

  Please visit these links if you want to know more.
</small>

==========

<br/><br/>
Formation ['Textes et éditions numériques'](https://www.unil.ch/doc-digitalstudies/home/menuinst/activites-du-programme/textes-et-editions-numeriques.html)

Université de Lausanne, 25-26 avril 2019

<small>Elena Spadini, *TEI Customization: ODD and schema*</small>
<br/>
<small>Licence: [CC-BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)</small>

