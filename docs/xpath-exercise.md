# XPath exercise in oXygen


## Data
Download data from

Anne Baillot (ed.), "Briefe und Texte aus dem intellektuellen Berlin um 1800". Berlin: Humboldt-Universität zu Berlin. http://www.berliner-intellektuelle.eu/

- Go to https://www.berliner-intellektuelle.eu/about?de
- In section *Daten*, download `berliner-intellektuelle-manuscripts.zip`
- Unzip the folder (important!)
- Open `Brief001Boeckh.xml` in oXygen
- In oXygen menu toolbar, choose Project > New Project. A window will pop-up, check that the value of Project directory ends with `berliner-intellektuelle-manuscripts/xml` and click Create.

**Projects** are a way to organize your XML-related files. You can perform batch operations (such as validation and transformation) over sets of files and share your project settings and transformation scenarios. The project is safed with the extension `.xpr` in the Project directory.


## The XPath Search in the toolbar

You should have and 'XPath 2.0' toolbar in the upper-left of the oXygen editor, otherwise please ask. The toolbar contains:
– a dropdown menu on the left for selecting the version of XPath you are using
– a box in which to type xpath queries for the current file
– a setting dropdown menu enabling you to change options

When you do a search in oXygen it lists the hits in a window at the bottom of the editor. This contains a description, the XPath location, what file it is in, and location. Click on one of the results and you will be taken to that result. This can be an easy way to navigate through a large file. Notice what it lists as the 'Description' and that next to the heading it also lists how many results there are.

## Query a single file

Have a look at the open file, `Brief001Boeckh.xml`.

Imagine we are revising this transcription and we need to check all the unclear readings, encoded with the element `<unclear>`.

To obtain all unclear readings, type `//unclear` in the XPATH Search toolbar box. The results are 10 items.

To only obtain the number of results, use the `count` function, as follows: `count(//unclear)`. Note that we do not have access to each result anymore.

Type `//unclear` again to obtain the details of each result. Double-clicking on the first result, we see that the element carries three attributes. Look for the values of the attribute `@cert` (indicating the degree of certainty associated with the text). How to do it? The answer is at the bottom of the exercise, see Answer 1.

Now let's look for the values of the attribute `@reason`, instead of `@cert`. The mechanism is the same, but you have to specify a different attribute name.

Try restricting your search to the unclear passages with low certitude: `<unclear cert="medium">`. After trying yourself, double-check with Answer 2.

## Query multiple files
oXygen gives the possibility to change the scope of the XPath query. You can set the scope using the dropdown menu activated by the small document icon within the XPath Search toolbar box.

Change it to Project, to include all the XML files contained in the directory specified as the Project directory.

Now we want to know who are the senders of the almost 200 letters. Information about senders and receivers are encoded within the metadata, in the element `<correspDesc>`. Type `//correspDesc` to obtain the corresponding element in all files: the results are 182 items. This time, the left part of results panel is empty, because this element does not immediately contain text, but only other elements. We can anyway double-click on any line and observe the structure of `<correspDesc>`.

`<correspDesc>` contains two `<correspAction>`, one of type 'sent' and one of type 'received'. Let's restrict our query to only the 'sent' actions. Try yourself and then see Answer 3.

Now try to extract the names of the persons who sent the letter, encoded with `<persName>`. See answer 4.

Note that there are only 178 results, and not 182 as before. This means that in some cases there is no `<persName>` within the 'sent' `<correspAction>`. Want to know more? We can have a look only at those elements which do not contain `<persName>`. One way would be to query for `//correspAction[@type='sent'][not(persName)]` or `//correspAction[@type='sent'][not(descendant::persName)]` (the latter will also work for nested `<persName>`). Try it out in the XPath Search.

We can use the `contains()` function to refine our search. Imagine we want all the letters sent by Dorothea Tieck. We can use the following XPath query: `//correspAction[@type='sent']/persName[contains(.,'Dorothea')]`. Another way to obtain all the letters sent by Dorothea Tieck would be to filter on the value of the `@ref` attribute on the `<persName>`. The value corresponding to her is '#p0217'. Try it yourself, see Answer 5. The second approach is safer, because it would retrieve the result even if the name would have been spelled differently or abbreviated.



## More exercise on a single file
Imagine that we have access to the digitized source and we want to know in which page/file we can find this text. This information is encoded in the attribute `@facs` on the element `<pb/>`. See answer 6.




## Answers

1. `//unclear/@cert`
2. `//unclear[@cert='medium']`
3. `//correspAction[@type='sent']`
4. `//correspAction[@type='sent']/persName`
5. `//correspAction[@type='sent']/persName[@ref='#p0217']`
6. `//pb/@facs`






