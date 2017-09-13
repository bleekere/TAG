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

**letter**   
Description: division of text, in this case a letter or an excerpt of a letter. In TEI a text division is often marked up like ```<div type="letter">``` but for this test-encoding of *Lady Susan* we created a proper ```letter``` element.

- should contain ```p```, ```title```, ```l```
- dominates ```p```, ```line```, ```w```, ```hyphen```, ```del```, ```add```, ```rend```, ```capital```, ```emph```
- is dominated by [nothing in this excerpt, but in theory it can be dominated by an overarching tag like ```text```
- cannot contain ```pagenumber```
- attributes ```n```

**pagenumber**  
Description: authorial page numbering

- attributes: ```rend```
- should contain: ```l```, alphanumeric characters
- is contained by ```page```

**rend**  
Description: refers to the physical or material structure of the document, takes ```place``` as attribute

- can contain attributes ```place```
- cannot be empty; should contain attribute with alphanumeric value
- annotations: ```direct```
- is dominated by ```pagenumber```, ```title```, ```del```, ```add```, ```emph```, ```s``` (basically, almost every tag)
- can be contained by ```l```

**text**  
Description: contains a single text of any kind, in this case a collection of letters

- Dominates: all other tags (```page```, ```p```, ```line```, ```s```, ```w```, etc).


## Matrix 1

| | page | p | line | w | hyphen | letter | page number |
|---| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| page |  [not allowed] | is contained by | is dominated by  | is contained by | is contained by | is contained by | is dominated by |
| p | contains | [not allowed] | is contained by | is dominated by | is contained by | dominates| [not allowed]
|line | dominates | contains | [not allowed] | is contained by | is contained by | dominates | dominates |
| w | contains | dominates | contains | [not allowed] | is dominated by | dominates | dominates |
| hyphen | contains | contains | contains | dominates | [not allowed] | dominates | dominates |
| letter | contains | is dominated by | is dominated by | is dominated by | is dominated by | [not allowed] | [not allowed] | 
| page number | dominates | [not allowed] | is dominated by | is dominated by | is dominated by | [not allowed] | [not allowed] |

**NB**. Dominance implies containment. In this matrix, domination does not necessarily imply requirement. For instance, a ```page number``` dominates a ```line``` but a ```line``` does not require a ```page number``` as a parent (it could also have a ```page``` as a parent).

Matrix 1 demonstrates that "containment" is a characteristic of nearly all elements. More interesting are the elements that dominate one another (in the words of MsMcQ "dominance is reserved for *meaningful* relations") and/or the elements that cannot be combined. Matrix 2 focuses on those. 

## Matrix 2


| | text | letter | page | pageNr | title | line | s | w |
| --- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| text | [n.a.] | is dominated by | is dominated by | is dominated by | is dominated by | is dominated by | is dominated by | is dominated by |
| letter | dominates | [n.a.] | contains | [n.a] | is dominated by | is dominated by | is dominated by | is dominated by |
| page | dominates | is contained by | [n.a.] | is dominated by | is dominated by | is dominated by |  is contained by | is contained by | 
| pageNr | dominates | [n.a.] | dominates | [n.a.] | [n.a.] | is dominated by | is dominated by | is dominated by |
| title | dominates | dominates | dominates | [n.a.] | [n.a.] | is dominated by | is dominated by | is dominated by |
| line | dominates  | dominates | dominates | dominates | dominates | [n.a.] | is contained by | is contained by | 
| s | dominates | dominates | contains | dominates  | dominates | contains | [n.a.] | dominates |
| w | dominates | dominates | contains | dominates | dominates | contains | dominates | [n.a.] |

**NOTE**: This is work in progress! At the moment, dominance implies multiple levels of parentage. Matrix 2 may be edited to display only direct parent-child relationships. Furthermore, the matrix can be mirrored so its right side may actually be left out. 

## Structure of Lady Susan, letter 9

[NOTE: replace "contains" with "dominates" where applicable?]

	# a text is a sequence of pages, and a sequence of letters
	
	# a page has an numeric annotation (the editorial page number) 
	# followed by a sequence of lines 
	
	# a pagenumber is a self-contained structure with a rend annotation 
	# that indicates the topographical location of the pagenumber
	
	# a letter starts with a title, follwed by a salute, and a content

	# a title is a self-contained structure that may contain several lines 
	
	# a salute contains one or more lines
		
	# a content contains one or more paragraphs

	# a paragraph contains a sequence of lines as well as a sequence of sentences
	
	# a line contains some alphanumeric characters
	
	# a sentence contains alphanumeric characters and may contain words (w)
	
	# a w contains a hyphen

So we can say that: 

	text > page > lines > characters
	text > letter > title > salute > content > sentence > w
	

## Attempt to divide the tags by hierarchy
**[NOTE]** *This gave no satisfying result, so we decided to approach it "bottom-up": that is, starting from the tags and exploring their relationships, instead of sorting them by hierarchy.*

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