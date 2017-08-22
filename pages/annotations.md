---
title: Notes concerning annotations
keywords:
tags:
sidebar: home_sidebar
permalink: /annotations.html
summary:
---

## Internal annotation scheme
Must be... :  
- single file  
- either human-readable or with good tool support  
- reversible and mergeable  


## First candidate: CoNLL-U
<http://universaldependencies.org/format.html>  
Text segmentation has to be adapted.  

### Editors
- Brat <http://brat.nlplab.org/examples.html>  
- UD Annotatrix <https://github.com/jonorthwash/ud-annotatrix>  

### Tools
- <https://github.com/UniversalDependencies/tools>  
- <https://github.com/EmilStenstrom/conllu/>  

## CoNLL-U preliminary testing

CoNLL-U implementation based on: <http://universaldependencies.org/format.html>

Original CoNLL-U Syntax calls for such structure marking:

	# newdoc id = mf920901-001
	# newpar id = mf920901-001-p1
	# sent_id = mf920901-001-p1s1A
	# text = Slovenská ústava: pro i proti
	# text_en = Slovak constitution: pros and cons

In the Ur III administrative corpus, sentences span many lines and the structure of documents is complex and is divided into surfaces and sections, based on the medium of the text. The ConLL-U syntax is thus adapted as such:

	# newdoc id = P101049
	# newsurface id = P101049-obverse
	# newsection id = P101049-obverse-column-001
	# line_id = P101049-obverse-column-001-0001
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting

Notes: It might be best to reduce the ids to the actual division and process the preceding divisions to get their ids if needed, to avoid repetition? Eg:

	# newdoc id = P101049
	# newsurface id = obverse
	# newsection id = column 1
	# line_id = 1
	# text = 2(disz) ma2 1(gesz2) gur 2(ban2)-ta ma2-lah5-bi i3-ib2-u3
	# text_en = 2 barges of 60 gur (capacity), 2 ban2 (per day) each, their skippers piloting

### ConLL-U Fields  
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

HEAD, DEPREL, and DEPS will be used only when we get to syntactic parsing and we should be able to use the Brat GUI editor for this task. (http://brat.nlplab.org/)

In the examples below, the UPOSTAG field is completed using UD and XPOSTAG with ORACC/ETCSL/PENN so we can compare the different tag sets available.

The FEATS field displays tags as:  UD / ETCSRI. ETCSL tags will be added when available


*Émilie Pagé-Perron*
