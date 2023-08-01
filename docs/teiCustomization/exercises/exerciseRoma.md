---
output:
  pdf_document: default
  word_document: default
  html_document: default
---
	
# Exercise: TEI customization with ROMA


## Before you start
In this exercise, you will use Roma, a web tool available from the TEI web site. You will need access to the internet and a web browser (Firefoxm Chrome, Opera, etc.) and once you have your schema you will also need an XML-aware editor to use it (e.g., oXygen).

These instructions only cover part of Roma’s functionality. They describe the steps needed to

- select modules,

- delete elements,

- delete attributes, 

- make an attribute mandatory, and

- constrain its values.

These instructions do not cover some other capabilities of Roma, including adding elements; changing an element’s class membership, contents, or description; changing an attribute's permitted values (other than to a closed list of values); changing the language of Roma interface itself or of the elements & attributes generated.


## Getting started

In this exercise, we will start from an existing customization and we will edit it. 

- The customization is in your Materials folder (download from the course homepage).

- Now, let's go to Roma: when you are on-line, point your favorite web browser to <https://roma.tei-c.org/>.

- You should get to the Roma - ODD Customization home page. 

- As said, we will edit an existing ODD: go to the 'Upload ODD' tab and upload the file **myCustomization_before.odd**, that you can find in the Materials folder.

- Click Start!

## Metadata
After clicking Start, it should take you to the Settings page. Here you can enter basic metadata of your customization:

- For the **title** choose a meaningful (for you!) name, like 'My first TEI customization' or 'TEI customization for X Workshop'.

- For the **identifier**, it’s a good idea to avoid characters that may confuse operating systems, like spaces, slashes, back-slashes, colons, etc. You can use something like 'myTEI' or 'TeiCustomizationWorkshop'. This will also be the filename of the ODD and of the schema.

- We will not create new elements, so the **Customization Namespace** is not relevant and can be left as it is.

- Leave the **prefix** as it is.

- Choose the **languages** you prefer. 

- The **author** is you.

Press the Customize ODD button (the name of your customization appears on the top bar).

## Modules

We can remove entire modules (corresponding to chapters of the Guidelines) if we do not need them. In this exercise, remove the module Dictionaries:
- start typing on the right 'dict'. An element should appear, which belong to the module Dictionaries. You can see that on the right.
- Click on the X symbol next to the name of the module, (dictionaries). A window will pop up, saying something like "This will remove the entire module from your customization. Are you sure you want to continue?". Click Yes.
- Notice that the symbol next to the Dictionaries module is now a +. We can click there if we need to add again that module.

## Elements 

It is often the case that the modules chosen contain many more elements than are desired.
We are starting from a large customization, so let's remove some elements that we know we will not use.

- Sort the list of elements by module. To do this, you should have selected the button Elements on the top left and and click the sorting button (with the up and down arrows) By module.
- As in this exercise we are using a letter, the Namesdates module will certainly be useful. But not all elements of it. Scroll down until you arrive to the Namesdates module, the name of the modules appear on the right. You now should see the elements addName, affiliation, age, etc.
- To remove the elements climate, offset and terrain (for example), uncheck the box to the left of their names.

Done!

## Attributes

Imagine that we want to make sure that for each person the date of birth is specified (so that later you can put all the data on a beautiful timeline). In order to do this, we want the attribute '@when' to be mandatory on the element 'birth'.

Also, as we are very confident about the information we have about the birth of persons, we don't need to specify how certain we are; we can therefore Excude the attribute '@cert' (that signifies the degree of certainty associated with the intervention or interpretation)

- Scroll up to the element birth and click on it, then on Attributes. A list of attributes is displayed, organised by their classes.

- Find the attribute '@cert' (belonging to the class att.global.responsibility) and remove it with the X symbol.

- Then, find the attribute '@when' (belonging to the class att.datable.w3c) and click on the pencil symbol next to it for editing. Change the usage to Required.

Done!


## Save your ODD file

From the Download menu on the top right, select Customization as ODD. The generated file can be saved with an extension .odd or .xml: it is still a XML document, but you might find convenient to use the extenstion .odd to distinguish it from the rest.

Remember to **always** save your ODD file, or you will have to go through all this work again anytime you want to modify your customization.

## Generate the documentation

From the Download menu on the top right, select Documentation as ... and the format of your choice.

## Generate the schema
To generate an output schema select the *Schema* tab. Here you can change the desired schema language of the schema that Roma will generate and download when you click Submit. For our purposes, leave the default, RELAX NG compact syntax. 

## Test your customization

To test your customization, go to oXygen and associate the schema to a TEI document: 

- in oXygen, open the TEI document vanGoghLetters_001_forExercise.xml, which is also in the Materials folder.

- choose menu 'Document' > 'Schema' > 'Associate schema'. Select the schema you just downloaded. Leave the rest as it is and press OK. 

- The schema is now associated (you can see it at the top of your TEI document)

- Try to validate the document: you should have two errors, because we change the behaviour of the element birth. They can be fixed by removing the attribute @cert and by adding the attribute @when.

- Now try to use the element 'entry'. oXygen will prompt you an error 'Element "entry" not allowed anywhere'! Why? Because we deleted the module Dictionaries.

You can keep playing with what you changed in the schema (try to use the element climate for example) and see what happens.

To check the differences between the schema before and after your customisation, you can now associate the schema myCustomization_before.rng, which is also available in the Materials folder. Everything should validate, even if you remove the attribute @when or use the element climate.


## Still have time ... ?

Try to constrain the list of values for an attribute.

---

This exercise reuses tutorials at

- <http://www.wwp.northeastern.edu/outreach/seminars/_current/handouts/exercise-roma.xhtml> Licence: CC-BY-NC-SA

- <http://www.tei-c.org/Guidelines/Customization/use_roma.xml> Licence: CC-BY



## About this exercise

Title: TEI customization with ROMA

Author: Elena Spadini

Reusing materials published by TEI-C and Women Writers Project, as specified above.

Licence: [CC-BY-NC-SA 4.0]<https://creativecommons.org/licenses/by-nc-sa/4.0/>
