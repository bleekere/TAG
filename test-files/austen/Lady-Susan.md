# Lady Susan (Pierpont Morgan Library, NY)

**Objective**: encode the relationship between the manuscripts as linguistic structures (words, phrases, etc.) and as physical support (notebook)

### General characteristics of material
- novela of letters, originally written into bound quarto notebook
- documentary encoding
- virtual reunification of Austen's holograph manuscripts 
	- conservation history
	- material state

### Capture with encoding
- Austen's particularities of spelling, paragraphing, punctuation, etc.; defined in the metadata and referenced in the text:
	- long ```S``` (unicode?)
	- ampersand ```&```
	- hyphenation ```::``` or ```-```, etc.
	- dashes (long, short, very long)
	- underlined text
	- quotes and quotation marks
	- distinct spelling
	- abbreviation
- structure of text: 
	- two hierarchies: physical structure of document and narratological structure of text. Which data in which hierarchy?
	- front/body/back
	- line- and page breaks 
	- paragraphs
	- indentation (four different indentations in _Lady Susan_: short-indent, indent, indent1, indent2)
	- page containing two letters
- hand shifts (person who writes and instrument of writing), rewritings, deletions and additions
- hyphenation in insertions, to make sure that they correspond with the linebreaks in the original/deleted part (in XML with milestones)


### Declaration of tags (based on KLT excerpt)

**page**  
Description: editorial page numbering, which may differ from authorial page numbering

- has (alpha)numeric annotation
- can be contained by ```book``` or ```volume``` or ```quire``` , etc.
- can contain ```pagenumber```, ```title```, ```salute```, ```p```, ```s```, ```capital```, ```dash```, ```rend```
- dominates ```l```
- cannot directly contain text characters

**p**  
Description: paragraph

- possible attributes ```indent```
- can contain ```del```, ```add```, ```capital```, ```w```,   
- should contain ```l``` 
- dominates ```l```, ```dash```
- is dominated by ...
- can be contained by ```page```
- can be proceeded or followed by ```salute```

**line**  
Description: indicates a _topographic_ line in the document (so not verse, which is marked up with ```l```)

- can contain ```rend```, ```w```, ```capital```, ```emph```, ```rend```, ```del```, ```add```, ```hyphen``` 
- should contain alphanumeric characters
- dominates ```dash```
- is dominated by ```page```, ```salute```
- attributes: ```indent```

**w**  
Description: represents a grammatical (not necessarily an ortographic) word

- should contain ```hyphen```, alphanumeric characters 
- can contain ```line```
- dominates ```hyphen```


| | page | p | line | w | hyphen | letter | page number |
|---| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| page |  [not allowed] | is contained by | is dominated by  | is contained by | is contained by | is contained by | is dominated by |
| p | contains | [not allowed] | is contained by | is dominated by | is contained by | dominates| [not allowed]
|line | dominates | contains | [not allowed] | is contained by | is contained by | dominates | dominates |
| w | contains | dominates | contains | [not allowed] | is dominated by | dominates | dominates |
| hyphen | contains | contains | contains | dominates | [not allowed] | dominates | dominates |
| letter | contains | is dominated by | is dominated by | is dominated by | is dominated by | [not allowed] | [not allowed] | 
| page number | dominates | [not allowed] | is dominated by | is dominated by | is dominated by | [not allowed] | [not allowed] |

**NB**. In this matrix, domination does not necessarily imply requirement. For instance, a ```page number``` dominates a ```line``` but a ```line``` does not require a ```page number``` as a parent (it could also have a ```page``` as a parent).




**pagenumber**  
Description: authorial page numbering

- attributes: ```rend```
- should contain: ```l```, alphanumeric characters
- is contained by ```page```


**rend**  
Description: attribute with value that refers to the physical or material structure of the document

- can contain attributes ```place```
- cannot be empty; should contain attribute with alphanumeric value
- annotations: ```direct```
- is dominated by ```pagenumber```, ```title```, ```del```, ```add```, ```emph```, ```s``` (basically, almost every tag)
- can be contained by ```l```




#### Data-centric hierarchy (physical structure of document)

- page / pagenumber
- line
- del and its "rend"-attributes
- handnotes / hand shifts

#### Text-centric hierarchy (narratological structure of text; particularities of Austen)

- letter (perhaps something like ```<div type=letter>``` or ```[div [type}letter{]}```)
- title
- rend (such as  "place"-attribute)
- indent
- distinct spelling
- sentence (s)
- dash
- salute
- paragraphs (p)
- capital
- hyphen
- dash
- emph
- word (w)