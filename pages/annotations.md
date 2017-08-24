---
title: Notes concerning annotations
keywords:
tags:
sidebar: home_sidebar
permalink: /annotations.html
summary:
---

## Gold standard annotation

### Workflow

1. Export raw ATF from the CDLI  
Manually export ATF of texts to annotate from the CDLI database. This can be done by doing a search at <http://cdli.ucla.edu/search> and clicking on "download" after the results appear.

2. Convert texts to pseudo-conll for morphological annotation  
Use the Pyhton script X to prepare a tokenized and conll-style version of the textual information to facilitate morphological annotation.

3. Morphological annotation  
Manually annotate morphology and subject, direct and indirect object dependencies in the files. (See below for more details)

4. Conversion to full annotations set in CoNLL-U Format  
Using the X Python script, convert the new annotations to the fuller version that will be used by subsequent processes.

5. Conversion to Brat standoff  
Use the CoNLL-U to Brat standoff converter to prepare data for syntactic annotations using the Brat editor.

6. Syntax annotation  
Manual annotation of syntax using the Brat interface


### CoNLL-like and CoNLL-U formats

Conll-U format information: <http://universaldependencies.org/format.html>  
CoNLL-U implementation based on: <http://universaldependencies.org/format.html>

Original CoNLL-U Syntax calls for such structure marking:

	# newdoc id = mf920901-001
	# newpar id = mf920901-001-p1
	# sent_id = mf920901-001-p1s1A
	# text = Slovenská ústava: pro i proti
	# text_en = Slovak constitution: pros and cons

In the Ur III administrative corpus, sentences span many lines and the structure of documents is complex and is divided into surfaces and sections, based on the medium of the text.

The ConLL-U syntax is thus adapted in such manner:

- In a comment line above the textual information, the text id must be mentionned, eg: 

	# newdoc id = P653433
 - Blank lines are used to separate clearly different sections of the texts but usually one text will be considered as one long sentence.

### CoNLL-U Fields  
#### Original CoNLL-U Fields  
ConLL-U fields description based on the Universal Dependencies website

- ID: Word index, integer starting at 1 for each new sentence; may be a range for multiword tokens; may be a decimal number for empty nodes.  
- FORM: Word form or punctuation symbol.  
- LEMMA: Lemma or stem of word form.  
- UPOSTAG: Universal Dependencies (UD) part-of-speech tag.  
- XPOSTAG: Language-specific part-of-speech tag; underscore if not available.  
- FEATS: List of morphological features from the universal feature inventory or from a defined language-specific extension; underscore if not available.  
- HEAD: Head of the current word, which is either a value of ID or zero (0).  
- DEPREL: Universal dependency relation to the HEAD (root iff HEAD = 0) or a defined language-specific subtype of one.  
- DEPS: Enhanced dependency graph in the form of a list of head-deprel pairs.  
- MISC: Any other annotation.  

#### Conll-like fields for annotation
	# ID	FORM	SEGM	XPOSTAG	HEAD	DEPREL	MISC
ID: all information about the surface, column, line and token (o.col1.1.1;  o.1.1 if there is no column) Only the column number is optional.
FROM: token from text, atf transliteration
SEGM: normalized form of the token
XPOSTAG: ORACC ETCSRI morphological tags based on the segmentation and using POS tag or named entity tag instead of "STEM" for the stem (eg.: GN.ABL)
HEAD: id of token that is the verb for which this token is a subject of object
DEPREL: relationship with verb as subject, direct object or indirect object (nsbj/dobj/iobj)
MISC: semantic role of this word eg. "seller"

#### CoNLL-U fields with processed data
	#ID	FORM	LEMMA	UPOSTAG	XPOSTAG	FEATS	HEAD	DEPREL	DEPS	MISC
LEMMA: Lemma to which the token should be associated
UPOSTAG: Universal dependencies part of speech tag, based on a mapping between the ETCRSI POS and the UD POS
FEATS: Unimorph tags, in order of morpheme appearance
DEPS: will not be used at this time


### Editors
Morphological annotations are added to the conll file manually using any plain text editor. We recommend Atom <https://atom.io/> because it can be used on any platform. Other plain text editors will do the job, such as Sublime <http://www.sublimetext.com/2>, Text Wrangler <https://www.barebones.com/products/textwrangler/>, Notepad++ <https://notepad-plus-plus.org/> and the like.

Syntax annotations can be added manually in the conll file or using the Brat interface. We have a developpement brat server up at <http://cdli-dev.org/brat/>.

Brat website: <http://brat.nlplab.org/examples.html>
another dependency annotation tool: UD Annotatrix <https://github.com/jonorthwash/ud-annotatrix>  


### Morphological annotation example

## Automated annotation workflow


*Émilie Pagé-Perron*
