# TAGS (TAG-Schema)

### Function of schema's:

1. explain the syntax and the grammar to the application; make sure that the syntax and grammar conform to the application's requirements
2. typing your text and your text edition
3. "auto insurance"; it's there in the background helping you when you've hurt yourself. This is David's main definition of a schema, but it also helps you with the two acts above. 
4. Guiding the creation of new transcription documents


### What does a schema mean for TAG?

1. Validation
	- text typing
	- querying
	- string grammar ("which combination of characters is allowed?")
	- graph grammar
	- cross-referencing, e.g. XML id's or pointers to another file like a dictionary
	- Error messages: the schema tells you what you did wrong and where the error is located (like in oXygen)

2. Hierarchies
	- in syntax (like XML)
	- in schema (like LMNL, which does make LMNL difficult to use for XML fans)

	
### State of the art

1. String grammar
	- stream of characters;
	- create a regex (a pattern) based on schema;
	- patterns are used to match the structure of permissable elements, so: compare regex with stream;
	- the schema is a decision diagram (a graph); the regex is a graph too, efficiently built with what you need only
	- validation means asking "can you make this string based on this grammar?" and "given this grammar, can you make this string?"

2. Graph grammar
	- not based on stream (obvs), but on text
	- schema is expressed as a graph (DAG or HG)
	- Consider a HG containing information from which a GODDAG is derived which is in turn validated ("can you build this GODDAG using this grammar?", and from which XML can be derived.

TexMecs and LMNL developed schema's but did not get very far; the reason for this is a bit unclear. 

Further: "schema-aware query processing". 

### What could/should a schema have and do
- not restrict, but "patternize"
- validate structure of document
- datatype assignment: describe and define datatypes that can be used (e.g. content of text nodes and attributes, or relationships between nodes)
- provide connection to  datatype library that validate the syntax
- constrain text values
- prescribe order
- reuse and redefine information in grammars that can be merged
- define the use of namespaces
- validates documents independently of any application (cf. Van der Vlist)
- differentiate between significant and insignificant whitespace
	 - between empty string and no string and strings containing only whitespace
- (foreign) namespaces
- [translatable in other schema language (e.g. from XML Schema to TAG S) without (significant?) information loss]
- [same language as syntax]
- [describes the elements in the syntax with synopses and examples]

From [MSMcQ](http://www.cmsmcq.com/2008/bielefeld/slides.html#(31)):
Why do we care about grammar? 

- structural units (conceptual and markup) are tools of thought
- it is difficult to query / navigate / process varying parent-child relationships
- grammar rules capture ("christallize") knowledge
- grammar is needed for validation


#### Relax NG
Light(er)-weight alternative for XML Schema. It is supposedly the best tool to validate XML document's structure. Besides structure validation, it describes XML vocabulary. Relax NG has 2 main objectives:  

- validate the structure of an XML doc
- provide connection with datatype libraries to validate the content of the text nodes and attributes
- uses patterns which is a more flexible approach to write, maintain, and combine schema's
- patterns match XML node types 1. text nodes; 2. elements; 3. attributes that can be combined 
- provides for ordered mixed-content: nodes may appear anywhere but the order of the XML elements is fixed 

Terminology:  

- **infoset** a description of the elements and their structure: in the XML world those are elements, attributes, and textual content. XML schema languages work at the level of the XML infoset, so everything that is not part of the XML infoset (like the order of the attributes) cannot be constrained by a schema. The infoset takes on a logical view of the XML document (i.e. it sees the graph behind the linearized string)
- **patterns**: "Patterns are used to match the structures of permissible elements, attributes, and text nodes, much as the regular expressions used in programming can be used to match characters in text" ... and "patterns can be defined as the description of a set of valid node sets [a collection of nodes with an internal structure]" (Van der Vlist).

#### W3C XML Schema
(based on Van der Vlist)
- Validates structure of XML document
- Validates the content of text nodes and attributes
- Checks the integrety between keys and reference
- Provides a modelling language to classify XML elements and attributes
- Identifies semantics of XML elements and attributes
- Uses these semantics as extensible object-like models 
- Performs automatic binding between XML documents and objects.


#### Questions
- schema's have their own systax that do not necessecarily correspond with the syntax of the documents they validate(?)
- description of schema cf. XML's information set? 
- validate only the structure of the TAG document, or validate also the values of the content of this structure?
- is the particular structure implied by the syntax (such as TexMECS or XML), where the dominance relation is implicit in the order of tagging, actually always going to be the best structure?
- do we work with "spurious overlap", when the order of tags does not properly reflect containment or closure?
	- TexMex: ```<b|bold <i|italic|b>|i>```
	- LMNL: tag order does not contain information

#### Examples

- **poetry**: meter + syllables and stress analysis - find all the places where there's stress, moving over the document and looking at it horizontally (over the line) and vertically (the columns). In XML processing this requires creating several intermediate documents; ideally in TAG one would add different layers of markup, one layer at the time, possibly with analysis in between.


## Starlodge Notes
### General

- It is difficult to find tags that have the same meaning in different hierarchies (```w``` or ```p``` have specific meaning)
- In the status quo there are two ways of dealing with variance in structure: the XML way means finding workarounds; the LMNL way means no validation. Both are not desirable: we don't want workarounds and we do want validation
- Do we let the exceptions influence the schema? Where do you draw the line? Another solution is to let the computer generate a schema. It would be a base schema that you can edit later.
- The schema would be able to deal with multiple (overlapping) hierarchies 
- The advantage is that it looks at what you tagged, instead of what you *think* you tagged. 
- Because TAG allows multiple structures in text, the role of the schema becomes much more important. The output would first be descriptive ("this is what you have tagged") and could be transformed into a prescriptive schema ("this is how the document structure should be"; "this is how your tags should interact").
- The output would be a schematic overview of the multiple DAGs in your text, showing where tags overlap and where there's a relationship between them
- The need for a (generated) schema in TAG is self-evident because the markup of TAG is so much more complex
- Generating schema's is similar to the approach of SMcQ's (2008) that parses a TexMecs document assuming dominance relationships, and where it finds an instance that is not dominance it defines it as "containment". This approach is limited in the way that the editor cannot influences or overwrite this. Furthermore there is no validation; the Rabbit/Duck grammars can validate multiple data streams but only tree structures (not graphs)
- XML has a schema generator, written bij James Clarke, that works well: it has data typing etc.
- EARMARK expresses the markup, not the concepts behind it. 
- We want to express not only the markup but especially the conceptual ideas (world view) behind it. For this we can turn to OWL and SKOS ontologies. 


### Balisage paper

- Why would you want to generate a schema; why is it a good idea for TAG?
- How do you do this? 
- We define rules about the text that are based on our understanding of the text. For instance, we can say that a document instance is of the type "poem" and that a poem document has line groups that exhaustively include lines and that those lines only text nodes can exist and that those text nodes need to be continuous. 
- the markup expresses a view of the world (knowledge) and a schema needs to check whether the tagging is consistent with your specific view of the world. 

### Conceptual model Prometheus Unbound - p21v

#### Physical
- the document's surface is a page that has a number of sections
- the physical structure of a section varies, but each section consists at least of a sequence of page lines
- a page line runs from left to right and consists of alphanumeric characters, spaces, and words (w)
- in this physical view, a word is defined as a linear sequence of alphanumeric characters, UTF-8 symbols, and may have a facsimile element
- a word has no spaces
- a word may overlap with a page line but not with a section
- a page line can consist of spaces only (if it's a "new line")
- a page line cannot overlap with a section
- a page line can contain another page line if the embedded page line has an add element
- the add element has a type attribute and consists of a sequence of text nodes

#### Poetic
- the document instance is also a poem
- a poem is defined as one or more line groups
- the poem starts with a speech that is not part of the poetic structure
- the speech node has alphanumeric characters (one or more text nodes) and may also have a speaker node (one or more text nodes that have alphanumeric characters)
- a line group has a type attribute, in this cause stanza, and a number of poetic lines (```l```) 
- poetic lines are related to page lines but not the same: sometimes a poetic line overlaps with a page line
- a line group is related to section, as the definition of a section  and the definition a line group are based on physical appearance ("block of text"), but a line group has only poetic lines, whereas a section can also have a speech with a speaker
- however a line group is not dominated by a section because a section is bound by the surface of the page and a line group can overlap page
- a ```l``` (poetic line) has text nodes that have alphanumeric characters and spaces and word elements. It cannot contain another poetic line. It is related to a page line, but can cross page lines and pages.
- a poetic line dominates word elements, so words can cross page lines but not poetic lines
- a word element is used here to mark the words in a poetic line that rhyme. The rhyme itself is indicated with the rhyme element 
- a rhyme element has a label attribute that contains text characters with the rhyme, and wraps around alphanumeric characters





